# Tool Learning Log

## Tool: **Unity**

## Project: **Rogue Like Game**

---

### 11/2/25:

## Unity Basic Controls

### 1. Scene Navigation

To move around the Scene view:

Right Mouse Button (Hold) + W/A/S/D → Fly around the scene.

Middle Mouse Button (Hold) → Pan view.

Scroll Wheel → Zoom in/out.

Q → Hand tool (pan)

W → Move tool

E → Rotate tool

R → Scale tool

T → Rect tool (for 2D/UI objects)

### 2. Object Selection

Left Click → Select object in the Scene or Hierarchy.

![alt text](image.png)
Shift + Click → Select multiple objects.

Ctrl/Cmd + D → Duplicate selected object.

Delete → Remove object.

### 3. Transform Basics

Every GameObject has a Transform component:

Position → Where the object is in the scene (x, y, z).

Rotation → How the object is rotated.

Scale → Size of the object.

You can change these in the Inspector or by using the Move/Rotate/Scale tools in the Scene.
![alt text](image-1.png)
### 4. Game View vs Scene View

Scene View → Where you build and arrange your game.

Game View → Shows what the player will see.

Switch between tabs at the top of the editor.

### 5. Play Mode

Play Button → Test your game in the editor.

Pause/Step Buttons → Debug or step through gameplay.

Changes made in Play Mode are not saved after stopping, unless copied to edit mode.

### 6. Hierarchy and Inspector

Hierarchy → Shows all objects in the scene.

Inspector → Shows details and components of the selected object.

Project Window → Where all your assets (models, scripts, textures) are stored.

![alt text](image-2.png)


### 11/16/25:


### Materials

you can change your material in the project file and fine where's all your material is located and drag it to the thing you wan to put the material on.
![alt text](image-3.png)

as for the sky you do the same but this time you drag the specfict skyboxes file to the sky 
![alt text](image-4.png)

![alt text](image-5.png)

1. Hand Tool (Pan View)

Lets you pan the Scene View without selecting or moving objects.

**Shortcut: Q**

2. Move Tool 

4-arrow cross

Move objects along X, Y, Z axes.

**Shortcut: W**

3. Rotate Tool

Curved rotation arrows

Rotate objects around X, Y, Z axes.

**Shortcut: E**

4. Scale Tool

Square scaling icon

Scale objects uniformly or per-axis.

**Shortcut: R**

5. Rect Tool

Rectangle with corner handles

Function: Move/Resize 2D objects & UI elements.

**Shortcut: T**

6. Transform Tool (Move + Rotate + Scale Combined)

Circles + arrows combined

A unified gizmo that allows moving, 
rotating, and scaling without switching tools.

**Shortcut: Y**

7. Create Placement Tool

Green circle with +

Function: Place new GameObjects (like prefabs) into the scene with click-to-place behavior.

(You activate it by selecting a prefab in the Hierarchy or dragging one)


<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->

### 12/8/25:

## Create with code

![alt text](image-6.png)
you can use the slider on the bottom right to zoom in and out of the item inside of a folder
![alt text](image-7.png)

added a secenes  by dragging it from the folder to the viewer

**F** Key is used when you can't find a object, first you click on the object you want to find in the hierarchy and press **F** and it will take your view to that object.

you can hold down the **Alt** and drag you mouse you can rotate around your camera with out moving 
![alt text](image-8.png)
right click hierarchy and you can add a camera that show the player's view
![alt text](image-9.png)
anything change in playmode will **not be save**
this is the what I have right now 
![alt text](image-10.png)
next step I'm going to continual with the lesson and try to make the car move
![alt text](image-11.png)

## The codes (C#)

### movement of the vehicle
```C#
 // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }
```

```C#
    // Update is called once per frame

 void Update()
    {

    }
```
```C#
public class NewMonoBehaviourScript : MonoBehaviour
{
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        //We'll move the vehicle forward
        transform.Translate(Vector3.forward * Time.deltaTime * 20);
    }
```
`transform` Every GameObject in Unity has a Transform component. It stores the object’s position, rotation, and scale.

`Translate()` `Translate` moves the object by a given amount. It adds a movement vector to the object’s current position.

`Vector3.forward` This is shorthand for the vector (0, 0, 1). It represents the forward direction of the object (along the Z-axis).

`Time.deltaTime` The time (in seconds) since the last frame. This makes movement frame-rate independent.

`* 20` This is the movement speed. The object moves 20 units per second forward.

`float` is a variable that tell the computer we are inputting a decimal number

```C#
 float speed = 5.0f;
 ```

 ### movement of the player camera

 first we create the `GameObject` class and go back to our *Hierarchy* and add the vehicle to it
![alt text](image-12.png)

then we add this to our update 
```C#
        transform.position = player.transform.position + offset;
```
so now the player's camera will move along with the vehicle and the `offset` is a variable I made that stand for `public Vector3 offset = new Vector3(0, 5, -7);
`

plus you can add something call `LateUpdate` so the command will run after the car move making the camera look more smooth


### 1/25/2026

to add rotation to the car first we make a float like `public float horizontalInput;` and after we can add it in the update like 
```c#
 void Update()
    {
        horizontalInput = Input.GetAxis("Horizontal"); // this will make it so you can get a input in unity
        transform.Translate(Vector3.forward * Time.deltaTime * speed);
        transform.Translate(Vector3.right * Time.deltaTime * turnSpeed * horizontalInput);// making the turnSpeed times the horizontalInput bye user pressing on left or right and make the car move left or right
    }
}
```