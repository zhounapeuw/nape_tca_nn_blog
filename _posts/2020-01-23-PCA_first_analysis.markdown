---
layout: post
title:  "PCA First Pass Analysis"
date:   2020-01-23 14:11:55 -0800
categories: jekyll update
---

Here I use sklearn's PCA to reduce the dimensionality of trial-averaged data. Since my data are in xarray format, I have to import a library called sklearn-xarray, which
possesses a wrapper function that facilitates the compatibility of the PCA object with xarray data:

```python
from sklearn_xarray import wrap
from sklearn.decomposition import PCA

pca_xr_wrapper = wrap(PCA(n_components=3), reshapes='yx') # create PCA object and specify dimension to perform PCA on

Xt = pca_xr_wrapper.fit_transform(xr_flatten_pix_trial.transpose()) # fit/transform estimator; transpose to apply PCA on pixels
```

![frame_image!](/_assets/frame0_img.PNG)

![PC_pixel_map]({{ site.url }}/_assets/pc_pixelmap.PNG)

![PC_timecourse!!]({{ site.url }}/_assets/pc_timecourse.PNG)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
