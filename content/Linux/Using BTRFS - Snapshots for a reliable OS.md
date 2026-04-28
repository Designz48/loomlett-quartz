>"A snapshot is not a backup: snapshots work by use of BTRFS’ copy-on-write behaviour. A snapshot and the original it was taken from initially share all of the same data blocks. If that data is damaged in some way (cosmic rays, bad disk sector, accident with dd to the disk), then the snapshot and the original will both be damaged. Snapshots are useful to have local online “copies” of the filesystem that can be referred back to, or to implement a form of deduplication, or to fix the state of a filesystem for making a full backup without anything changing underneath it. They do not in themselves make your data any safer."


https://itsfoss.com/btrfs/
https://linuxconfig.org/how-to-create-backups-with-fsarchiver-on-linux
https://linuxconfig.org/how-to-create-incremental-system-backups-with-timeshift-on-linux
https://linuxconfig.org/how-to-manage-snapshots-with-snapper-on-linux
https://linuxconfig.org/how-to-boot-from-system-snapshots-with-boom

https://btrfs.readthedocs.io/en/latest/btrfs-subvolume.html

`btrfs subvolume create`. That command is the "assembly language" of snapshots—powerful but tedious and easy to mess up if you forget flags.

Since you are on Arch (indicated by `pacman` and the `@` subvolume layout), you are likely missing the **management layer** that sits on top of Btrfs.

Here are the three best ways to automate this, ranked by how "set-and-forget" they are:

### 1. Snapper (The Standard for Arch/openSUSE)

This is the most robust tool for system snapshots. It integrates with `pacman` (via hooks) to automatically snapshot before and after package installs.

- **How it works:** You install it, configure a "timeline" (hourly, daily, weekly), and it handles creation, naming, and **deletion** of old snapshots automatically.
- **Setup:**
    
    `sudo pacman -S snapper sudo snapper -c root create-config / # Then edit /etc/snapper/configs/root to set TIMELINE_LIMIT_HOURLY, etc. sudo systemctl enable --now snapper-timeline.timer`
    
- **Why use it:** It creates the snapshots inside `@.snapshots` automatically and provides a CLI/GUI to roll back if an update breaks your system.

### 2. Timeshift (The "System Restore" Approach)

If you want something that feels like Windows System Restore or macOS Time Machine, this is it.

- **How it works:** It creates scheduled snapshots (RSYNC or BTRFS mode). It has a nice GUI to browse and restore.
- **Setup:**
    
    `sudo pacman -S timeshift sudo timeshift --restore  # First run wizard`
    
- **Note:** Ensure you select **BTRFS** mode in the wizard, not RSYNC. It will handle the subvolume logic for you.

### 3. A Simple Cron/Timer Script (The "DIY" Approach)

If you don't want heavy dependencies and just want a script that runs every night to snapshot `/home` and `/` and deletes the oldest 5:

Create a script `/usr/local/bin/auto-snap.sh`:

`#!/bin/bash DATE=$(date +%Y-%m-%d_%H-%M-%S) ROOT_VOL="/@" SNAP_DIR="/.snapshots" # Create snapshot sudo btrfs subvolume snapshot "$ROOT_VOL" "$SNAP_DIR/$DATE" # Delete oldest 5 snapshots (keep newest 5) # This assumes your snapshots are just named by date in /.snapshots cd "$SNAP_DIR" || exit ls -t | tail -n +6 | xargs -r sudo btrfs subvolume delete`

Make it executable and add it to a cron job (`crontab -e`): `0 2 * * * /usr/local/bin/auto-snap.sh`