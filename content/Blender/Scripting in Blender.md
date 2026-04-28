> [python_console](https://docs.blender.org/manual/en/dev/editors/python_console.html#bpy-types-spaceconsole)

+ .x can also be .xyz *(or indiv.)*
+ symbols can be changed (+, +=)

# coordinate moving
import bpy

	bpy.context.object.location.x = 2

	bpy.context.object.location = (1, 2, 3)
# location moving
	bpy.context.object.location.x += 0.5

### check object mode
	bpy.context.mode
### selected objects
bpy.context.selected_objects