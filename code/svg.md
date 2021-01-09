# SVG

###### Created 9 Jan 2021, Updated 9 Jan 2021

## Introduction

Graphics options comprise CSS and related; and then SVG (Scalable Vector Graphics).
They will be used to work together.  
There is not much information on SVG, as its its use is straightforward. I think that it is not the first thing that you learn... do by the time you find it you are proficient enough to just "read it".

There is an alternative to `CSS` and its `@keystrokes`. This will be covered in another link i.e. CSS Graphics.

## Tools

There are limited resources:

- a good resource is [A Guide to SVG Animations ](https://css-tricks.com/guide-svg-animations-smil/) by Sara Soueidan.
- Use [Inkscape](https://inkscape.org/) to create or edit SVG.
- Old faithful: [W3 School SVG](https://www.w3schools.com/graphics/svg_intro.asp)

## Code

### Animation identification

For **animation** its best to identify the object that will be used.

```svg
<rect id="cool_shape"
<animate xlink:href="#cool_shape" ....>
```

Alternatively keep the animation within the objects definers.

### CSS Manipulation

Use the following to identify CSS attributes:

- Then `attributeName="cx"` is the identifier that will change i.e. the **"x"** axis.
  - It can only handle one attribute.
  - If there is confusion with html id's then use `XMLNS` or `attributeType`. If not there or set to `auto`... the browser will search through all to find i.e. so better to identify.
- The following are what is available in [CSS Attributes](https://slides.com/sarasoueidan/styling-animating-svgs-with-css#/10)
- See the example below:

```svg
<rect>
  <animate
    attributeType="CSS"
    attributeName="opacity"
    from="1"
    to="0"
    dur="5s"
    repeatCount="indefinite"
  />
</rect>
```

- see the following code below:

```svg
<circle id="my-circle" r="30" cx="50" cy="50" fill="orange" />

  <animate
    xlink:href="#my-circle"
    attributeName="cx"
    from="50"
    to="450"
    dur="1s"
    begin="click"
    fill="freeze" />
```

### Completion

SVG can also use the following: `freeze` - for stopping the animation; and `remove` - to remove the animation effect.
