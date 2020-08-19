---
layout: default
title: Human/Biped foot placement Setup
parent: Tutorials
nav_order: 1
---

# Bipedal foot placement Setup

Applicable for humans & 2-legged creatures like chickens and raptors.
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Setup

---
      
        
1)
<img src="http://codehawk64.github.io/assets/images/setup1.png" >
{: .fs-3 .ls-7 .text-mono .code-example }
        
        
2)
<img src="http://codehawk64.github.io/assets/images/setup2.png" >
{: .fs-3 .ls-7 .text-mono .code-example }



3)
<img src="http://codehawk64.github.io/assets/images/setup3.png" >
{: .fs-3 .ls-7 .text-mono .code-example }



4) Copy/Paste the "dragon input data" from the spine solver to foot solver .
<img src="http://codehawk64.github.io/assets/images/setup4.png" >
{: .fs-3 .ls-7 .text-mono .code-example }



5)
<img src="http://codehawk64.github.io/assets/images/setup6.png" >
{: .fs-3 .ls-7 .text-mono .code-example }


6)
<img src="http://codehawk64.github.io/assets/images/setup7.png" >
{: .fs-3 .ls-7 .text-mono .code-example }

---

## Commonly encountered problems and their solutions


---


* IK not working ?
{: .fw-700 }
Ans : Check if the red lines and other widgets are rendering if you click on any of the solvers. If nothing is rendered, then the IK failed to activate. The IK won't activate
if any of the bones are typed wrong. Also ensure pelvis and spine-start are typed correctly, as bad order will also cause the IK to fail.

* IK feels like it is "turning off" on extreme slopes ?
{: .fw-700 }
Ans : Increase the "trace height upwards" and "trace height downwards" in the spine solver. If that doesn't help, also increase the "Maximum feet-terrain fail distance" as well as the "Minimum terrain capsule activation distance".

* Feets floating in the air ?
{: .fw-700 }
Ans : Decrease the "Trace Height Upwards" in the feet solver.

* IK reacting to too many objects in a level, including objects you don't want to react to ?
{: .fw-700 }
Use a custom trace channel to selectively ignore objects in the level. Create a new trace channel called "ik_channel" in the project settings under collision. Set it "ignore" by
default instead of "block". Replace the visibility channel used by the spine solvers and foot solvers. Set your terrain meshe's "ik_channel" response to block. Set objects you want the IK to ignore to "ignore".

* Body bones rotating too much or too less ?
{: .fw-700 }
Ans : Tweak the "forward rotation intensity" and "sideward rotation intensity" for both the pelvis and chest in the spine solver. It is a multiplier value.

* Feets not rotating properly when on slopes and or when doing actions such as crouching ?
{: .fw-700 }
Ans : Ensure to connect a cached copy of the original pose (the pose data before it goes through the spine solver) into the foot solver's "(optional) Ref pose for feet rotation on slopes"

* Feets are shaking or reacting too quickly towards the terrain.
{: .fw-700 }
Ans : Decrease or tweak the "shift speed" as well as the interpolation parameters such as "location lerp speed" and "rotation lerp speed"

* Leg knees are bending in undesirable directions ?
{: .fw-700 }
Ans : Tweak the position of the blue pole widgets in the animation blueprint viewport. The knee bending will have an extra bias in the same direction of the blue pole widgets. Alternatively, you can directly type the data inside the feet array's "knee direction offset" parameter.

* IK struggling in closed spaces like small rooms in an apartment or caves ?
{: .fw-700 }
Ans: Use the anti-channel functionality. Enable it in both the spine solver and foot solver. Create a new channel and call it "anti_channel" or anything comfortable with. Make sure the anti-channel's channel response is ignore by default in project settings. Objects with this anti-channel trace channel's response to "block" will repel the traces used for solving calculation. You can use meshes with the anti-channel to cover ceilings and under stairs for a customized workflow experience.
