---
layout: page
title: Deformable Superpoint
description: Geometric Vision (16822) Course Project
img: assets/img/project_dsuperpt_results.png
importance: 2
category: team
---

`November 2022 - December 2022, Team of 2`

## Documentation

* [final report](/assets/pdf/projects-dsuperpoint-final-report.pdf)
* [code](https://github.com/gsethi2409/pytorch-superpoint)
* [final presentation](https://docs.google.com/presentation/d/15jcwfE36iIIaCNkeAjqrDYsAGHk0I1pnO6mXjRNDyK0/edit?usp=sharing)
* [misc-doc (limited access)](https://docs.google.com/spreadsheets/d/10oSbnph0kD4mL2bi44w22mS-ij-5XqmbMt--m8M3-s4/edit?usp=sharing)


## Situation

I had recently read the deformable convolution (d-convs) paper. During one of the Geometry Vision classes, I was curious to know if this new method of convolution would be able to improve interest point detection. Since d-convs have the ability to focus on the geometric spatial extent of the object, it would improve local feature detection.
I decided to take this up as a course project!

## Task

The goal was to answer the question – **can deformable convolutions improve the performance of CNN-based interest point detectors?** We chose to conduct this experiment on SuperPoint -- a SOTA learning-based interest point detector.

We integrated deformable convolutions within the VGG-style encoder of SuperPoint and evaluated the detected interest points on several metrics and downstream geometric vision tasks (SfM, Homography Estimation).

##### Challenges

It was challenging to implement the d-conv layer. First, I referred to the [PyTorch implementation of d-convs](https://pytorch.org/vision/stable/generated/torchvision.ops.DeformConv2d.html). Due to lack of appropriate documentation, I was unable to debug shape mismatch errors and didn't fully grasp how to use it. On further review, we saw that alot of git repositories had custom implementations of the d-conv layer. 

Thus, we read several blogs/git repos to understand alternate ways to implement d-convs. I isolated the SuperPoint encoder module into a Google Colab notebook and tried to plug-and-play custom implentations of d-convs. I continuously referred to the paper to evaluate each step in the implementation. I verified the new d-conv-based encoder by training it successfully for 1 epoch on a mini MSCOCO dataset. 

## Action

I used the deformable convolution v2 implementation from [PyTorch-Deformable-Convolution-v2](https://github.com/developer0hye/PyTorch-Deformable-Convolution-v2). Next, I inetgrated the updated d-conv-based, VGG-style encoder into the SuperPoint architechture as below. For this, we chose the [PyTorch-SuperPoint](https://github.com/eric-yyjau/pytorch-superpoint) repo.  

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_dsuperpt_arch.png" title="project poster" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


Once this was complete, I wrote the config yaml files for training. We began training and continuously monitored the loss curves.

We first trained MagicPoint on Synthetic Shapes Dataset. I wrote a script to plot interest points detected on the Synthetic Shapes test set. Some results can be seen below.




 Next, Shruthi used this to generate pseudo-groundtruth labels for MSCOCO. We then trained SuperPoint on MSCOCO. 


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_dsuperpt_results.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_dsuperpt_recon.png" title="recon" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


## Results
In the work, we showed that deformable convolutions have the potential for improving the repeatability and minimizing localization error of learning-based interest point detectors. Furthermore, when used for downstream tasks like homography estimation or SfM, we proved that these new interest points perform better. While homography estimation gives significantly better results than learning-based and classical methods, SfM shows minor improvement.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/project_dsuperpt_metrics.png" title="project poster" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
