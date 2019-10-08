## imagefluency: Image Statistics Based on Processing Fluency <img src="man/figures/logo.png" align="right" />

<!-- badges: start -->
[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](http://www.repostatus.org/badges/latest/active.svg)](http://www.repostatus.org/#active)
[![Travis build status](https://travis-ci.org/stm/imagefluency.svg?branch=master)](https://travis-ci.org/stm/imagefluency)
[![CRAN status](https://www.r-pkg.org/badges/version/imagefluency)](https://cran.r-project.org/package=imagefluency)
[![CRAN downloads](http://cranlogs.r-pkg.org/badges/imagefluency)](https://cran.r-project.org/package=imagefluency)
[![codecov](https://codecov.io/github/stm/imagefluency/branch/master/graphs/badge.svg)](https://codecov.io/github/stm/imagefluency)
  <!-- badges: end -->

## Overview

**imagefluency** is an simple R package for image fluency scores. The
package allows to get scores for several basic aesthetic principles that
facilitate fluent cognitive processing of images. If you want to try it out before installing, you can find an interactive Shiny app [here](http://mayer.shinyapps.io/imagefluency/) (alpha version).
    
The main functions are:

* `img_contrast()`  to get the visual contrast of an image.
* `img_complexity()`  to get the visual complexity of an image (equals
   1 minus image simplicity)
* `img_self_similarity()`  to get the visual self-similarity of an image
* `img_simplicity()`  function to get the visual simplicity of an image (equals
   1 minus image complexity).
* `img_symmetry()`  to get the vertical and horizontal symmetry of an
   image.
* `img_typicality()`  to get the visual typicality of a list of images relative
   to each other

Other helpful functions are:

* `img_read()`  wrapper function to read images into R using `read.bitmap()` from the
  [readbitmap](https://github.com/jefferis/readbitmap) package
* `rgb2gray()`  convert images from RGB into grayscale (might speed up computation)
* `run_imagefluency()`  to launch a Shiny app locally on your computer for an interactive demo of the
   main functions


The main author is [Stefan Mayer](http://github.com/stm/).

## Installation

You can install the current stable version from CRAN.
```r
install.packages("imagefluency")
```

To download the latest development version from Github use the `install_github` function of the `devtools` package.
```r
# install devtools if necessary
if (!require("devtools")) install.packages("devtools")
# install imagefluency from github
devtools::install_github('stm/imagefluency')
```
Use the following link to report bugs/issues: <https://github.com/stm/imagefluency/issues>

## Example usage

```r
# visual contrast
#
# example image file (from package): bike.jpg
bike_location <- system.file("example_images", "bike.jpg", package = "imagefluency")
# read image from file
bike <- img_read(bike_location)
# get contrast
img_contrast(bike)

# visual symmetry
#
# read image
rails <- img_read(system.file("example_images", "rails.jpg", package = "imagefluency"))
# get only vertical symmetry
img_symmetry(rails, horizontal = FALSE)
```

See the package [vignette](https://stm.github.io/imagefluency/articles/imagefluency.html) for more details (or type `vignette("imagefluency", package = "imagefluency")` into the R console).

## Citation

If you want to cite this package in a scientific journal or in any other
context, run the following code in your `R` console:

``` r
utils::citation(package = "imagefluency")
```
There is currently a publication in preparation corresponding this
package and the citation will be updated once it’s published.


## Dependencies
The `img_complexity` function relies on the packages [R.utils](https://cran.r-project.org/package=R.utils) and [magick](https://github.com/ropensci/magick). The `img_self_similarity` function relies on the packages [OpenImageR](https://github.com/mlampros/OpenImageR), [pracma](https://cran.r-project.org/package=pracma), and [quadprog](https://cran.r-project.org/package=quadprog). The `img_read` function relies on the [readbitmap](https://github.com/jefferis/readbitmap) package. The `run_imagefluency` shiny app depends on [shiny](https://github.com/rstudio/shiny).

## References

* Mayer, S. & Landwehr, J, R. (2018). Quantifying Visual Aesthetics
Based on Processing Fluency Theory: Four Algorithmic Measures for
Antecedents of Aesthetic Preferences. *Psychology of Aesthetics,
Creativity, and the Arts*, *12*(4), 399--431. 
doi: [10.1037/aca0000187](https://doi.org/10.1037/aca0000187)

* Mayer, S. & Landwehr, J. R. (2018). Objective measures of design
typicality. *Design Studies*, *54*, 146--161.
doi: [10.1016/j.destud.2017.09.004](https://doi.org/10.1016/j.destud.2017.09.004)
