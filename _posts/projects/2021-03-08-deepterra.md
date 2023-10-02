---
title:  "DeepTerRa: <u>Deep</u> Digital <u>Ter</u>rain Models from ALS Point
Clouds via <u>Ra</u>sterization"
author: Hoàng-Ân Lê, Florent Guiotte, Minh-Tan Pham, Sébastien Lefèvre, Thomas Corpetti'
affiliation: 'France Énergies Marines, IRISA, University of South Brittany, France'

date:   2021-03-08
layout: post
project: true
excerpt: "
We collect from open sources a large-scale dataset of ALS point clouds and
corresponding DTMs. The baseline method extracts DTMs directly from ALS point
clouds via rasterization techniques, coined DeepTerRa.
"
feature: /assets/images/posts/2021-03-08/deepterraFeat.png
thumbnail: /assets/images/posts/2021-03-08/deepterraThumb1.png

tag:
- research
- computer vision
- dataset
- multimodal
- dtm
- digital terrain models
- rasterization
- ALS point clouds
- GAN
comments: false
---

## Abstract

Despite the popularity of deep neural networks in various domains, the
extraction of digital terrain models (DTMs) from airborne laser scanning (ALS)
point clouds is still challenging. This might be due to the lack of the
dedicated large-scale annotated dataset and the data-structure discrepancy
between point clouds and DTMs. To promote data-driven DTM extraction, this
article collects from open sources a large-scale dataset of ALS point clouds and
corresponding DTMs with various urban, forested, and mountainous scenes. A
baseline method is proposed as the first attempt to train a deep neural network
to extract DTMs directly from ALS point clouds via rasterization techniques,
coined DeepTerRa. Extensive studies with well-established methods are performed
to benchmark the dataset and analyze the challenges in learning to extract DTM
from point clouds. The experimental results show the interest of the agnostic
data-driven approach, with submetric error level compared to methods designed
for DTM extraction.

## Paper

[arXiv](https://arxiv.org/abs/2206.03778) -  [IEEE OpenAccess](https://ieeexplore.ieee.org/document/9794452)

## Data

Download the dataset [DeepTerRa v0.1](https://share-irisa.univ-ubs.fr/sixp/pub/DeepTerRa/)

There are 2 zip files for downloading in bulk or downloading each scene by going
into each folder.

The data are stored in `*.mat` file, which can be read in Python using the `scipy`
package. All the rasterized data are stored as `np.ndarray` in the read dictionary.
```
from scipy.io as sio
mat = sio.loadmat('filename.mat')
print (mat.keys())
```
We have performed the rasterization and offset correction following the
discovery mentioned in the paper, so the data sizes are not always round numbers
(There are shapes of, eg. 1996x1994). We have made sure all rasters of the
same scene stay the same shapes.

Please also let us know by sending email to `hoang-an.le[at]irisa.fr` if you
encounter some problems with the data.

The original `las` point clouds can be downloaded from the same link, in
`las_tiles` directory.
As we have observed an aligning problem when trying to rasterize these point
clouds with the original DTMs, and the provided DTMs on our website have been
offset to best match with the rasters (see the paper for more information).

### Currently known problems

1. DTM of `DALES/5145_54340` has a corrupted strip of empty column (zero values)

## Source code

The exact code is not not ready to be shared at this moment.
However, it is mostly borrowed from the pix2pix code which you can get from
[the original repo](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix).
You'll need to work on the dataloader to get the rasterizations and DTM from
the `mat` files.

## Citation

If you find the material useful please consider citing our work

{% raw %}
```
@article{le22deepterra,
    author = "L{\^{e}}, Ho{\`{a}}ng{-}{\^{A}}n and Guiotte, Florent and Pham, Minh-Tan and Lef{\`{e}}vre, S{\'{e}}bastien and Corpetti, Thomas",
    title={Learning Digital Terrain Models From Point Clouds: ALS2DTM Dataset and Rasterization-Based GAN},
    journal={IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing (JSTARS)},
  year={2022},
  volume={15},
  number={},
  pages={4980-4989},
}
```
{% endraw %}
