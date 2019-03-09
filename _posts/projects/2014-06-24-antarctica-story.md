---
layout: post
title:  "Antarctica Story: when Linux and Wireshark get along"
author: 'Khoi-Nguyen C. Mac, Hoang-An Le, Quoc-Minh Bui, Hoang-Xuan Q. Nhat'
affiliation: 'EURECOM institute, Campus SophiaTech, Telecom ParisTech'
date:   2014-06-24
excerpt: "Simple Android game project for the course Mobile Aplications and Services, Fall 2015,
at EURECOM institute, Campus SophiaTech, France."
project: true
feature: /assets/images/posts/2015-02-02/main_menu.png
thumbnail: /assets/images/posts/2015-02-02/dumdumicon.png
tag:
- maya
comments: true
---

A short just-for-fun clip for 3D Graph course, 2014,
EURECOM institute, Campus Sophia Tech, France

The scenery and all the 3D models are manually designed by the authors using Autodesk Maya 2015. Video production and effects are done with Adobe After Effect X5.

This clip was done as a course project. No commercial purpose involves. Some of the videos and audio tracks used in the clip may be copyrighted and the authors do not hold these copyrights.

This clip was made in the scope of a course project and has no means to be used for commercial purpose. Some of the videos and sound tracks used in this video may be copyrighted and the authors do not own these copyrights.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6aaPkBlRJak" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

The movie tells a story of a penguin family in Antarctica. They were spotted by a white shark
while resting on a floating iceberg. Although the iceberg was out of reach, the shark made
his own approach to the penguins. While everything was under-anticipated according to his
plan, the shark encountered something new later on, something that would completely change
everything...

## Pre-production

### Storyboard

### Scene list

Because of the complexity in modeling and animation which may require advanced Maya tech-
niques in control and manipulate the objects, the product cannot be filmed in just one simple
scene. Instead, to simulate the real filming process, the movie is decomposed into different
scenes which has in detail different camera at different perspectives.
For safe developing and testing purpose (as we studied on the way), each scene is constructed
several times, each time (as we call it take) has some increment in model, technique, effect, etc.,
until the whole scene is completed. By this way, we can in parallel render each scene (or part
of a scene) separately and simultaneously on different computers, which helps improving the
efficiency (as we can fix and re-render fault scenes, if any) and thus, reduces time consuming.
The detailed scene list is presented in the Appendix 6.2


## Modeling

### Penguin model
#### Construction

The penguin model is built by shaping and combination of basic geometric shapes such as a
cone (for the peak) and a sphere (for other body parts). As shown in Figure 1(a), the torso is a
sphere scaled along y-axis. The upper half is scaled and moved up while the lower half is scale
and moved down. In the similar manner, a wing is a sphere scaled down about along y-axis
and scaled up along x-axis (Figure 1(b)). The peak (Figure 1(c)) is a cone rotated and scaled
down along z-axis. A part of the cone is translated inwards, and rotated along x-axis. The
eyes are made from 2 simple spheres. A foot is a sphere scaled down along y-axis and having
a part translated forward in z-axis (Figure 1(e)). The whole penguin is built by plugging all
part together, at the appropriate positions (Figure 1(f)).

#### Textures
The penguin would not look like one without the textures shown in Figure 2.


#### Animating skeletons

To animate it, it is necessary to attach a skeleton to the model (Figure 3)

#### Emotion expression

One of the notable points in this project is that all details from the characters or scenery models
to how they animate are constructed from very simple and trivial primitives. The models and
animation of a penguin are already shown in the previous parts. However, a simple (or even
textured or animated) penguin model would not attract much interest because it behaves just
like a robotic statue. To energize these models so that they look lively, we put some emotions
onto their faces.

The emotion expression idea is originated from well-known Japanese comics and cartoons,
also known as manga and anime. In these comics and cartoons, we draw characters’ emotions
using simple strokes on their faces or on the surrounding environment. As shown on Figure 4,
this could be done quite simply by just changing the characters’ textures or put some extra ones
around the characters. To avoid the side effect caused by environmental lighting, the textures
used as emotion expression are all set to transparent, with low diffusion and to reject shadow
formation.

## Shark model
With a bit difference, the shark torso is reconstructed from a downloaded model 1 . As shown
in the Figure 5
Besides, the shark model is also rigged with skeleton and then textures as the penguin
models (Figure 6)

The emotional expression is created with the same technique as it was to the penguin
models: as shown in Figure 7 the emotional strokes is drawn as some extra textures onto the
shark

## Scenery

### Landscape
The landscape including the mountains and iceberg is constructed using sculpt modeling tech-
nique. The technique is motivated from the real sculpting process where a model is developed
from a dense substance such as clay by pull, smooth, grab, pinch or otherwise manipulate
each part of the initial mess 2 . There are 3 types of sculpt modeling including displacement,
volumetric and dynamic tessellation. The mountains and iceberg model in this work belong to
the displacement type: a dense model, in this case a plane, will has each of its vertex adjusted
to a different height (above or below the original plane) which is predefined from a so-called
displacement map (or height map) adjusted locations 3 . Figure 8 shows the displacement map
used to generate the iceberg. Depending on the parameters set in Maya, we can indicate the
height a vertex should be corresponding to a grayscale color provided in the map. Generally,
the lighter the color is, the higher a vertex is on a model.

Because of the complexities such as the size relation between the landscape size (computed
in Maya’s unit) and the map size (computed in pixel), the variation in height parameter cor-
responding with each color on the map, the time consumed (though only about 15 seconds) in
generating a model from a map, and the requirement of natural shape of the generated model,
construction of the displacement map is really a challenge when working with displacement
sculpt model. The landscape used in the production was identified to have a low part in the
middle which is later filled with water (where placed the iceberg and starting our story) while
has some sort of mountains around the boundary. The mountains should not be plotted as a
heap of blocks or some geometric primitive but should be as natural as real mountains. To do
so, many displacement maps have been tested (Figure 9), each was generated randomly and
after that, retouched with different tools such as blurring, smoothing, blending, etc.
As shown in the left of Figure 10, the samples could not be accepted because they get
too artificial with pointed cone shapes while having quite smooth mountainside. Besides, due
to uniform color area in a displacement map, the mountains have some staircase-like areas
(top-right Figure 10) or unsmoothed surface (bottom-right Figure 10)

### Ocean

The ocean is created using fluid dynamic technique, a built-in function of Maya. However,
given the generated ocean as in Figure 12, the challenges are how to make it look like real
oceans, including 5 steps


## Post-production

## Credits

### Softwares

### Videos

### Sound tracks


## Product


