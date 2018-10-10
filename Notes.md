# Day 1 - Math Review

A quick review of graphics and games related math.

## 1D

Single dimensional values are called scalars. In the context of this class, they are almost always represented as floats.

## 2D

Position v Vector


A position or location is literaly a  location in space.

A vector is merely a direction. That's it.

## Triangles

Three sides to a triangles

Interior v exterior angle.

Interior angle + exterior angle = 360

## Two kinds of angles.

Degrees v Radians

360 degrees in a circle.

2 * Pi radians in a circle

If I have x degrees, how mant radians do I have?

Sum of all interior angles in a triangle = 180.

## Three kinds of angles:

Acute: Less than a right angles.

Right: 90 degrees or PI halves radians.

Obtuse: Greater than right angles.

A right triangle can not have any obtuse interior angles.

## Trig


Fire a rocket at 45 degrees. How far does it travel in x and y in 1 second a 1 unit/second velocity.

Treat the problem as a triangle.
### Parts of a triangle:

Hypotenus - longest leg or leg opposite right angle

Adjacent Leg and Opposite Leg


Sine - Sin(Angle) = Opposite Leg/ Hypotenus

Cosine - Cos(Angle) Adjacent Leg/Hypotenus

Tangent - Tan(Angle) Opposite Leg / Adjacent Leg

What we really need to know in this class:

Sin(Angle) - Y
Cos(Angle) - X
Atan(Y/X) - Angle in Q1,2
Atan2(Y,X) - Angle in Q1,2,3,4 -- *Always use atan2*

## Dot Products and Cross Products


The dot produt gives the cosine of the angle between two vectors

V1 = (V1_x,V1_y), V2=(V2_x,V2_y)
Dot product = (V1_x*V2_x) + (V1_y*V2_y). Dot products always produce a scalar.

If the the vectors are normalized...
Dot product of 1 = colinear.
0 = orthogonal/perpendicular
-1 = Antiparallel

##  Normalizing

Always normalize first (almost).
Normalize means set length to 1.
To normalize divide the vector by its length.

How do we get the length of a vector?

Euclidean distance or L2 Norm.

Euclidean distance -- sqaure root of the sum of the sqaures.

sqaure root of(x*x + y*y).

## 3D

Right handedness and left handedness

## Cross Product

Given two vectors, the cross product gives a thrid vector that is orthogonal to both vectors.

# Day 2 - See the Tree

Too often students approach graphics and games like drawing a tree with their back to the tree. You have seen countless trees in your life--but when it comes to drawing one on your own, you have to *See the Tree*.

What does that mean? It means you have to do a detailed study of what you want to make in 3D. Really study it. Draw it. Measure it. Compare it to similar things. What is the same, what is different?

Remember that most ideas start on paper. The professionals, with their million dollar budgets start their ideas on paper (digital or otherwise). You would be okay to follow suit!

# Day 3 - Basics of Rendering on a GPU

The four fundamentals of rendering in 3D are:

- Triangular meshes
- Shaders
- Rigging (how things can move)
- Animations (how things do move)

Meshes exist in world space and model space. Model space defines how a model looks, irregarldess of where it is positioned in the scene. Any change in model space changes all the instances of the model. Changes in world space only change the instance.

Animation is based of keyframes. In between keyframes, the engine determines the interpolated values. Animation is often done using curves, wich each curve representing a channel (X traslation, Y rotation, Z scale, etc).

# Day 4 - Rigging and Shaders

## Rigging 

Rigging means adding bones to a model and specifying *how* it can move.

Ridged-body animation means the meshes cannot flex or bend.

Soft-body animation means the meshes can flex or bend.

In blender, you parent meshes to bones (in an armature) to create a rig. Unity can understand this rigs, but cannot generate them. Unity can, however, create animations. 

## Shading

Shaders are small programs attached to meshes that compute how to color each part of the mesh. In early days of computer graphics, sprites were simple attached to meshes. This was simply called texturing. Now, the GPU computes lighting, shadows, ambient occlusion, parallax, and countless other effects in hardware using shaders. Blender's powerful shader engine (Cycles) is not compatible with Unity. If Unity is your final destination, I would use Blender primarily for UV mapping, and do all shading with Unity.

# Day 5 - Exporting to OBJ - For Loops

The simplest way to procedurally generate anything is to use simple for loops.

To demonstrate, we create a simple city layout using a double for loop that creates a serious of cubes.

To use the results from this code, we export as an OBJ file.

OBJ is a format for exporting 3D objects. In word processing there are two main formats for exporting text -- TXT and DOCX. TXT is the standard for long-term support. It has been around forever and will be around forever. It does not support any complex formatting, but *everything* understands TXT. DOCX, on the otherhand, supports all sorts of formatting. It is a newer format and one day will be replaced by something else.

In the graphics world OBJ is like TXT--it is a simple format that has been around for a very long time and will probably be around forever. Everything understands OBJ, but is it not ideas for production because it does not support complex details. Currently, the industry standard for interoperability is the FBX format. FBX is a proprietary format controlled by Autodesk. One day it will be superceded by something else. In this class, we'll stick with OBJ.

Start with a JS Fiddle:

https://jsfiddle.net/bricksphd/y46wpzo1/

End with this JS Fiddle: 

https://jsfiddle.net/bricksphd/5dpj0mwy/

# Day 6: Procedural Generation--Recursion & Noise

## How can we procedurally create terrain?

### Simple trig function?

Pros: simple, lots of hills

Cons: Uniform

### Random function?

Pros: Not uniform

Cons: Looks like a corn field or low poly sharp rocks mountain thing

### Look at Real Mountains:
- Terraced Slopes

- Ridges
- Lots of vegetation
- Rocks are textured
- Slopes
- Not super pointy on top
- Clouds and air
- Erosion
- Water lines
- Rock lines = sedementary layers
- Geology theory -> Rocks were laid down flat

## Noise:
- White noise. ->Perfectly random interference or noise
- Brown noise. ->Shows up a lot in nature.

## Brown Noise
- Used extensively in terrain
- It does not supply erosion, etc.
- Hard to tell the scale with brown noise.
- An example is some stock market data

- Generate Brown noise -> Recursion midpoint algorithm

# Day 7 - Terrain & Unity

We ended Day 6 with ok 2D terrain and impcomplete 3D terrain. Today we polished up 3D terrain and produced convincing 3D terrain.

The "polished" 2D terrain came with a better jitter method when doing the midpoint displacement. Instead of choosing a random displacement location inbetween the left and right points, we chose a value +/- the average the average the right and left points. This plus adjusting the scale, produce reasonable 2D terrain.

Moving onto 3D terrain, we completeted the square diamond alogrithm. The 3D alogrithm has to recurse using 3 steps in order to cover all the points in the plane. With only the square part of the alogrithm, many of the points in the plane would not be adjusted. With both parts of the algorithm, the results are impressive and convincing.  By exporting as an obj, we can import the result as an object in Unity. By adding a first person character, https://github.com/bricksseeds/unity/, and adding a mech collider to the terrain, we walk around on the terrain we generated.

# Day 8 Cheeseburgers and L-Systems

When we create things procedurally, we want a controlled chaos--random creation within certain bounds. This leads to two important concepts.  First, in any creation, we have a space of possible items we create. This space, created implicitly or explicitly defines the set of things we can create. Whether plants, trees, cities, or cheeseburgers, we can define mathematically the set of what can be created by our algorithm. Second, in any creation, we define how we sample that space when we create something. A truly random sampling rarely produces what we want. In the real world there are rules that define how we create things or how things are created naturallly.

In order to procedurally generate things in a plausable way, we need to define what those rules are. One way to do that is with L-systems.

# Day 9 - Indepth Unity Game

Today we started developing our most indepth Unity game. The process brought out several interesting points quite naturally.

- Bullets through walls. With fast-moving objects in a scene (such as bullets), the physics engine can betray you. The most obvious symptom of this is that the bullets will fly through walls. The reason for this is that by default Unity does discrete collision detection, meaning that is integrates the movement of the bullets my moving them through space and checking at each time step if the bullet is in collision with any objects. If the bullet is travelling fast enough that it moves further than a wall's width during a time step, the physics engine will never know that the bullet hit the wall. To resolve this, we need to tell the psychics engine to use continuous collision detection. This lets the engine know need to use a different method for the bulltes that will always catch wall collisions.

-Phyics in general. Anything that we control with code that also uses the physics engine needs to be done in the FixedUpdate method. This is called on a regular schedule that matches the pyhics engine, as opposed to Update, which gets called on a non-deterministic rate which matches the framerate. Symptoms of using Update instead of FixedUpdate include briefly penetrating walls, etc.

# Day 10 - Triggers & L-Systems in Practice

## Triggers. 

Unity can treat physics colliders as triggers. A trigger is simply a collider that doesn't collide in a physics sense, but merely calls a "OnTriggerEnter" method when it is peneterated. We can use that to create responsive enemies that "notice" the player when they get close enough.

# Procedural Generation Theory

When you generate something using procedural generation, there are two main steps. First, you define a sample space (every possibe outcome). Then you define a method that samples that space.

# L Systems

We can layout a game level using L-Systems. Unfortunately, unless you really take care when generating L Systems, the systems can create degenerate L Systems that self intersect, creating impossible-to-cross levels. One way to resolve this is to use an additional sampling technique called rejection sampling. With rejection sampling, you put your L System in a do-while loop. You generate your L System, then check the result. If the result is acceptible, you break out of the loop. Otherwise, you run the L System. This prevents you from having to creating an terribly complex L System when a simple check in a while loop could detect degenerate cases that would be hard to code out of an L System.






















