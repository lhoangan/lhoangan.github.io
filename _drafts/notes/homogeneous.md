---
layout: post
title: "Modeling projection"
date: 2020-10-29
excerpt: "About homogeneous coordinate"
thumbnail: /assets/images/posts/2018-07-30/pinhole_camera.png
feature: /assets/images/posts/2018-07-30/camera_obscura.jpg
caption: _photo credit_ Camera Obscura [Vondelpark, Amsterdam](https://www.stefnagel.com/22412066/vondelpark-amsterdam) by Stef Nagel

tags:
- research
- computer vision
- camera model
- intrinsic parameter
- homogeneous coordinate
- projection
comments: true
share: true
---

The [camera model and intrinsic parameters]({% post_url 2018-07-30-camera-params %})
gives

{% include image image="camera_model.png" caption="<b>Figure 2</b> Pinhole
camera model. Redrawn from 
<a target='_blank'
href='https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html'>
OpenCV documentation</a>"
%}


\\[
  x = s_u\dfrac{fX}{Z} \qquad \text{and} \qquad y = s_v\dfrac{fY}{Z}, \qquad(1)
\\]
thus
\\[
  u = s_u\dfrac{fX}{Z} + c_x \qquad \text{and} \qquad v = s_v\dfrac{fY}{Z} + c_y \qquad(2)
\\]

\\[
\begin{align} 
    g: \mathbb{R}^3 &\rightarrow  \mathbb{R}^2 \\\\ 
    \left(X,Y,Z\right) &\mapsto \left(X\dfrac{f}{Z}, Y\dfrac{f}{Z}\right)
\end{align}
\\]


**Equation (1) is a linear transformation?**


