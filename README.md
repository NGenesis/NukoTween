

# NukoTween

NukoTween is a Tween animation engine implemented in Udon. It is intended to be used with VRChat.

## How to install

### Prerequisites
It is assumed that VRChat Creator Companion (VCC) is installed.

Also, you need to add the following packages:
- UdonSharp

### install
1. Access [NukoraTween introduction page](https://nukora.github.io/NukoTween/) and press the Add to VCC button.
2. VCC will start and a confirmation screen for adding the NukoTween repository will be displayed. Follow the on-screen instructions to add it.
3. Find the project you want to use NukoTween in VCC and press the Manage Project button.
4. Add NukoTween from the package list.

*Steps 1 and 2 can be omitted from the second time onwards.

*For environments other than VCC, please download the older version of unitypackage from [NukoTween v0.0.8 release page] (https://github.com/nukora/NukoTween/releases/tag/v0.0.8). However, this will no longer be updated.


### how to use
1. Place the NukoTweenEngine prefab in the hierarchy in the Packages/NukoTween/Runtime directory.
2. Create the object you want to Tween on the hierarchy.
3. Attach UdonBehavior to the created object and write a script like the one below.
```C#
using UdonSharp;
using UnityEngine;
using VRC.SDKBase;
using VRC.Udon;

public class TweenCube : UdonSharpBehaviour
{
    public NukoTween.NukoTweenEngine tween;

    public override void Interact()
    {
        tween.LocalMoveTo(gameObject, new Vector3(1f, 0.5f, 0f), 1f, 0f, tween.EaseInOutCubic, false);
    }
}
```
4. Attach the NukoTweenEngine on the hierarchy to the tween field in the inspector.
5. Press the Trigger Interact button after playing the scene and confirm that the animation is playing.

## Method list

All functions are implemented as instance methods of the `NukoTweenEngine` class.  
Set the following values ​​for the arguments.
- `target` target to operate on
- `to` state after operation
- `duration` Time taken for operation (seconds)
- `delay` time (in seconds) to delay the start of the operation
- `easeId` [easing function] to use (#easing function)
- `relative` Whether to change relative to the current state

### Transform
#### `Local Move To`
```C#
LocalMoveTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target's LocalPosition to the specified position.

#### `Move To`
```C#
MoveTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target's Position to the specified position.

#### `LocalScaleTo`
```C#
LocalScaleTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target's LocalScale to the specified magnitude.

#### `LocalRotateTo`
```C#
LocalRotateTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target's LocalRotate to the specified angle.  
The angle is specified in Euler angles.

#### `LocalRotateQuaternionTo`
```C#
LocalRotateQuaternionTo(GameObject target, Quaternion to, float duration, float delay, int easeId, bool relative)
```
Changes the target's LocalRotate to the specified angle.  
Specify the angle as a quaternion.

#### `RotateTo`
```C#
RotateTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target Rotate to the specified angle.  
The angle is specified in Euler angles.

#### `RotateQuaternionTo`
```C#
RotateQuaternionTo(GameObject target, Quaternion to, float duration, float delay, int easeId, bool relative)
```
Changes the target Rotate to the specified angle.  
Specify the angle as a quaternion.

### RectTransform
#### `AnchorPosTo`
```C#
AnchorPosTo(GameObject target, Vector3 to, float duration, float delay, int easeId, bool relative)
```
Changes the target's AnchoredPosition to the specified position.

### Graphic
#### `GraphicColorTo`
```C#
GraphicColorTo(Graphic target, Color to, float duration, float delay, int easeId)
```
Changes the target color to the specified color.

#### `GraphicFadeTo`
```C#
GraphicFadeTo(Graphic target, float to, float duration, float delay, int easeId)
```
Changes the transparency of the target Color to the specified value.

### Image
#### `FillAmountTo`
```C#
FillAmountTo(Image target, float to, float duration, float delay, int easeId)
```
Changes the target's FillAmount to the specified value.

### Text
#### `TextTo`
```C#
TextTo(Text target, string to, float duration, float delay, int easeId)
```
Manipulate the target Text and perform character advancing animation.

### Text Mesh Pro
#### `TMPTextTo`
```C#
TMPTextTo(TextMeshProUGUI target, string to, float duration, float delay, int easeId)
```
Manipulate the target Text and perform character advancing animation.

### Audio Source
#### `AudioFadeTo`
```C#
AudioFadeTo(AudioSource target, float to, float duration, float delay, int easeId)
```
Changes the target Volume to the specified volume.

### Materials
#### `MaterialColorTo`
```C#
MaterialColorTo(Material target, string propertyName, Color to, float duration, float delay, int easeId)
```
Changes the material's Color type property to the specified color.

#### `Material Fade To`
```C#
MaterialFadeTo(Material target, string propertyName, float to, float duration, float delay, int easeId)
```
Changes the transparency of the material's Color type property to the specified value.

#### `MaterialVectorTo`
```C#
MaterialVectorTo(Material target, string propertyName, Vector4 to, float duration, float delay, int easeId)
```
Changes the Vector type property of the material to the specified value.

#### `Material FloatTo`
```C#
MaterialFloatTo(Material target, string propertyName, float to, float duration, float delay, int easeId)
```
Changes the material's Float type property to the specified value.

#### `MaterialTexOffsetTo`
```C#
MaterialTexOffsetTo(Material target, string propertyName, Vector2 to, float duration, float delay, int easeId)
```
Changes the Offset of the material's texture type property to the specified value.

#### `MaterialTexTilingTo`
```C#
MaterialTexTilingTo(Material target, string propertyName, Vector2 to, float duration, float delay, int easeId)
```
Changes the Tiling of the material's texture type property to the specified value.

### Misc
#### `DelayedSetActive`
```C#
DelayedSetActive(GameObject target, bool active, float delay)
```
Changes the GameObject's SetActive after the specified time.

#### `Delayed Call`
```C#
DelayedCall(UdonSharpBehaviour target, string customEventName, float delay)
```
Executes SendCustomEvent after the specified time.

### Control Mathods
#### `Complete`
```C#
Complete(int tweenId)
```
Immediately puts a running tween into a completed state.

#### `Complete All`
```C#
CompleteAll()
```
Brings all running tweens to a completed state.

#### `Kill`
```C#
Kill(int tweenId)
```
Aborts a running tween in its current state.

#### `Kill All`
```C#
KillAll()
```
Aborts all running tweens in their current state.

### Loop
Set the registered tween to loop.  
Specify the number of loops for loops, and passing -1 will create an infinite loop.

#### `Loop Restart`
```C#
LoopRestart(int tweenId, int loops)
```
When looping, the animation reruns after resetting the value to the previous starting point.

#### `Loop Reverse`
```C#
LoopReverse(int tweenId, int loops)
```
When looping, repeat the animation starting from the previous end point and returning to the previous start point.

#### `Loop Incremental`
```C#
LoopIncremental(int tweenId, int loops)
```
When looping, it runs the same animation as before, starting from the previous ending point.

## Easing function

You can use the following easing functions:  
It is defined as a read-only instance variable of the `NukoTweenEngine` class, so please use this when calling the method.

- EaseLinear
- Ease In Sine
-EaseOutSine
- Ease In Out Sine
- Ease In Quad
-EaseOutQuad
- EaseInOutQuad
- EaseInCubic
-EaseOutCubic
- EaseInOutCubic
-EaseInQuart
-EaseOutQuart
-EaseInOutQuart
-EaseInQuint
-EaseOutQuint
-EaseInOutQuint
- Ease In Expo
- Ease Out Expo
- EaseInOutExpo
-Ease In Circ
-Ease Out Circ
-Ease In Out Circ
- Ease In Back
-Ease Out Back
- Ease In Out Back
- Ease In Elastic
- Ease Out Elastic
-EaseInOutElastic
- Ease In Bounce
-Ease Out Bounce
- EaseInOutBounce

## properties

Customize engine behavior.  
It can be changed from the inspector of the object to which `NukoTweenEngine` is attached.

### Simultaneous Size
Specifies the number of tweens that can run simultaneously. This includes waiting tweens.

## License

This program is covered by the MIT license.

This software is released under the MIT License, see LICENSE.

