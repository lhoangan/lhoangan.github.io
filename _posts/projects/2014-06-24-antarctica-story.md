---
layout: post
title:  "Antarctica Story: when Linux and Wireshark getting along"
author: "Khoi-Nguyen C. Mac, Hoang-An Le, Quoc-Minh Bui"
affiliation: "EURECOM institute, Campus SophiaTech, Telecom ParisTech"
date:   2014-06-24
excerpt: "Simple Android game project for the course Mobile Aplications and Services, Fall 2014,
at EURECOM institute, Campus SophiaTech, France."
project: true
feature: /assets/images/posts/2014-06-24/feature2.png
thumbnail: /assets/images/posts/2014-06-24/thumbnail4.png
tag:
- course project
- CGI
- maya
comments: true
---

This short movie tells a story of a penguin family in Antarctica. They were spotted
by a white shark while resting on a floating iceberg. Although the iceberg was
out of reach, the shark made his own approach to the penguins.  While everything
was under-anticipated according to his plan, the shark encountered something
new later on, something that would completely change everything...

The video clip is provided as the result for the course on 3D and Virutal
Imaging in 2014 at EURECOM institute, Campus Sophia Tech, France.
The scenery and some the 3D models are manually
designed by the authors using Autodesk Maya 2015. Video production and effects
are done with Adobe After Effect X5.

*This clip was made in the scope of a course project and has no means to be
used for commercial purpose. Some of the videos and sound tracks used in
this video may be copyrighted and the authors do not own these copyrights.*

## Pre-production

### Storyboard

Because of the complexity in modeling and animation which may require advanced
Maya techniques in control and manipulate the objects, the product cannot be
filmed in just one simple scene. Instead, to simulate the real filming process,
the movie is decomposed into different scenes which has in detail different
camera at different perspectives. For safe developing and testing purpose
(as we studied on the way), each scene is constructed several times, each time
(as we call it take) has some increment in model, technique, effect, etc.,
until the whole scene is completed. By this way, we can in parallel render
each scene (or part of a scene) separately and simultaneously on different
computers, which helps improving the efficiency (as we can fix and re-render
fault scenes, if any) and thus, reduces time consuming.


{% include image image="Page-10-Image-14.png" caption="<b>Figure</b> Sketched
storyboard."%}

## Modeling

### Penguin model

The penguin model is built by shaping and combination of basic geometric shapes
such as a cone (for the peak) and a sphere (for other body parts). As shown in
Figure 1(a), the torso is a sphere scaled along y-axis. The upper half is scaled
and moved up while the lower half is scale and moved down. In the similar manner,
a wing is a sphere scaled down about along y-axis and scaled up along x-axis
(Figure 1(b)). The peak (Figure 1(c)) is a cone rotated and scaled
down along z-axis. A part of the cone is translated inwards, and rotated
along x-axis. The eyes are made from 2 simple spheres. A foot is a sphere
scaled down along y-axis and having a part translated forward in z-axis
(Figure 1(e)). The whole penguin is built by plugging all part together,
at the appropriate positions (Figure 1(f)).

{% include image image="Page-2-Image-1.png" caption="<b>Figure 1</b> The penguin
model: (a) the torso, (b) a wing, (c) the peak, (d) an eye, (e) a foot, (f) all
together."%}

The penguin would not look like one without the textures shown in Figure 2.

{% include image image="Page-3-Image-2.png" caption="<b>Figure 2</b> The penguin
texture. From left to right: the body, an eye, and final result ."%}

To animate it, it is necessary to attach a skeleton to the model (Figure 3).

{% include image image="Page-3-Image-3.png" caption="<b>Figure 3</b> The penguin
skeleton rig."%}

One of the notable points in this project is that all details from the characters
or scenery models to how they animate are constructed from very simple and
trivial primitives. The models and animation of a penguin are already shown in
the previous parts. However, a simple (or even textured or animated) penguin
model would not attract much interest because it behaves just like a robotic
statue. To energize these models so that they look lively, we put some
emotions onto their faces.

The emotion expression idea is originated from well-known Japanese comics and
cartoons, also known as *manga* and *anime*. In these comics and cartoons,
we draw characters' emotions using simple strokes on their faces or on the
surrounding environment. As shown on Figure 4, this could be done quite 
simply by just changing the characters’ textures or put some extra ones
around the characters. To avoid the side effect caused by environmental
lighting, the textures used as emotion expression are all set to transparent,
with low diffusion and to reject shadow formation.

{% include image image="Page-3-Image-4.png" caption="<b>Figure 4</b> The penguin
emotion. From left to right: happy, in love, nervous, anxious."%}

## Shark model
With a bit difference, the shark torso is reconstructed from a
[downloaded model](https://www.animationmethods.com/rigs.html) as shown in the
Figure 5. Besides, the shark model is also rigged with skeleton and then textures
as the penguin models (Figure 6)

{% include image image="Page-4-Image-5.png" caption="<b>Figure 5</b> The original
shark model (left) and the reconstructed one (right)."%}

{% include image image="Page-4-Image-6.png" caption="<b>Figure 6</b> The
shark model rigged with skeleton (left) and textures (right)."%}

The emotional expression is created with the same technique as it was to the
penguin models: as shown in Figure 7 the emotional strokes is drawn as some
extra textures onto the shark

{% include image image="Page-4-Image-7.png" caption="<b>Figure 7</b> The
shark emotion. From left to right each row: angry, in love, attracted, and stunned."%}

## Scenery

### Landscape
The landscape including the mountains and iceberg is constructed using [sculpt
modeling technique](https://en.wikipedia.org/wiki/Digital_sculpting).
The technique is motivated from the real sculpting process where a model is
developed from a dense substance such as clay by pull, smooth, grab,
pinch or otherwise manipulate each part of the initial mess 
There are 3 types of
[sculpt modeling](https://en.wikipedia.org/wiki/3D_modeling#Modeling_process)
including *displacement*, *volumetric* and *dynamic tessellation*.
The mountains and iceberg model in this work belong to the displacement type:
a dense model, in this case a plane, will has each of its vertex adjusted
to a different height (above or below the original plane) which is predefined
from a so-called displacement map (or height map) adjusted locations.
Figure 8 shows the displacement map used to generate the iceberg.
Depending on the parameters set in Maya, we can indicate the height a vertex
should be corresponding to a grayscale color provided in the map. Generally,
the lighter the color is, the higher a vertex is on a model.

{% include image image="Page-5-Image-8.png" caption="<b>Figure 8</b> Displacement
map for the iceberg (left) and the result model (right)."%}

Because of the complexities such as the size relation between the landscape size
(computed in Maya's unit) and the map size (computed in pixel),
the variation in height parameter corresponding with each color on the map,
the time consumed (though only about 15 seconds) in generating a model from a
map, and the requirement of natural shape of the generated model, construction
of the displacement map is really a challenge when working with displacement
sculpt model. The landscape used in the production was identified to have a low
part in the middle which is later filled with water (where placed the iceberg
and starting our story) while has some sort of mountains around the boundary.
The mountains should not be plotted as a heap of blocks or some geometric
primitive but should be as natural as real mountains. To do so,
many displacement maps have been tested (Figure 9), each was generated randomly
and after that, retouched with different tools such as blurring, smoothing,
blending, etc.  As shown in the left of Figure 10, the samples could not be
accepted because they get too artificial with pointed cone shapes while having
quite smooth mountainside. Besides, due to uniform color area in a displacement
map, the mountains have some staircase-like areas (top-right Figure 10) or
unsmoothed surface (bottom-right Figure 10)

{% include image image="Page-6-Image-9.png" caption="<b>Figure 9</b> Different
proposed displacement maps of different size for the landscape, and the
chosen one (top right)."%}

{% include image image="Page-7-Image-10.png" caption="<b>Figure 10</b> Some
landscape examples (left) and their problems (right)."%}

{% include image image="Page-7-Image-11.png" caption="<b>Figure 11</b> The final
landscape."%}

### Ocean

The ocean is created using fluid dynamic technique, a built-in function of Maya.
However, given the generated ocean as in Figure 12, the challenges are how to
make it look like real oceans, including 5 step (1) applying physical sun and
sky so that we'll know how the sea would look like; (2) in the real lighting
environment; (3) changing water shading to change the water color according to
the sun and sky; (4) putting it into scenes to check the compatibility of the
ocean color with the mountains' and iceberg's; (5) and finally, creating wakes,
so that the water surface can interact with other objects, making it look more
lively.

{% include image image="Page-8-Image-12.png" caption="<b>Figure 12</b> The default
water sample generated by Maya (with and without the shark)."%}

{% include image image="Page-8-Image-13.png" caption="<b>Figure 13</b> Some
proposed samples (color, lighting effect) and the final version (right most)."%}

## Post-production

The Maya's rendering technique mental ray can only create image files.
One of the common format is the Maya's Interchange File Format (or IFF).
Thus, to really construct a video out of these images, we need to use another
application to do the compositing and more than that, visual effects.
The post processing is carried out by using Adober After Effect CS6:
- **Motion graphics** Read the Maya's output images and combine them together.
This task includes also time controlling: stretch and shrink the duration of
each scene so that it fulfills the idea
- **Sound composition** Some effects including trimming, fade in, fade out,
amplification, etc. Visual effects Some of the visual effects used in the clip are
  - *Wiggle effect*: to shake a scene to visualize the earthquake or dizzy effect;
  - *Fish-eye effect*: makes the scene as if it was seen from the eye of the shark;
  - *Lightning*: create some lightning from stormy thunder clouds;
  - *Speed lines*: acceleration effect;
  - *Tracing look-path*: to show the looking path between 2 objects;
  - *Fireworks*: the firework effects are created from an external video.

## Product

It's finally time. Please grab your favorite beverage, sit back, and enjoy!

<iframe width="560" height="315" src="https://www.youtube.com/embed/6aaPkBlRJak" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Credits

### Videos

- [MGM Logo 3 Roar 2008 Restoration, Youtube](http://www.youtube.com/watch?v=OVCxJ1aT24A)
- [Miki Owns MGM Lion , Youtube](http://www.youtube.com/watch?v=LD3JzRZXhs0)
- [Muteki Kanban Musume - MGM style, Youtube](http://www.youtube.com/watch?v=AODKUqOVp7g)

### Sound tracks

#### Background musics

- *Opening* [Sepia No Hi - Card Captor Sakura (Letra), Youtube](http://www.youtube.com/watch?v=TeqwDrUK_Ik)
- *Thrilling* [Let It Go (Disney's ”Frozen”) Vivaldi's Winter - ThePianoGuys , Youtube](https://www.youtube.com/watch?v=6Dakd7EIgBE)
- *Jumping* [Super Mario Bros Official Theme Song , Youtube](http://www.youtube.com/watch?v=mnipB_8Br8U)
- *Flying* [Tom and Jerry at MGM music performed live by the John Wilson Orchestra 2013 BBC Proms, Youtube](http://www.youtube.com/watch?v=viDZza0CXj0)
- *Ending* [Tom and Jerry Episode 31 Salt Water Tabby, Youtube](http://www.youtube.com/watch?v=8IuYFA11nOU)

#### Sound effect

- *Evil laugh* [Tom and Jerry 26 - Solid Serenade Full, Ben McNairy, Youtube](http://www.youtube.com/watch?v=FQHqR2qmVHM)
- *Heart thumbing* [Tom And Jerry 034 - Kitty Foiled (1948), Youtube](http://www.youtube.com/watch?v=iBEjtpk-9P4)
- *Falling 2* [Tom and Jerry 62 - Cat Napping Full , Ben McNairy, Youtube](http://www.youtube.com/watch?v=MlY1aPVQrZ8)
- *Air* [Swagging Tom and Jerry 64 - The Duck Doctor Full , Ben McNairy, Youtube](http://www.youtube.com/watch?v=O6XQ_wVPMl4)
- *Afraid* [Tom and Jerry 77 - Just Ducky Full, Ben McNairy, Youtube](http://www.youtube.com/watch?v=T-HyYUmu8J8)
- *Falling 1* [Tom and Jerry 90 - Southbound Duckling Full, Ben McNairy, Youtube](https://www.youtube.com/watch?v=A0M5sR3OVUE)
- *Surprising* [Tom and Jerry Cartoon The Flying Cat, Youtube](http://www.youtube.com/watch?v=eWIUJRxXlQU)
- *Screaming* [Tom and Jerry Cartoon Baby Puss, Youtube](http://www.youtube.com/watch?v=Tlg2bHGXvbc)
- *Dog barking* [Tom and Jerry Cartoon That's My Pup!, Youtube](http://www.youtube.com/watch?v=Wj9izA4D31E)
- *Kissing* [Kissing sound effect, Youtube](http://www.youtube.com/watch?v=Wh4hV1CLaVk)
- *Cruching sound* [Person Bites Into Rice Cake Version 2, FreeFx](http://www.freesfx.co.uk/sfx/bite)
- *Oh, yeah!* [Man Saying Oh Yeah, AudioSparx](http://www.audiosparx.com/sa/summary/play.cfm/crumb.1/crumc.0/sound_iid.530621)
- *Thunder* [Thunder & Lightning Sound Effects-High Quality , Youtube](http://www.youtube.com/watch?v=QZpgHrKXooc)
- *Ocean sound* [Ocean Seagulls Relaxation, Youtube](http://www.youtube.com/watch?v=xys0gMPDHFA)
- *Laughing* [Jiraiya, The Big Pervert , Youtube](http://www.youtube.com/watch?v=eBwnVcsJBEs)
- *Popping* [Super Mario Bros - Jump - Sound Effect-HQ , Youtube]( http://www.youtube.com/watch?v=9LmPIlNZNUM)

## Appendix

### Scene list

Following is the scene list together with the camera details and the computers
at EURECOM lab that have been used to render.

- **Scene1Take8** (Petzi) : introducing the general scene
- **Scene2Take25** The shark falls: frame 95 - 155 (camera 3)
- **Scene2Take4** (Yakari): Camera zoom out, the shark seeing the drumstick
appearing on the penguins frame 1 - 85 (camera 1)
- **Scene2Take5** (Yakari): The shark jumps: frame 85-105 (camera 1 first few
frames, camera 2)
- **Scene3** (hoi Nguyen): scene3.1 : eye moving scene 3.2: happy dancing
- **Scene4Take2** (Petzi):
  - *frame 1 - 60*: the shark is angry (camera 4)
  - *frame 60 - 150*: the shark with the volcano (camera 4)
- **Scene4Take3** (Petzi): frame 1-95: the shark attacks; camera perspective
coefficients:
  - *Translate*: -5.394 3.077 -25.055
  - *Rotate*: 8.062 -8.2 0
- **Scene5Take1** (Yakari): frame 1 - 30 (camera 1): still laughing
- **Scene5Take2** (Yakari): frame 31 - 73 (camera 1): eye bulbing (iceberg falls
1st time)
- **Scene5Take3** (Yakari): frame 74 - 120 (camera 1) : eye bulbing + sweating
(iceberg falls 2nd time)
- **Scene5Take4** (Yakari): frame 121 - 140 (camera 1): camera zoom out
- **Scene5Take5** (Yakari): frame 141 - 210 (camera 1): 1st penguin fies
- **Scene5Take6** (Petzi): frame 211 - 270 (camera 1): 2nd penguin fies
- **Scene5Take7** (Yakari): frame 271 - 370 (camera 1): 3rd penguin fies +
icerberg sunk + shark going forward
- **Scene6Take1** (Petzi): frame 1 - 100 (camera 1): shark laughs pevertedly
- **Scene7Take0** (Yakari): frame 371 - 460 (camera 1): 3rd penguin flies up
- **Scene7Take1** (Yakari): frame 451 - 520 (camera 1): 3rd penguin rotates
- **Scene7Take2** (Yakari): frame 437 - 450 (camera 1): 3rd penguin gets chill
- **Scene7Take3** (Yakari): frame 451 - 470 (camera 1): 3rd penguin blinks
- **Scene7Take4** (Yakari): frame 471 - 476 (camera 1): 3rd penguin falls
- **Scene7Take5** (Petzi): frame 471 - 516 (camera 2): 3rd penguin falls (fps)
- **Scene8Take1** (Yakari): frame 471 - 520 (camera 1): blink eyes
- **Scene8Take2** (Yakari): frame 471 - 981 (camera 1): love eyes
(missing from frame 471 - 520)
- **Scene9Take1** (TinTin): frame 1 - 360 (camera 1): go to the open sea to end
- **Scene10Take1** (Yakari): frame 1 - 110 (camera 1): 2 penguins fall down +
stand up
- **Scene10Take2** (Yakari): frame 111 - 170 (camera 1): 2 penguins look at
each other
- **Scene10Take3** (Yakari): frame 171 - 210 (camera 1): 2 penguins change

### Trivia

The project name "Antarctica Story: when Linux and Wireshark get along" is 
inspired by the course `Netw_1` *Introduction to computer networking and internet*,
in which we were introduced to Linux and the Wireshark tool, and had to spend
hours to understand the idea and know how to use them. The course was mandatory
to all tracks at EURECOM at that time, and rendered fear to those students who
were not familiar with networking concepts.
