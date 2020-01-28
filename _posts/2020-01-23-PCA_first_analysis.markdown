---
layout: post
title:  "PCA First Pass Analysis"
date:   2020-01-23 14:11:55 -0800
categories: jekyll update
---

Here's a picture of a single frame. You can see a few neurons activating (grouped white pixels):

![frame_image_](/nape_tca_nn_blog/images/frame0_img.PNG)

To get a better sense of the data going into downstream analysis, I take data with the dimensions
(y_pixel, x_pixel, samples) and perform the following preprocessing:
1) Flatten the first two dimensions - y and x dimensions in y_x
2) Load the behavioral data (ie. stimulus onset times)
3) Calculate a vector of samples that encompass a trial's window
4) Make a matrix of those sample vectors across trials and extract fluorescence data using those sample indices
5) Average across trials to get a matrix of (pixels, trial_samples)

Here I use sklearn's PCA to reduce the dimensionality of trial-averaged data. Since my data are in xarray format, I have to import a library called sklearn-xarray, which
possesses a wrapper function that facilitates the compatibility of the PCA object with xarray data:

```python
from sklearn_xarray import wrap
from sklearn.decomposition import PCA

pca_xr_wrapper = wrap(PCA(n_components=3), reshapes='yx') # create PCA object and specify dimension to perform PCA on

Xt = pca_xr_wrapper.fit_transform(xr_flatten_pix_trial.transpose()) # fit/transform estimator; transpose to apply PCA on pixels
```
Below I plot the eigenvectors reshaped into a spatial format. Each PC's spatial map indicates how much each
original pixel in the dataset contributes to the PC. Note that PC 0 and 1 possess positive pixels that group to form neurons,
meaning PCA is pulling out biologically relevant neural activity and neurons.

![PC_pixel_map](/nape_tca_nn_blog/images/pc_pixelmap.PNG)

Here I'm showing each PCs timecourse (ie. samples in PC space). Indeed these PCs may reflect biological fluctuations.
PC0 shows a characteristic calcium indicator rise and decay starting about 250 ms after stimulus onset, whereas PC2 shows
perhaps an anticipatory increase. PC1, I'm not entirely sure about, but may be some consumatory reward behavior. Since PCs
are composed of a linear combination of features that can be negative or positive, it can be tough to interpret what the PCs mean.

![PC_timecourse!!](/nape_tca_nn_blog/images/pc_timecourse.PNG)

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
