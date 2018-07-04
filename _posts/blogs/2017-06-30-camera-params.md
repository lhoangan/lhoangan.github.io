---
layout: post
title: "Camera parameters"
date: 2017-06-30
excerpt: "Something about camera parameters"
tags: [computer vision, pinhole camera model, instrinsic, extrinsic, parameters]
#comments: true
share: false
---


# Pinhole camera model
Camera is one of the main object in computer vision. Understanding how a camera
works can actually get us to many interesting problems of computer vision such as
image panorama or 3D reconstruction.

Camera functioning simulates the way human eyes work. Yet, despite the 
incredibe complexity of the eyes ([the second-most, only after the brain](
http://optimumperformancetechnologies.blogspot.nl/2008/05/second-most-complex-organ-after-brain.html)),
or how insane modern cameras could get to nowaday, the underlining mechanism
of cameras, and especially ones employed in most computer vision problems, is
somewhat simpler, a pinhole camera model which is shown in Figure 1.

{% include image image="pinhole_camera.png" caption="<b>Figure 1</b> Pinhole
camera consists of a light-proof box with a tiny aperture on one side and
a film on the opposite inner side."
%}

We see things because there are light rays reflecting from them come into our eyes.
The colors we perceive are the wavelengths that are not absored from the objects'
surfaces. To captured images, we use photographic films, thin plastic sheets coasted with 
light-sensitive substances, that react to light rays contact (read more at [wiki](
https://en.wikipedia.org/wiki/Photographic_film)).

If we simply put a film in front of an object, we get blurry images, because
light rays reflecting from every part of object end up at the same position 
on the film, and screw it up. Thus, to limit the number of rays that can touch 
the film, we put a barrier with a pinhole (or *aperture*) on it. 
Hence, up to a certain point the smaller the hole, the sharper but dimmer the
image (read more on [how to select pinhole size](https://en.wikipedia.org/wiki/Pinhole_camera#Selection_of_pinhole_size)).
Light rays reflecting from an object pass through and create an inverted image 
on the film. That basically makes a (pinhole) camera, and the effect is called 
*camera obscura* effect.

A pinhole camera creates real image on the film, hence the film is usually known
to as *real image plane*. To ease out the mathematic that involves in explaining
the model, we consider a virtual image plane that is symmetric to the real plane
about the *center of projection* (the aperture).

In pinhole camera model, the focal length is defined to be the distance from
the center of projection to the image plane. This is,
however, different from the focal length of a lens (usually used in lens cameras), 
which is the distance to the plane where incoming parallel rays meet. 
Because of having no lens, if we consider the same definition for a pinhole camera, 
its focal length would be infinity.

{% include image image="pinhole_vs_lens.png" caption="<b>Figure 2</b> Pinhole
camera vs. lens camera.
<a target='_blank' href='https://physics.stackexchange.com/questions/223738/does-focal-length-mean-something-different-with-lenses-and-pinhole-cameras?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa'>Image source</a>"
%}

As most of commodity cameras employed in research compose are
based on similar structure with thin lenses, small apertures and light sensors
in place of films, the pinhole camera model is usually employed in explaining
and modelling image formation in computer graphic and computer vision research.


## Image formation

We are to relate a pixel position to its corresponding point in 3D space. The
image formation can be broken down into 3 stages, when light ray reflects from
an object's surface in the world coordinate, go into camera space and interact
with the film.

We are going backward, from the image to the objects in the world

Before going into the image formation details, we are to describe the coordinate
systems that involve in 

### Three coordinate systems

#### Image coordinate system

This is the coordinate system that attachs to each image, that is used to index
the pixels in the image. Conventionally, the origin is at top-left corner of 
the image with x-axis pointing rightward, and y-axis downward. The image coordinate
system is denoted by lowercase letters in 

#### Camera coordinate system

Coordinate system attaching to each camera. The origin is at the camera, with
z-axis system pointing at the looking direction, y-axis downward, x-axis rightward.

#### World coordinate system

An arbitrary coordinate system relate a camera to other objects in a scene

#### Image formation


{% include image image="camera_model.png" caption="<b>Figure 2</b> Pinhole
camera model. Redrawn from 
<a target='_blank' href='https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html'>OpenCV documentation</a>"
%}      

Let \\( P = {\begin{bmatrix} X & Y & Z  \end{bmatrix}}^T \\) be an 
arbitrary 3D point seen by a camera \\( O \\) at the origin of its camera space,
and \\( p = {\begin{bmatrix} u & v  \end{bmatrix}}^T \\) be the image 
of \\(P\\), expressed in the image coordinate system.
The point \\( p \\) represents a pixel in an image captured by the 
camera, which is formed by intersecting the light ray from \\( P \\) 
passing through the *camera optical center* \\( O \\) and the image plane.

The camera model associates a 3D points \\( P \\) in the camera space 
with its 2D image \\( p \\) in the image plane so that we can locate 
one by knowing the other. Assuming that the projective plane is perpendicular 
to the \\( Z \\)-axis of the camera coordinate system; the intersection is at 
the *principal point* \\( F = {\begin{bmatrix} 0 & 0 & f  \end{bmatrix}}^T \\),
which is expressed in the image coordinate system as 
\\( c = {\begin{bmatrix} c_x & c_y \end{bmatrix}}^T \\). Imprecision 
during manufacture causes the optical axis not to pass through the center of the
image plane, making \\( c \\) usually different from \\( \mathbf{0} \\).

The size of the image \\( pF \\) relative to the object \\( PP' \\) is 
parameterized by the distance between the projective plane and the camera center,
i.e. \\( f \\), the *focal length*. Similar triangles give:

\\[
  x = \dfrac{fX}{Z} \qquad \text{and} \qquad y = \dfrac{fY}{Z} \\\
  u = s_ux + c_x \qquad \text{and} \qquad v = s_vx + c_y,
\\]

where \\( s_u, s_v \\) respectively are size of imager element; \\( s_u, s_v \\)
count the number of pixels per inch along image width and height dimension.
They are introduced because the \\( P \\) and \\( F \\) are expressed 
in regular measurement unit, such as inches or meters, while \\( p \\)
and \\( c \\) are expressed in image pixel. These factors should be the same if
we have squared pixels, yet due to manufacturing impression, they are usually 
different. 

\\[
  u = s_u\dfrac{fX}{Z} + c_x \qquad \text{and} \qquad v = s_v\dfrac{fY}{Z} + c_y,
\\]

Since \\( p \\) is in a 2D projective space (an image plane),
it could be represented by a 3-component vector 
\\( \tilde{p} =  {\begin{bmatrix} u & v & w  \end{bmatrix}} ^T \\)  using homogeneous coordinate, turning Equation into

\\[
	\begin{bmatrix}
	   u  \\\
	   v  \\\
	   w
	\end{bmatrix} = \begin{bmatrix}
	   s_u f & 0 & c_x  \\\
	   0 & s_v f & c_y  \\\
	   0 & 0 & 1
	\end{bmatrix} \begin{bmatrix}
	   X  \\\
	   Y  \\\
	   Z
	\end{bmatrix} = \begin{bmatrix}
		   f_x & 0 & c_x  \\\
		   0 & f_y & c_y  \\\
		   0 & 0 & 1
		\end{bmatrix} \begin{bmatrix}
		   X  \\\
		   Y  \\\
		   Z
		\end{bmatrix} \\\
		\tilde{p} = KP
\\]

Note that, by definition of homogeneous coordinate, the value of \\( u, v \\) in Cartesian coordinate value is obtained when \\( w = 1 \\), which makes Equation equivalent to Equation.

The matrix \\( K \\) contains all the camera internal parameters in pixel unit, such as the focal length \\( f_x, f_y \\) and principal point coordinate \\( c_x, c_y \\), thus is called the camera *intrinsic matrix*.

All the computation so far is carried out in the camera coordinate system, i.e. when the camera is at the origin of the coordinate and looks along the \\( z \\)-axis. In general, let the camera be part of an arbitrary general world coordinate system, where it can take any position and orientation, and \\( P \\) be any point described in that coordinate system. The same computation can be employed if we can transform the camera coordinate system to fit to the world system. The transformation, presented in a camera *extrinsic matrix*, includes a rotation matrix \\(  {\begin{bmatrix} \mathbf{r}_1 & \mathbf{r}_2 & \mathbf{r}_3 \end{bmatrix}}  \\) and translation vector \\( \mathbf{t} \\).
By transforming all points \\( P \\) in the world space with \\(  {\begin{bmatrix} \mathbf{r}_1 & \mathbf{r}_2 & \mathbf{r}_3 \end{bmatrix}}  \\) and \\( \mathbf{t} \\), we can describe \\( P \\) in the camera coordinate system, and thus can use the same \\( K \\) as what we have described before.

Let \\( \tilde{P} \\) be the homogeneous coordinate of \\( P \\), which is now expressed in world coordinate system. The camera model that finds image coordinate \\( \tilde{p} \\) is

\\[
	\tilde{p} = \underbrace {K {\begin{bmatrix}
			\mathbf{r}_1 & \mathbf{r}_2 & \mathbf{r}_3 & \mathbf{t}  \\
			\end{bmatrix}} }_H\tilde{P} \equiv H\tilde{P}
\\]

The homogeneous coordinate of \\( P \\) presumes a projective transformation applied on \\( \tilde{P} \\). Thus, the matrix \\( H \\) relates points \\( \tilde{P} \\) from a projective 3D space to points on projective plane, thus is called homography matrix, generally with \\( s \\) be a scale factor, the homography matrix says:

\begin{equation}
	\tilde{p} = sH\tilde{P} \qquad\text{or, equivalent to}\qquad \tilde{P} = \dfrac{1}{s}H^{-1}\tilde{p}
\end{equation}

From similar triangles:

\\[
X = \dfrac{(u-c_x)Z}{f_x} \Leftrightarrow \dfrac{X}{Z} = \dfrac{u-c_x}{f_x}
\\]

and 

\\[
Y = \dfrac{(v-c_y)Z}{f_y} \Leftrightarrow \dfrac{Y}{Z} = \dfrac{v-c_y}{f_y}
\\]

In case of some commodity cameras, like Kinect or RealSense, the device provides Z coordinates of the points, thus, the formulas are already well-provided. 

In case when only depth, or point distance is provided, we need to take extra steps to compute Z

Similar triangles:

\\[
\dfrac{pF}{PP'} = \dfrac{OF}{OP'} \Leftrightarrow \dfrac{pF^2}{PP'^2} = \dfrac{f^2}{Z^2} \Leftrightarrow 
\dfrac{pF^2}{PP'^2 - OP'^2} = \dfrac{OF^2}{OP'^2} \Leftrightarrow OP'^2 = \dfrac{OF^2OP^2 - OF^2OP'^2}{pF^2} \\\
\Leftrightarrow OP'^2 = \dfrac{OF^2OP^2}{pF^2 + OF^2} \\\
\Leftrightarrow OP'^2 = \dfrac{OP^2}{\left(\dfrac{pF}{OF}\right)^2 + 1} \\\
\Leftrightarrow OP'^2 = \dfrac{OP^2}{\left(\dfrac{PP'}{OP'}\right)^2 + 1} \\\
\Leftrightarrow Z^2 = \dfrac{d^2}{\left(\dfrac{X}{Z}\right)^2 + \left(\dfrac{Y}{Z}\right)^2 + 1} \\\
\Leftrightarrow Z = \dfrac{d}{\sqrt{\left(\dfrac{u-c_x}{f_x}\right)^2 + \left(\dfrac{v-c_y}{f_y}\right)^2 + 1}} \\\
\\]

\\[
X' = \dfrac{u-c_x}{f_x} \qquad Y' = \dfrac{v-c_y}{f_y} \qquad \\\
Z = \dfrac{d}{\sqrt{ X'^2 + Y'^2 + 1}} \qquad X = X' * Z \qquad Y = Y' * Z
\\]


# Read more

1. How pinhole camera works, *Scratch A Pixel*, [Part 1](http://www.scratchapixel.com/lessons/3d-basic-rendering/3d-viewing-pinhole-camera),
[Part 2](http://www.scratchapixel.com/lessons/3d-basic-rendering/3d-viewing-pinhole-camera/how-pinhole-camera-works-part-2)

1. Camera Calibration and 3D Reconstruction, *OpenCV documentation*, [link](
https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html)

2. Dissecting the Camera Matrix: Intrinsic matrix, *Kyle Simek*, [link](
http://ksimek.github.io/2013/08/13/intrinsic/)

3. The Perspective Camera, *Kyle Simek*, [link](
http://ksimek.github.io/2012/08/13/introduction/)
