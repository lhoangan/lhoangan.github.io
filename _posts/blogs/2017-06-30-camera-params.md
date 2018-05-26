---
layout: post
title: "Camera parameters"
date: 2017-06-30
excerpt: "Something about camera parameters"
tags: [camera, instrinsic, extrinsic, parameters, Blender]
#comments: true
share: false
---


# Pinhole camera model
Camera is one of the main object in computer vision. Understanding how a camera
work can actually get us to many interesting problem of computer visions such as
image panorama or 3D reconstruction.

Believe it or not, camera was once invented with motivation from human eyes (ref?)
one of the most complex organ in a human body (ref?). Despite how complicated
camera technology can get to now, the camera model employed in computer vision
is, surprisingly, kinda simple.

[The eyes are the second most complex organ after the brain in a human body.](
http://optimumperformancetechnologies.blogspot.nl/2008/05/second-most-complex-organ-after-brain.html)

To captured image, we use photographic films, thin plastic sheets coasted with 
light-sensitive substances, that react to light rays contact (read more at [wiki](
https://en.wikipedia.org/wiki/Photographic_film)).

If we simply put a film in front of an object, we get a very blur image, because
light rays reflected from every part of object can end up at the same position 
on the film. Thus, no good

To limit the number of rays that can touch the film, we put a barrier with a 
pinhole, or *aperture*, on it. The pinhole is designed to allow just one light
ray pass through and create an inverted image of the scene. That basically makes 
a (pinhole) camera, and the effect is called *camera obscura* effect.

define focal length: distance from pinhole to the film

a pinhole camera requires no lens, but for the sake of simplicity, 
in most computer vision research, we assume the camera used follow a pinhole
camera model

{% include image image="pinhole_camera.png" caption="<b>Figure 1</b> Pinhole
camera model."
%}      

A pinhole camera creates real image on the film, hence the name real image plane.
But for easy mathemetic in the following section, we consider a virtual image
plane that are symmetric to the real image plane about the lens.

We are going backward, from the image to the objects in the world

### Three coordinate systems

Image coordinate system


Camera coordinate system


World coordinate system


### Image formation

{% include image image="camera_model.png" caption="<b>Figure 2</b> Pinhole
camera model. Redrawn from 
<a target='_blank' href='https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html'>OpenCV documentation</a>"
%}      

Let \\( \mathbf{P} = {\begin{bmatrix} X & Y & Z  \end{bmatrix}}^T \\) be an 
arbitrary 3D point seen by a camera \\( O \\) at the origin of its camera space,
and \\( \mathbf{p} = {\begin{bmatrix} u & v  \end{bmatrix}}^T \\) be the image 
of \\(\mathbf{P}\\), expressed in the image coordinate system.
The point \\( \mathbf{p} \\) represents a pixel in an image captured by the 
camera, which is formed by intersecting the light ray from \\( \mathbf{P} \\) 
passing through the *camera optical center* \\( O \\) and the image plane.

The camera model associates a 3D points \\( \mathbf{P} \\) in the camera space 
with its 2D image \\( \mathbf{p} \\) in the image plane so that we can locate 
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
They are introduced because the \\( \mathbf{P} \\) and \\( F \\) are expressed 
in regular measurement unit, such as inches or meters, while \\( \mathbf{p} \\)
and \\( c \\) are expressed in image pixel. These factors should be the same if
we have squared pixels, yet due to manufacturing impression, they are usually 
different. 

\\[
  u = s_u\dfrac{fX}{Z} + c_x \qquad \text{and} \qquad v = s_v\dfrac{fY}{Z} + c_y,
\\]

Since \\( \mathbf{p} \\) is in a 2D projective space (an image plane),
it could be represented by a 3-component vector 
\\( \mathbf{\tilde{p}} =  {\begin{bmatrix} u & v & w  \end{bmatrix}} ^T \\)  using homogeneous coordinate, turning Equation into

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
		\mathbf{\tilde{p}} = K\textbf{P}
\\]

Note that, by definition of homogeneous coordinate, the value of \\( u, v \\) in Cartesian coordinate value is obtained when \\( w = 1 \\), which makes Equation equivalent to Equation.

The matrix \\( K \\) contains all the camera internal parameters in pixel unit, such as the focal length \\( f_x, f_y \\) and principal point coordinate \\( c_x, c_y \\), thus is called the camera *intrinsic matrix*.

All the computation so far is carried out in the camera coordinate system, i.e. when the camera is at the origin of the coordinate and looks along the \\( z \\)-axis. In general, let the camera be part of an arbitrary general world coordinate system, where it can take any position and orientation, and \\( \mathbf{P} \\) be any point described in that coordinate system. The same computation can be employed if we can transform the camera coordinate system to fit to the world system. The transformation, presented in a camera *extrinsic matrix*, includes a rotation matrix \\(  {\begin{bmatrix} r_1 & r_2 & r_3 \end{bmatrix}}  \\) and translation vector \\( \mathbf{t} \\).
By transforming all points \\( \mathbf{P} \\) in the world space with \\(  {\begin{bmatrix} r_1 & r_2 & r_3 \end{bmatrix}}  \\) and \\( \mathbf{t} \\), we can describe \\( \mathbf{P} \\) in the camera coordinate system, and thus can use the same \\( K \\) as what we have described before.

Let \\( \mathbf{\tilde{P}} \\) be the homogeneous coordinate of \\( \mathbf{P} \\), which is now expressed in world coordinate system. The camera model that finds image coordinate \\( \mathbf{\tilde{p}} \\) is

\\[
	\tilde{\mathbf{p}} = \underbrace {K {\begin{bmatrix}
			r_1 & r_2 & r_3 & \mathbf{t}  \\
			\end{bmatrix}} }_H\tilde{\mathbf{P}} \equiv H\tilde{\mathbf{P}}
\\]

The homogeneous coordinate of \\( \mathbf{P} \\) presumes a projective transformation applied on \\( \mathbf{\tilde{P}} \\). Thus, the matrix \\( H \\) relates points \\( \mathbf{\tilde{P}} \\) from a projective 3D space to points on projective plane, thus is called homography matrix, generally with \\( s \\) be a scale factor, the homography matrix says:

\begin{equation}
	\tilde{\mathbf{p}} = sH\tilde{\mathbf{P}} \qquad\text{or, equivalent to}\qquad \tilde{\mathbf{P}} = \dfrac{1}{s}H^{-1}\tilde{\mathbf{p}}
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

