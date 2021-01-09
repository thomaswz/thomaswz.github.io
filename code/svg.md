# SVG

###### Created 9 Jan 2021, Updated 9 Jan 2021

## Introduction

Graphics options comprise CSS and related; and then SVG (Scalable Vector Graphics).
They will be used to work together.  
There is not much information on SVG, as its its use is straightforward. I think that it is not the first thing that you learn... do by the time you find it you are proficient enough to just "read it".

There is an alternative to `CSS` and its `@keystrokes`. This will be covered in another link i.e. CSS Graphics.

## XML

SVG is equivalent to XML.
Its graphics are called SMIL or Synchronised Media Integration Language.

## Tools

There are limited resources:

- a good resource is [A Guide to SVG Animations ](https://css-tricks.com/guide-svg-animations-smil/) by Sara Soueidan.
- Use [Inkscape](https://inkscape.org/) to create or edit SVG.
- Old faithful: [W3 School SVG](https://www.w3schools.com/graphics/svg_intro.asp)
- Good linke to some code from [Amelia Bellamy-Royds](https://codepen.io/AmeliaBR/pens/popular)

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

### Restart

There is also a `restart` attribute. It can use the following options: `always`, `whenNotActive`, and `never`.

### Repeating

Use `repeatCount="2"` or `"indefinite"`.

Its good to use `repeatDur="01:30"`. This will stop the graphic after 1minute 30s; as these things can get a bit boring if they repeat all the time.

## Linking Animations

Two animation effects can be linked throug the naming of the one with the `d` attribute i.e. `d="circle01-animate"` and then in second animation: `begin="circle01-animate.begin + 1s`".

- Note that `begin` will also accept ` 01:30` i.e. one minute and 30 seconds later.
- `begin="circle01-animate.end"` will also work - starting the second animation once the first has ended.
- negative timing can be used i.e. ` - 10s`.

## Changing Values

In the code below, the `keyTimes` are linked to the `values=` abover them. The `keyTimes` are percentages(%) of the `dur=2s` (duration).

```svg
<animate
    xlink:href="#orange-circle"
    attributeName="cx"
    from="50"
    to="450"
    dur="2s"
    begin="click"
    values="50; 490; 350; 450"
    keyTimes="0; 0.5; 0.8; 1"
    fill="freeze"
    id="circ-anim" />
```

## Timing

### `calcMode`

The timing of animations is set with `calcMode` i.e. `calcMode="linear"`.
It can be manipulated. There are the following options:

- `linear` i.e. smooth
- `discrete`i.e. staggered / steps or jumps.
- `paced` i.e. it will smooth the speed of the motion for all the points. Key times are ignored.
- `spline` allows the value of the transitions to be changed. `spline` then as the following additions:
  - `values` are linked to `keyTimes`. These control the movement.
  - `keyTimes` are linked to `keySplines`. These are four values (or more) that control the cubic-bezier line. They are the xy of the start and end of a graph where **x** is initial start angle and **y** is the final (approach) angle. See [Bezier Curve](https://en.wikipedia.org/wiki/B%C3%A9zier_curve).
    The rest of the curve smooths the transition between the x-start and y-approach angle.

### Animation transitions

The transtions `end` can be linked between the animations.
If the value of the initial is set as: `end="circle02.begin"`, and the second circle has `begin="click"` then when it is clicked the linked animation will **end**. :-)

This can result in actions from the user i.e. from clicking an object it then progresses to the next event. i.e. changing colour... a colour is selected and then the object moves.

### `min` and `max`

The timing durations can also have min and max values that are set in seconds of standard time i.e. 1:30 - 1min 30s

### Resolving timing

The code calculates `dur`, `repeatCount`, `repeatDur`, and `end`; and then applies the `min` and `max` values.

## Animation progression

This assists with the transtion of one animation to another by adjusting the start to the prior end. For this use:

- `additive`: this determines if the start values are absolute or relative to the prior animation. It accepts `sum` or the default `replace`. i.e. replace the ending start / end with the current.
- `accumulate`: from the above - just that instead of replacing (the default) the new values are added onto the existing.

These require `from` and `to`; however if set to `sum` then the values are a progression from where the last animation ended.
i.e. otherwise the transition will all start from the beginning point.

# Morphing

Animations can morpth using the `<path>` and `d` values i.e. **d** is for "data".  
**_For the animations to work the d structure must be exactly the same._**
The is an excellent example of [Counting Numbers](https://codepen.io/felixhornoiu/pen/dovub).
It is very simple code i.e. one timing value i.e. 6s; and then
