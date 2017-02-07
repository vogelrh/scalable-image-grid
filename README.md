[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://beta.webcomponents.org/element/vogelrh/ken-burns-image)
# \<scalable-image-grid\>

A Polymer web component that will display a grid of `iron-images` of equal aspect ratios and will scale the images to
fit the host container while maintaining the image aspect ratio. The grid remains responsive by modifying the columns 
to maintain a minimum image width.

The user can specify the number of columns to display, the image aspect ratio, and a minimum image width. The grid will
layout the images within the specified number of equal width columns, scaling the images to fit within the 
columns. However, if the column width would be less than the specified minimum image width, then the grid will reduce the
number of columns so that the image widths remain greater that the minimum width. Once the grid reduces to a single
column, the images continue to scale however to fit the container. As the image scales, the image aspect ratio is always
maintained.

_[API Docs](https://vogelrh.github.io/ken-burns-image/components/ken-burns-image/)_

_[Demo](https://vogelrh.github.io/ken-burns-image/components/ken-burns-image/demo)_

Install the component with bower:

```bower install scalable-image-grid --save ```

### Usage

