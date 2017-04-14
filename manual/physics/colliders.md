# Colliders

<span class="label label-doc-level">Beginner</span>
<span class="label label-doc-audience">Designer</span>

To use physics in your project, add a **collider** component to an entity. 

Colliders define the shapes and rules of physics objects. There are three types:

* [static colliders](static-colliders.md) don't move (eg walls, floors, heavy objects, etc)
* [rigid bodies](rigid-bodies.md) are moved around by forces such as collision and gravity (eg balls, barrels, etc)
* [characters](characters.md) are controlled by user input (ie player characters)

You can also: 

* set the [shape of collider components](collider-shapes.md)
* make [triggers](triggers.md), and detect when objects pass through them
* constrict collider movement with [constraints](constraints.md)

## How colliders interact

Colliders interact according to the table below.

|   | Kinematic objects   | Kinematic triggers   | Rigid body colliders   | Rigid body triggers   | Static colliders        | Static triggers   
|---|-------------|---------------------|-------------|---------------------|----------|------------------
| Kinematic objects        | Collisions           | Collisions  | Collisions and dynamic| Collisions   | Collisions    | Collisions     
| Kinematic triggers | Collisions           | Collisions   |Collisions           | Collisions     | Collisions     | Collisions   
| Rigid body colliders          | Collisions and dynamic     | Collisions     | Collisions and dynamic     | Collisions     | Collisions and dynamic| Collisions
| Rigid body triggers | Collisions         | Collisions  | Collisions | Collisions     | Collisions     | Collisions
| Static colliders| Collisions| Collisions| Collisions and dynamic | Collisions   | Nothing   | Nothing
|Static triggers     | Collisions     | Collisions     | Collisions     | Collisions    | Nothing    | Nothing

* "Collisions" refers to collision information and events only. This means the collision is detected in the code, but the objects don't bump into each other (no dynamic response).

* "Dynamic" means both collision information and events, plus dynamic response (ie the colliders bump into each other instead of passing through).

For example, rigid body colliders dynamically collide with static colliders (ie bump into them). However, no objects dynamically collide with triggers; collisions are detected in the code, but objects simply pass through.

## Show colliders in the scene editor

By default, colliders are invisible in the scene editor. To show them:

1. In the Game Studio toolbar, in the top right, click the **Display gizmo options** icon.

   ![Display gizmo options](media/display-gizmo-options.png)

2. Select **Physics**.

    ![Display physics option](media/display-physics-option.png)

The scene editor displays collider shapes.

![Display physics](media/display-physics.png)

## Show colliders at runtime

You can make colliders visible at runtime, which is useful for debugging problems with physics. To do this, use:

``
this.GetSimulation().ColliderShapesRendering = true;
``

To show or hide collider shapes at runtime with a keyboard shortcut, use the **DebugPhysicsShapes** script.

1. In the **Asset view**, click **Add asset**.
2. Select **Scripts** > **Debug Physics Shapes**.
3. Add the **Debug Physics Shapes** script as a component to an entity in the scene.

The script binds the collider shape visibility to **Left Shift + Left Ctrl + P**, so you can turn it on and off at runtime. You can edit the script to bind a different key combination.

> [!Note]
> Collider shapes for infinite planes are always invisible.

## See also

* [Collider shapes](collider-shapes.md)
* [Static colliders](static-colliders.md)
* [Rigid bodies](rigid-bodies.md)
* [Kinematic rigid bodies](kinematic-rigid-bodies.md)
* [Simulation](simulation.md)
* [Physics tutorials](tutorials.md)