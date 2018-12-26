---
layout: post
title: Learning CSS
date: 2018-12-26 18:33 -0500
---
## CSS
CSS is a complex language that packs quite a bit of power.It allows us to add layout and design to our pages, and it allows us to share those styles from element to element and page to page. Before we can unlock all of its features, though, there are a few aspects of the language we must fully understand.

First, it’s crucial to know exactly how styles are rendered. Specifically, we’ll need to know how different types of selectors work and how the order of those selectors can affect how our styles are rendered. We’ll also want to understand a few common property values that continually appear within CSS, particularly those that deal with color and length.

Let’s look under the hood of CSS to see exactly what is going on.
We’ll begin breaking down exactly how styles are rendered by looking at what is known as the cascade and studying a few examples of the cascade in action. Within CSS, all styles cascade from the top of a style sheet to the bottom, allowing different styles to be added or overwritten as the style sheet progresses.

For example, say we select all paragraph elements at the top of our style sheet and set their background color to orange and their font size to 24 pixels. Then towards the bottom of our style sheet, we select all paragraph elements again and set their background color to green, as seen here.
{% highlight html %}
p {
  background: orange;
  font-size: 24px;
}
p {
  background: green;
}

{% endhighlight %}
Because the paragraph selector that sets the background color to green comes after the paragraph selector that sets the background color to orange, it will take precedence in the cascade. All of the paragraphs will appear with a green background. The font size will remain 24 pixels because the second paragraph selector didn’t identify a new font size.

## Cascading Properties
The cascade also works with properties inside individual selectors. Again, for example, say we select all the paragraph elements and set their background color to orange. Then directly below the orange background property and value declaration, we add another property and value declaration setting the background color to green, as seen here.

{% highlight html %}
p {
  background: orange;
  background: green;
}
{% endhighlight %}
Because the green background color declaration comes after the orange background color declaration, it will overrule the orange background, and, as before, our paragraphs will appear with a green background.

All styles will cascade from the top of our style sheet to the bottom of our style sheet. There are, however, times where the cascade doesn’t play so nicely. Those times occur when different types of selectors are used and the specificity of those selectors breaks the cascade. Let’s take a look.

## Calculating Specificity
Every selector in CSS has a specificity weight. A selector’s specificity weight, along with its placement in the cascade, identifies how its styles will be rendered.
The higher the specificity weight of a selector, the more superiority the selector is given when a styling conflict occurs. For example, if a paragraph element is selected using a type selector in one place and an ID selector in another, the ID selector will take precedence over the type selector regardless of where the ID selector appears in the cascade.

##HTML
{% highlight html %}
<p id="food">...</p>

{% endhighlight %}
# CSS
{% highlight html %}
 food {
    
  background: green;
}
p {
  background: orange;
}
{% endhighlight %}
Here we have a paragraph element with an id attribute value of food. Within our CSS, that paragraph is being selected by two different kinds of selectors: one type selector and one ID selector. Although the type selector comes after the ID selector in the cascade, the ID selector takes precedence over the type selector because it has a higher specificity weight; consequently the paragraph will appear with a green background.

## Combining Selectors
So far we’ve looked at how to use different types of selectors individually, but we also need to know how to use these selectors together. By combining selectors we can be more specific about which element or group of elements we’d like to select.

For example, say we want to select all paragraph elements that reside within an element with a class attribute value of hotdog and set their background color to brown. However, if one of those paragraphs happens to have the class attribute value of mustard, we want to set its background color to yellow. Our HTML and CSS may look like the following:
#HTML
{% highlight html %}
<div class="hotdog">
  <p>...</p>
  <p>...</p>
  <p class="mustard">...</p>
</div>

{% endhighlight %}
## CSS
{% highlight html %}
.hotdog p {
  background: brown;
}
.hotdog p.mustard {
  background: yellow;
}

{% endhighlight %}
When selectors are combined they should be read from right to left. The selector farthest to the right, directly before the opening curly bracket, is known as the key selector. The key selector identifies exactly which element the styles will be applied to. Any selector to the left of the key selector will serve as a prequalifier.

## Specificity Within Combined Selectors

When selectors are combined, so are the specificity weights of the individual selectors. These combined specificity weights can be calculated by counting each different type of selector within a combined selector.

Looking at our combined selectors from before, the first selector, .hotdog p, had both a class selector and a type selector. Knowing that the point value of a class selector is 0-1-0 and the point value of a type selector is 0-0-1, the total combined point value would be 0-1-1, found by adding up each kind of selector.

The second selector, .hotdog p.mustard, had two class selectors and one type selector. Combined, the selector has a specificity point value of 0-2-1. The 0 in the first column is for zero ID selectors, the 2 in the second column is for two class selectors, and the 1 in the last column is for one type selector.

Comparing the two selectors, the second selector, with its two classes, has a noticeably higher specificity weight and point value. As such it will take precedence within the cascade. If we were to flip the order of these selectors within our style sheet, placing the higher-weighted selector above the lower-weighted selector as shown here, the appearance of their styles would not be affected due to each selector’s specificity weight.

{% highlight html %}

.hotdog p.mustard {
  background: yellow;
}
.hotdog p {
  background: brown;
}

{% endhighlight %}

## Layering Styles with Multiple Classes

One way to keep the specificity weights of our selectors low is to be as modular as possible, sharing similar styles from element to element. And one way to be as modular as possible is to layer on different styles by using multiple classes.

Elements within HTML can have more than one class attribute value so long as each value is space separated. With that, we can place certain styles on all elements of one sort while placing other styles only on specific elements of that sort.

We can tie styles we want to continually reuse to one class and layer on additional styles from another class.

Let’s take a look at buttons, for example. Say we want all of our buttons to have a font size of 16 pixels, but we want the background color of our buttons to vary depending on where the buttons are used. We can create a few classes and layer them on an element as necessary to apply the desired styles.
## HTML
{% highlight html %}
<a class="btn btn-danger">...</a>
<a class="btn btn-success">...</a>

{% endhighlight %}

## CSS
{% highlight html %}
.btn {
  font-size: 16px;
}
.btn-danger {
  background: red;
}
.btn-success {
  background: green;
}

{% endhighlight %}
Here you can see two anchor elements, both with multiple class attribute values. The first class, btn, is used to apply a font size of 16 pixels to each of the elements. Then, the first anchor element uses an additional class of btn-danger to apply a red background color while the second anchor element uses an additional class of btn-success to apply a green background color. Our styles here are clean and modular.
## CSS Property Values
We’ve used a handful of common CSS property values already, such as the keyword color values of red and green. You may not have thought too much about them; that’s okay. We’re going to take time now to go over some previously used property values as well as to explore some of the more common property values that we’ll soon be using.

Specifically, we’ll look at property values that relate to colors and length measurements.

## Colors
All color values within CSS are defined on an sRGB (or standard red, green, and blue) color space. Colors within this space are formed by mixing red, green, and blue color channels together, mirroring the way that televisions and monitors generate all the different colors they display. By mixing different levels of red, green, and blue, we can create millions of colors—and find nearly any color we’d like.

Currently there are four primary ways to represent sRGB colors within CSS: keywords, hexadecimal notation, and RGB and HSL values.

{% highlight html %}
.task {
  background: maroon;
}
.count {
  background: yellow;
}

{% endhighlight %}

## Hexadecimal Colors

Hexadecimal color values consist of a pound, or hash, #, followed by a three- or six- character figure. The figures use the numbers 0 through 9 and the letters a through f, upper or lower case. These values map to the red, green, and blue color channels.

In six-character notation, the first two characters represent the red channel, the third and fourth characters represent the green channel, and the last two characters represent the blue channel. In three-character notation, the first character represents the red channel, the second character represents the green channel, and the last character represents the blue channel.

{% highlight html %}
.task {
  background: #800000;
}
.count {
  background: #ff0;
}

{% endhighlight %}
Hexadecimal color values have been around for a while, and they have become fairly popular because they offer a large number of color options. They are, however, a little difficult to work with, especially if you’re not too familiar with them. Fortunately Adobe has created Adobe Kuler, a free application that provides a color wheel to help us find any color we want and its corresponding hexadecimal value.

## RGB & RGBa Colors

RGB color values are stated using the rgb() function, which stands for red, green, and blue. The function accepts three comma-separated values, each of which is an integer from 0 to 255. A value of 0 would be pure black; a value of 255 would be pure white.

As we might expect, the first value within the rgb() function represents the red channel, the second value represents the green channel, and the third value represents the blue channel.
{% highlight html %}
.task {
  background: rgb(128, 0, 0);
}
.count {
  background: rgb(255, 255, 0);
}

{% endhighlight %}
RGB color values may also include an alpha, or transparency, channel by using the rgba() function. The rgba() function requires a fourth value, which must be a number between 0 and 1, including decimals. A value of 0 creates a fully transparent color, meaning it would be invisible, and a value of 1 creates a fully opaque color. Any decimal value in between 0 and 1 would create a semi-transparent color.

## HSL & HSLa Colors

HSL color values are stated using the hsl() function, which stands for hue, saturation, and lightness. Within the parentheses, the function accepts three comma-separated values, much like rgb().

The first value, the hue, is a unitless number from 0 to 360. The numbers 0 through 360 represent the color wheel, and the value identifies the degree of a color on the color wheel.

The second and third values, the saturation and lightness, are percentage values from 0 to 100%. The saturation value identifies how saturated with color the hue is, with 0 being grayscale and 100% being fully saturated. The lightness identifies how dark or light the hue value is, with 0 being completely black and 100% being completely white.

{% highlight html %}
.task {
  background: hsl(0, 100%, 25%);
}
.count {
  background: hsl(60, 100%, 50%);
}

              
{% endhighlight %}
HSL color values, like RGBa, may also include an alpha, or transparency, channel with the use of the hsla() function. The behavior of the alpha channel is just like that of the rgba() function. A fourth value between 0 and 1, including decimals, must be added to the function to identify the degree of opacity.
## Lengths
Length values within CSS are similar to colors in that there are a handful of different types of values for length, all of which serve distinct purposes. Length values come in two different forms, absolute and relative, each of which uses different units of measurement.

## Absolute Lengths
Absolute length values are the simplest length values, as they are fixed to a physical measurement, such as inches, centimeters, or millimeters. The most popular absolute unit of measurement is known as the pixel and is represented by the px unit notation.
## Pixels

The pixel is equal to 1/96th of an inch; thus there are 96 pixels in an inch. The exact measurement of a pixel, however, may vary slightly between high-density and low-density viewing devices.

Pixels have been around for quite some time and are commonly used with a handful of different properties. The code here is using pixels to set the font size of all paragraphs to 14 pixels.

{% highlight html %}
p {
  font-size: 14px;
}
{% endhighlight %}
## Relative Lengths

In addition to absolute length values, there are also relative length values. Relative length values are a little more complicated, as they are not fixed units of measurement; they rely on the length of another measurement.

Percentages, represented by the % unit notation, are one of the most popular relative values. Percentage lengths are defined in relation to the length of another object. For example, to set the width of an element to 50%, we have to know the width of its parent element, the element it is nested within, and then identify 50% of the parent element’s width.
{% highlight html %}
.col {
  width: 50%;
}
{% endhighlight %}
## Em

The em unit is also a very popular relative value. The em unit is represented by the em unit notation, and its length is calculated based on an element’s font size.

A single em unit is equivalent to an element’s font size. So, for example, if an element has a font size of 14 pixels and a width set to 5em, the width would equal 70 pixels (14 pixels multiplied by 5).
{% highlight html %}
.banner {
  font-size: 14px;
  width: 5em;
}
              
{% endhighlight %}
When a font size is not explicitly stated for an element, the em unit will be relative to the font size of the closest parent element with a stated font size.




              
