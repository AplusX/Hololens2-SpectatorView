# Manipulation handler #

![Manipulation handler](../Documentation/Images/ManipulationHandler/MRTK_Manipulation_Main.png)

The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands. Manipulation can be restricted so that it only allows certain kinds of transformation. The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.

## How to use the manipulation handler ##

Add the [`ManipulationHandler.cs`](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/Input/Handlers/ManipulationHandler.cs) component to a GameObject.

Make sure to also add a collidable to the object, matching its grabbable bounds. To make the object respond to near articulated hand input, add the [`NearInteractionGrabbable.cs`](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.Services/InputSystem/NearInteractionGrabbable.cs) script as well. 

If you wish to set minimum or maximum values for the object's scale, you can add a [`TransformScaleHandler`](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/Input/Handlers/TransformScaleHandler.cs) script.

![Manipulation Handler](../Documentation/Images/ManipulationHandler/MRTK_ManipulationHandler_Howto.png)

## Inspector properties ##

<img src="../Documentation/Images/ManipulationHandler/MRTK_ManipulationHandler_Structure.png" width="450">

**Host Transform**
Transform that will be dragged. Defaults to the object of the component.

**Manipulation Type**
Specifies whether the object can be manipulated using one hand, two hands, or both.

* *One handed only*
* *Two handed only*
* *One and Two handed*

**Two Handed Manipulation Type**

* *Scale*: Only scaling is allowed.
* *Rotate*: Only rotation is allowed.
* *Move Scale*: Moving and scaling is allowed.
* *Move Rotate*: Moving and rotating is allowed.
* *Rotate Scale*: Rotating and scaling is allowed.
* *Move Rotate Scale*: Moving, rotating and scaling is allowed.

![Manipulation Handler](../Documentation/Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Allow Far Manipulation**
Specifies whether manipulation can be done using far interaction with pointers. 

**One Hand Rotation Mode Near**
Specifies how the object will behave when it is being grabbed with one hand / controller near.

**One Hand Rotation Mode Far**
Specifies how the object will behave when it is being grabbed with one hand / controller at distance.

**One Hand Rotation Mode Options**
Specifies how the object will rotate when it is being grabbed with one hand.

* *Maintain original rotation*: Does not rotate object as it is being moved
* *Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user
* *Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical. Useful for bounding boxes.
* *Face user*: Ensures object always faces the user. Useful for slates/panels.
* *Face away from user*: Ensures object always faces away from user. Useful for slates/panels that are configured backwards.
* *Rotate about object center*:  Only works for articulated hands/controllers. Rotate object using rotation of the hand/controller, but about the object center point. Useful for inspecting at a distance.
* *Rotate about grab point*:  Only works for articulated hands/controllers. Rotate object as if it was being held by hand/controller. Useful for inspection.

**Release Behavior**
When an object is released, specify its physical movement behavior. Requires a rigidbody component to be on that object.

* *Nothing*
* *Everything*
* *Keep Velocity*
* *Keep Angular Velocity*

**Constraints on Rotation**
Specifies on which axis the object will rotate when interacted with.

* *None*
* *X-Axis Only*
* *Y-Axis Only*
* *Z-Axis Only*

**Constraints on Movement**
* *None*
* *Fix distance from head*

**Smoothing Active**
Specifies whether smoothing is active.

**Smoothing Amount One Hand**
Amount of smoothing to apply to the movement, scale, rotation. Smoothing of 0 means no smoothing. Max value means no change to value.

## Events ##
Manipulation handler provides the following events:

* *OnManipulationStarted*: Fired when manipulation starts.
* *OnManipulationEnded*: Fires when the manipulation ends.
* *OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.
* *OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.
