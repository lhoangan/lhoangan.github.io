---
layout: post

title:  "Mutual Guidance meets Supervised Contrastive Learning: Vehicle Detection
in Remote Sensing Images"
author: 'Hoàng-Ân Lê, Heng Zhang, Minh-Tan Pham, Sébastien Lefèvre'
affiliation: 'University of South Brittany, Vannes France'

date:   2022-07-29

excerpt: ""
project: true
feature: 
thumbnail: 

tag:
- research
- computer vision
comments: false
---

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
