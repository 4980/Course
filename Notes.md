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

# Day 3 - Basics of Render on a GPU

The four fundamentals of rendering in 3D are:

- Triangular meshes
- Shaders
- Rigging (how things can move)
- Animations (how things do move)

Meshes exist in world space and model space. Model space defines how a model looks, irregarldess of where it is positioned in the scene. Any change in model space changes all the instances of the model. Changes in world space only change the instance.

Animation is based of keyframes. In between keyframes, the engine determines the interpolated values. Animation is often done using curves, wich each curve representing a channel (X traslation, Y rotation, Z scale, etc).














