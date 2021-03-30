---
layout: post

title:  "DeepTerRa: Deep Terrain Models from ALS Point Clouds via Rasterization"
author: 'Ho&agrave;ng-&Acirc;n L&ecirc;, Florent Guiotte, Minh-Tan Pham, Sébastien Lefèvre, Thomas Corpetti'
affiliation: 'France Énergies Marines, IRISA, Université Bretagne-Sud'

date:   2021-03-08

excerpt: ""

project: true

feature: /assets/images/posts/2021-05-18/cover.png

thumbnail: /assets/images/posts/2021-05-18/cover.png

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
---

## Abstract

Despite the popularity of deep-learning-based methods,
there is hardly any for extracting digital terrain models
(DTM) from airborne laser scanning (ALS) point clouds. This might
be due to the
data-structure discrepancy and the lack of dedicated large-scale
annotated dataset. This paper serves as a first endeavor to extract DTM from ALS
point clouds using deep networks and rasterization.
To that end, a large-scale dataset of ALS point clouds and reference DTMs, featuring
various scene categories (urban, forest, mountainous) is collected from open sources.
A domain-agnostic approach using an off-the-shelf deep architecture is
explored together with various rasterization strategies to analyze the challenges
of geospatial data.
Experiments conducted on this dataset with well-established baseline show the
interest of the proposed approach, with sub-metric error level. The data and source
code will be released for reproducibility upon acceptance.

## Citation

If you find the material useful please consider citing our work

{% raw %}
```
@inproceedings{le21dtm,
 author = "L{\^{e}}, Ho{\`{a}}ng{-}{\^{A}}n and Guiotte, Florent and Pham, Minh-Tan and Lef{\`{e}}vre, S{\'{e}}bastien and Corpetti, Thomas",
 title = {{DeepTerRa: Deep Terrain Models from ALS Point Clouds via Rasterization}},
 booktitle = {TBD},
 year = {2021},
}
```
{% endraw %}
