---
layout: post

title:  "Mutual Guidance meets Supervised Contrastive Learning: Vehicle Detection
in Remote Sensing Images"
author: 'Hoàng-Ân Lê, Heng Zhang, Minh-Tan Pham, Sébastien Lefèvre'
affiliation: 'University of South Brittany, Vannes France'

date:   2022-07-29

excerpt: ""

project: true

feature: /assets/images/posts/2020-11-02/garden_paper.jpg

thumbnail: /assets/images/posts/2020-11-02/eden80.jpg

tag:
- research
- computer vision
- CGI
- dataset
- multimodal
- semantic segmentation
- optical flow
- surface normals
comments: false
---

<p style="text-align: right"><i>
A garden enclosed, my sister, my bride,
a garden enclosed, a fountain sealed! <br>
Your branches are a grove of pomegranates,
with all choicest fruits <br>
(Songs of Songs, 4:12-13)
</i></p>

## Abstract

Vehicle detection is an important but challenging problem in
Earth observation due to the intricately small sizes and varied appearances of the
objects of interest.
In this paper, we use these issues to our advantage by considering them
results of latent image augmentation. In particular, we propose using
supervised contrastive loss in combination with 
a mutual guidance matching process 
to helps learn stronger object representations and tackles the misalignment of
localization and classification in object detection.
Extensive experiments are performed to understand
the combination of the two strategies and show the benefits
for vehicle detection on aerial and satellite images, achieving
performance on par with state-of-the-art methods designed for
small and very small object detection.
As the proposed method is domain-agnostic, it might also be used for
visual representation learning in generic computer vision problems.
Source code will be released upon acceptance to facilitate reproduction.

## Paper

[WACV](https://openaccess.thecvf.com/content/WACV2021/papers/Le_EDEN_Multimodal_Synthetic_Dataset_of_Enclosed_GarDEN_Scenes_WACV_2021_paper.pdf) |
[arxiv](https://arxiv.org/abs/2011.04389)



## Citation

If you find the material useful please consider citing our work

{% raw %}
```
@article{le22cmgsrs,
 author = {L{\^{e}}, Ho{\`{a}}ng{-}{\^{A}}n and Zhang, Heng and Pham, Minh-Tan
 and Lefèvre, Sébastien},
 title = {{Mutual Guidance meets Supervised Contrastive Learning: Vehicle Detection
in Remote Sensing Images}},
 booktitle = {Remote Sensing},
 year = {2022},
}
```
{% endraw %}
