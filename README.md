[![Published on webcomponents.org](https://img.shields.io/badge/webcomponents.org-published-blue.svg)](https://beta.webcomponents.org/element/vogelrh/ken-burns-image)
# \<scalable-image-grid\>

A Polymer web component that displays a grid of `iron-images` of equal aspect ratios, scales the images to
fit the host container while maintaining the specified image aspect ratio. The grid remains responsive by modifying the columns
to maintain a minimum image width.

The user can specify the number of columns to display, the image aspect ratio, and a minimum image width. The grid will
try to layout the images within the specified number of columns, scaling the images to fit within the width of the
columns. However, if the image width would be less than the specified minimum width, then the grid will reduce the
number of columns so that the image widths remain greater that the minimum width. Once the grid reduces to a single
column, the images continue to scale however to fit the container. As the image scales, the image aspect ratio is always
maintained.

Most aspects of the component are configured by custom CSS variables. (See Styling section below.) However, the CSS
variables are also exposed as component properties. (See API reference.)

_[API Docs](https://vogelrh.github.io/scalable-image-grid/components/scalable-image-grid/)_
<br/>_[Demo](https://vogelrh.github.io/scalable-image-grid/components/scalable-image-grid/demo)_

Install the component with bower:

```bower install scalable-image-grid --save```

##### Things to Consider:
This component works best with a series of images of that have equal aspect ratios and that all share the same orientation
(portrait or landscape). All internal layout and scaling calculations are based off of the width of an image. The aspect
ratio is controlled by specifying the height as a percentage of the width. For example if you have an image with a 4:3
aspect ratio, then the image height CSS variable / component property would have a value of 75, which is `(height / width * 100)`
for a landscape oriented image, or a value of 133.3 for a portrait oriented image.

### Usage

A typical usage scenario would involve configuring and styling the grid by defining custom CSS variables then using the
`loadImageList` API method to load the component with an array containing the image URLs. One can then listen for the
`scalable-image-selected` event to handle the user clicking on an image.

```
<style>
:root {
  --scalable-image-grid-max-columns: 4;
  --scalable-image-grid-gutter: 15;
  --scalable-image-grid-min-image-width: 250;
  --scalable-image-grid-image-height: 56;
  --scalable-image-grid-background-color: auto;
  --scalable-image-grid-image-style: {
    box-shadow: 0 12px 15px 0 rgba(0, 0, 0, 0.34);
  };
  ...
}
</style>
...
<body>
...
<scalable-image-grid id="imgGrid" ripple></scalable-image-grid>
...
  <script>
    window.addEventListener('WebComponentsReady', function(e) {
      var images = [
        {source: "myImage1.jpg", order: 12},
        {source: "myImage2.jpg", order: 2},
        {source: "myImage3.jpg", order: 3},
        {source: "myImage4.jpg", order: 4},
        {source: "myImage5.jpg", order: 5},
        {source: "myImage5.jpg", order: 6},
        {source: "myImage7.jpg", order: 7},
        {source: "myImage8.jpg", order: 8},
        {source: "myImage9.jpg", order: 9},
        {source: "myImage10.jpg", order: 10},
        {source: "myImage11.jpg", order: 11},
        {source: "myImage12.jpg", order: 1}
      ];

      var imgGrid = document.getElementById("imgGrid");
      imgGrid.loadImageList(images);

      document.getElementById('imgGrid').addEventListener('scalable-image-selected', function (e) {
        console.log(e.detail.imageIndex); //Respond to selection...
      })
    })
  </script>
</body>
```

### Styling

The following custom CSS properties and mixins are available for stying and control:

Custom property  | Description | Default
-----------------|-------------|--------
`--scalable-image-grid-max-columns` | Maximum number of columns of images | 3
`--scalable-image-grid-min-image-width` | The minimum width  an image will be scaled to before adjusting the number of grid columns. | 100 (px)
`--scalable-image-grid-gutter` | The number of pixels between the images in the grid. | 1 (px)
`--scalable-image-grid-image-height` | Maintains image aspect ratio by specifying image height as a percentage of width. The default value represents a 4:3 aspect ratio. | 75 (%)
`--scalable-image-grid-background-color` | Background color of grid. The gutter color | currentColor
`--scalable-image-grid-image-style` | A mix-in that can apply styling to each iron-image component. | {}

__Note:__ the numeric custom CSS properties are unitless numbers that are internally converted to the units shown in parenthesis.


### License

#### The MIT License ([MIT](https://opensource.org/licenses/MIT))
Copyright (c) 2017 Robert Vogel
