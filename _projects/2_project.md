---
layout: page
title: Deformable Superpoint
description: Geometric Vision (16822) Course Project
img: assets/img/project_dsuperpt_results.png
importance: 2
category: team
---

November 2022 - December 2022 

[final report](/assets/pdf/projects-dsuperpoint-final-report.pdf)

[code](https://github.com/gsethi2409/pytorch-superpoint)

We aim to answer the question – can deformable convolutions improve the performance of CNN-based interest point detectors?

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
