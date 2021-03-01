# imgaug

This python library helps you with augmenting images for your machine learning projects.
It converts a set of input images into a new, much larger set of slightly altered images.

[![Build Status](https://travis-ci.org/aleju/imgaug.svg?branch=master)](https://travis-ci.org/aleju/imgaug)
[![codecov](https://codecov.io/gh/aleju/imgaug/branch/master/graph/badge.svg)](https://codecov.io/gh/aleju/imgaug)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/1370ce38e99e40af842d47a8dd721444)](https://www.codacy.com/app/aleju/imgaug?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=aleju/imgaug&amp;utm_campaign=Badge_Grade)

![64 quokkas](examples_grid.jpg?raw=true "64 quokkas")

Features:
* Most standard augmentation techniques available.
* Techniques can be applied to both images and keypoints/landmarks on images.
* Define your augmentation sequence once at the start of the experiment, then apply it many times.
* Define flexible stochastic ranges for each augmentation, e.g. "rotate each image by a value between -45 and 45 degrees" or "rotate each image by a value sampled from the normal distribution N(0, 5.0)".
* Easily convert all stochastic ranges to deterministic values in order to augment different batches of images in exactly the same way. (E.g. images and their respective heatmaps. If an image is rotated, you want its heatmap to be rotated by the exactly same amount.)
* Optionally run the augmentations in background processes, improving performance of experiments.

Documentation:
* [http://imgaug.readthedocs.io/en/latest/source/examples_basics.html](http://imgaug.readthedocs.io/en/latest/source/examples_basics.html) - Quick example code to use the library.
* [http://imgaug.readthedocs.io/en/latest/source/augmenters.html](http://imgaug.readthedocs.io/en/latest/source/augmenters.html) - Example code for each augmentation technique.
* [http://imgaug.readthedocs.io/en/latest/source/modules.html](http://imgaug.readthedocs.io/en/latest/source/modules.html) - API.
* This README contains more examples. See further below.

The images below show examples for most augmentation techniques (values written in the form `(a, b)` mean that a value was randomly picked from the range `a  1=zoom in, <1=zoom out), translates them by `TPX` pixels or `TPC` percent, rotates them by `R` degrees and shears them by `SH` degrees. Interpolation happens with order `O` (0 or 1 are good and fast). Areas can appear in the resulting image, which have no corresponding area in the original image. `M` defines, how to handle these. If `M='constant'` then `CVAL` defines a constant value with which to fill the area. |
| PiecewiseAffine(S, R, C, O, M, CVAL) | Places a regular grid of points on the image. The grid has `R` rows and `C` columns. Then moves the points (and the image areas around them) by amounts that are samples from normal distribution N(0,`S`), leading to local distortions of varying strengths. `O`, `M` and `CVAL` are defined as in `Affine`. |
| PerspectiveTransform(S, KS) | Applies a random four-point perspective transform to the image (kinda like an advanced form of cropping). Each point has a random distance from the image corner, derived from a normal distribution with sigma `S`. If `KS` is set to True (default), each image will be resized back to its original size. |
| ElasticTransformation(S, SM) | Moves each pixel individually around based on distortion fields. `SM` defines the smoothness of the distortion field and `S` its strength. |
| Alpha(F, A, B, PCH) | Augments images using augmenters `A` and `B` independently, then overlays the result using alpha `F`. Both `A` and `B` default to doing nothing if not provided. E.g. use `Alpha(0.9, A)` to augment images via `A`, then blend the result, keeping 10% of the original image (before `A`). If `PCH` is set to true, the process happens channel-wise with possibly different `F` (`A` and `B` are computed once per image). |
| AlphaElementwise(F, A, B, PCH) | Same as `Alpha`, but performs the blending pixel-wise using a continuous mask (values 0.0 to 1.0) sampled from `F`. If `PCH` is set to true, the process happens both pixel- and channel-wise. |
| SimplexNoiseAlpha(A, B, PCH, SM, UP, I, AGG, SIG, SIGT) | Similar to `Alpha`, but uses a mask to blend the results from augmenters `A` and `B`. The mask is sampled from simplex noise, which tends to be blobby. The mask is gathered in `I` iterations (default 1-3), each iteration is combined using aggregation method `AGG` (default max, i.e. maximum value from all iterations per pixel). Each mask is sampled in low resolution space with max resolution `SM` (default 2 to 16px) and upscaled to image size using method `UP` (default: linear or cubic or nearest neighbour upsampling). If `SIG` is true, a sigmoid is applied to the mask with threshold `SIGT`, which makes the blobs have values closer to 0.0 or 1.0. |
| FrequencyNoiseAlpha(E, A, B, PCH, SM, UP, I, AGG, SIG, SIGT) | Similar to `SimplexNoiseAlpha`, but generates noise masks from the frequency domain. Exponent `E` is used to increase/decrease frequency components. High values lead to more pronounced high frequency components. Use values in the range -4 to 4, with -2 roughly generated cloud-like patterns. |


 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)