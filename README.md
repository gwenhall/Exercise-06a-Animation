When you are done, go to Object mode. In the Scene panel, select the GEO_ model pieces (holding shift or Command), until they are all selected. Finally, select metarig. Then press ctrl-P. Select Armature Deform->With Automatic Weights.

You can check that the bones are connected to the model by entering Pose Mode and grabbing (G) the bones. The model should deform accordingly.

Export the model as a .glTF 2.0 file: /Assets/Rain.glb

Open Godot. Import the project.godot file and open the "Animation" project.

Right-click on the Game node and Instance Child Scene. Select Assets/Rain.glb. Translate the new Rain node to (-8,0,0) and scale to (2.5,2.5,2.5)

---

Now, we will work on the animation of the Player node. Open the Player scene.

In the AnimationPlayer node, make sure the Idle and Walk animations are both set to AnimationLooping.

Right-click on the Player node and Add Child Node. Select AnimationTree. Select the AnimationTree node; in the Inspector->Tree Root, select New AnimationNodeBlendTree. Under Anim Player, select the AnimationPlayer. Set Active to On.

You will see a new AnimationTree panel appear at the bottom of the window. Drag the Output node to the right side of the workspace.

Add Node, and select Animation. Create a second Animation Node, and a Blend2 Node. Connect the Out ports from the two Animation nodes to the in and blend ports on the Blend2 node. Connect the out port from the Blend2 node to the Output node.

Rename the Blend2 node Idle_Walk.

In the first Animation node, call the animation Idle, and select Idle from the film canister menu.

In the first Animation node, call the animation Walk, and select Walk from the film canister menu.

As you adjust the slider, you should see the Walk animation become more or less dramatic.

Finally, select the characterMedium. In the Inspector, select Material->0, and select New Spatial Material. Edit that material. Under Albedo, Texture, add the res://Assets/alienB.png texture.

Save the Player scene.

In the Player.gd script, on line 25, add the following:

```
	$AnimationTree.set("parameters/Idle_Walk/blend_amount", current_speed/max_speed) 

```
# Exercise-06a-Animation
Exercise for MSCH-C220, 6 April 2021

An opportunity to play with animating 3D humanoid characters

## Implementation
Built using Blender 2.92.0, Godot 3.2.3

## References
[Kenney.nl Animation Characters](https://kenney.nl/assets/animated-characters-2)
[Rain v2.0 Blender model](https://cloud.blender.org/p/characters/5f04a68bb5f1a2612f7b29da)
[Godot tutorial: Create a basic ragdoll in 5 minutes](https://youtu.be/YZikII-uSis)
[Godot ThirdPerson Player Animation](https://youtu.be/msZw59Iln74)

## Future Development
None

## Extra Credit
None

## Created by 
Gwen Hall
