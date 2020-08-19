---
layout: default
title: Dragon Aim Look Solver
parent: Parameter Meanings
---

# Dragon Aim Look Solver


| Parameter | Description                          |
|:----------|:-------------------------------------|
| Start Bone (Eg:- Head)    | The head bone.|
| End Bone    | The last bone to be influenced. (Eg:- Pelvis or chest) |
| LookAtLocation| Target location transform in world space |
|  Dragon Input Data (optional)   | Type the input bones used by the solver - pelvis,spine-start and feets. Any wrong bone typing mistake can cause the solver to fail. |
|   Hands Input (optional)  | The hand inputs. Used for seperate clamping and restricting of limb movements during body aiming. Uses : Weapon aiming, hand restriction while extreme body bending, wings stability etc|
|   Max Body Lookat Clamp  | The maximum allowed body chain rotation. Uses the body clamp curve as a multiplier for the final result. |
|  Head Max Clamp   |  Maximum separate limbs clamp. Can be used to shrink the angle or extend the angle with respect to the body clamp. Ignored if seperate head clamp bool is disabled. |
|   Limbs Max Clamp  | Maximum separate limbs clamp. Can be used to shrink the max angle or extend the max angle with respect to the body clamp. |
|   Downward translation when aiming upwards (Multiplier)  | The extra dip downwards if character is looking vertically upwards. |
|   Sideward translation when aiming sideways (Multiplier)  | The extra offset of the root bone in left/right if character's end bone is rotating towards the same direction. |
|   Downward translation when aiming sideways (Multiplier)  | The extra offset of the root bone in left/right if character's root bone is rotate towards the same direction. |
|   Vertical aim clamp ratio for body  | Tweak this if you want the clamp intensity to be different in the vertical axis. It is a multiplier ratio, and clamp is relative to existing setup. 0 = Absolutley no vertical body bending/aiming. 1 = Full Vertical body bending/aiming. Only applies to body chain. Ignores arms and head. |
|  Max Vertical Angle Range (Degrees)   |  Max global vertical rotation clamp. Beyond these clamps, the aiming reverses. |
|   Max Horizontal Angle Range (Degrees)  | Max global horizontal rotation clamp. Beyond these clamps, the aiming reverses. |
|  Bone Clamp Curve   | Curve clamp used to tweak the body bending limits. Works as a multiplier and is part of the total solving calculation. 0th value in X-axis denotes the clamp intensity of the end bone (eg:- if max body clamp is 100, and the 0th value is 0.1, then the final clamp of pelvis/end bone is 10). All values until the 1st value in the X-axis are multipliers for all the bone chains from End to Start bones. Exact 1st X-axis value is ignored, as the head clamp is solely determined by the separate head clamp parameter.|
|  Body Rotation Multiplier Curve   | Curve multiplier to tweak the rotation multiplier in the body chain. Default set to 1 always. No need for modification in most cases.|
|   Should feets be locked using IK ?  | Lock legs to its original position using IK as the body moves and rotates. Only works with valid dragon input data.|
|  Ignore Elbow Compression   | Only rotate the shoulder towards the target, and ignore the wrist and elbow in the solving. |
|  Ignore Seperate Hand solving   | Turn off separate limbs aiming. |
|   Use Relative Rotation Algorithm ?  | Switch between two different rotation algorithm for different type of results. [enabled] = Relative rotation algorithm provides greater degree of freedom of movement and stable poses. Favours pose stability over accuracy. [disabled] = Non-Relative rotation algorthm provides a more direct and natural aiming but with limit in the range of motion. Favours accuracy over pose stability. |
|  Use Separate independent clamping for head ?   | If enabled, the heads clamp is determined by the separate max head clamp parameter. If disabled, the head clamp is determined by the value in the clamp curve graph along with the rest of the body. Also influenced by max body clamp parameter. Eg:- If using the aim solver for tails, keep it disabled.|
|  Automatic Foot-Knee-Thigh detection   | Parameter to choose between automatic feet bone detection or manual method. If enabled, solvers only uses the feet bones, and automatically assumes the next 2 parent bones as knees and thighs. If disabled, solvers uses the feet bones, knee bones and thigh bones typed in the feet array. If disabled, all bones need to be valid. Any invalid bones will not activate the ik. Very useful to keep it disabled on DAZ rigs and certain animal characters, where the thigh-knee-foot are not in a straight linear hierarchy. |
|  Enable Solver   | Toggle this parameter to instantly turn on/off ik. |
|  Interpolation Type   | Select the type of interpolation method. |
|   Interpolation Speed  | Speed of solving interpolation |
|  Lookat Axis   | The forward direction axis of the character. Characters using the standard unreal directions use the default value.|
|  Target Offset (only for limbs)   | Useful for tweaking the aiming offset of arms/limbs. Popular use is for weapons aiming and accuracy. Offset works in component space. |
