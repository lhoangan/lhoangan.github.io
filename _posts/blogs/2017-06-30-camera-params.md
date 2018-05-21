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
one of the most complicated organ in a human body (ref?). Despite how complicated
camera technology can get to now, the camera model employed in computer vision
is, surprisingly, kinda simple.

If we put a film in front of an object, we get a very blur image, because light
rays reflected from every part of object will ended at the same position on the
film. Thus, no good

To limit the ray that can touch the film, we put a barrier with small pinhole on
it. That basically makes a camera.

Show a diagram

We are going backward, from the image to the objects in the world

### Three coordinate systems

Image coordinate system


Camera coordinate system


World coordinate system


### Image formation

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
  u = s_u\dfrac{fX}{Z} + c_x \qquad \text{and} \qquad v = s_v\dfrac{fY}{Z} + c_y,
\\]

where \\( s_u, s_v \\) respectively are size of imager element; \\( s_u, s_v \\)
count the number of pixels per inch along image width and height dimension.
They are introduced because the \\( \mathbf{P} \\) and \\( F \\) are expressed 
in regular measurement unit, such as inches or meters, while \\( \mathbf{p} \\)
and \\( c \\) are expressed in image pixel. These factors should be the same if
we have squared pixels, yet due to manufacturing impression, they are usually 
different. 


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


Similar triangles:

\\[
\dfrac{pF}{PP'} = \dfrac{OF}{OP'} \Leftrightarrow \dfrac{pF^2}{PP'^2} = \dfrac{f^2}{Z^2} \Leftrightarrow 
\dfrac{pF^2}{d^2 - Z^2} = \dfrac{f^2}{Z^2} \Leftrightarrow Z^2 = \dfrac{f^2d^2 - f^2Z^2}{pF^2} \\\
\Leftrightarrow Z^2 = \dfrac{f^2d^2}{pF^2 + f^2} \Leftrightarrow Z = \dfrac{fd}{\sqrt{(u-c_X)^2 + (v-c_Y)^2 + f^2}}
\\]


