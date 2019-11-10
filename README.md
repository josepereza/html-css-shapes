# html-css-shapes
Make Your Content Look More Interesting With CSS Shapes

![Alt text](shape.png)
# Now we’ve seen it in action, how does CSS shapes work?

CSS shapes is a set of rules for wrapping content around custom shapes and path. It does not actually draw the shape, but rather gives instructions to the browser on what the float area looks like (We can still draw the shape using the clip-path CSS property, this feature just isn’t part of CSS Shapes). Currently it only works when paired with a float property (in the future, with the help of CSS Exclusions, it will be possible to do so without it). Also, it’s not possible to wrap text from both sides of a shape.

The CSS Shapes specification Level 1 defines three properties:

    shape-outside
    shape-image-threshold
    shape-margin

# shape-outside

The shape-outside CSS property defines a shape around which adjacent inline content should wrap. By default, inline content wraps around its margin box; by accepting different functions, shape-outside provides a way to customize this wrapping.

Some supported values are:

* circle()
```
.basic-circle {
  width: 150px;
  height: 150px;
  shape-outside: circle();
  float: left;
}

// Circle with a custom radius
.radius-circle {
  width: 150px;
  height: 150px;
  shape-outside: circle(30%);
  float: left;
}

// Circle with a custom radius and position (which defines the center of the circle)
.radius-position-circle {
  width: 150px;
  height: 150px;
  shape-outside: circle(50% at 0 50%);
  float: left;
}

```
* polygon() —The polygon() function allows you to “go crazy” and create any kind of shape. It gets as an argument, a list of at least 3 coordinates. This, for example, is how you would create a simple 5 pointed star:
```
.star-shape {
  width: 150px;
  height: 150px;
  shape-outside: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
  float: left;
}

```
Creating shapes by hand is a bit of a pain, so you can use online tools such as this one to generate the correct CSS, 
which you can just copy-paste to your project.

  *   url() — With this function you can create dynamic float borders from an image. 
    It only supports png/gif/svg formats thought. Also note that you need the actual image present as an <img> tag for it to work.
    
 ```
 <img src="some-image.png" class="custom-shape" />
<p>some text...</p>
<style>
.custom-shape {
  float: left;
  shape-outside: url(some-image.png);
}
</style>
 ```
 

# shape-image-threshold

When using shape-outside along with an image value (using the url() function), the shape-image-threshold property is used to adjust the minimum opacity level of pixels that will be used to create the shape. Its value must be in the range between 0 and 1.
```
.shape-from-image {
  float: left;
  shape-outside: url(some-image.png);
  shape-image-threshold: 0.1;
}

```
# shape-margin
If the shape you created with shape-outside is too close to the text, you can adjust its margin from the content using this property.

```
.circle {
  shape-outside: circle(50%);
  shape-margin: 20px;
  float: left;
}
```
