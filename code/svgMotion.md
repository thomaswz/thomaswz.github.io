# SVG Animating Motion

###### Created 9 Jan 2021, Updated 9 Jan 2021

## Introduction

SMIL has `<animateMotion>` that guides animation along a `<path>`.
It builds on the [inital SVG](//code/svg), just adding:

- `keyPoints`
- `rotate`
- `path`: this is expressed like `d`

and the `calcMode="paced"`as default.

# Tools

The official [w3.org notes](https://www.w3.org/TR/SVG2/animate.html#AnimationAttributesAndProperties).

### Starting point

The start point is where the object is i.e. the M0,0 below is not the top left of the viewport. Thus the object is offset from its base with the initial `m` values.

```svg
<animateMotion
xlink:href="#circle">
dur="6s"
begin="click"
path="M0,0 c3.2..."
    />
```

### Referencing `<path>` with `<mpath>`

`<mpath>` can be used to reference another object path as follows:

```svg
<animateMotion>
    <mpath xlink:href="#motionPath">
</animateMotion>
```

## Priorities

The order of priorites are **ascending**:

- `from`, `by` and `to`
- `values`
- `path`
- `mpath`

## Rotate

`rotate` takes the following values:

- `auto` which follows the angle of the motion path direction
- `auto-reverse` the motion path + 180 degrees
- a number i.e. the degree of rotation.

### Scale

Use the following to change the angle of the moving that is moving:

```svg
<g id="car" transform="scale (-1, 1) translate(-234.4, -182.8)">
```

## Other

### keyPoints

The following considerations - similar to standard SVG:

- `keyPoints` of values between 0 and 1
- `keyTimes` matching to the `keyPoints` (set `calcMode="linear"` for `keyTimes` to work)

For a **reverse** set the `keyPoints` to "0 1" i.e. rather than "1 0"

### Text

Use the following for text:

#### Initial setup:

```svg
<svg width="500" height="350" viewBox="0 0 500 350">
  <path id="myPath" fill="none" stroke="#000000" stroke-miterlimit="10" d="M91.4,104.2c3.2-3.4,18.4-0.6,23.4-0.6c5.7,0.1,10.8,0.9,16.3,2.3
  c13.5,3.5,26.1,9.6,38.5,16.2c12.3,6.5,21.3,16.8,31.9,25.4c10.8,8.7,21,18.3,31.7,26.9c9.3,7.4,20.9,11.5,31.4,16.7
  c13.7,6.8,26.8,9.7,41.8,9c21.4-1,40.8-3.7,61.3-10.4c10.9-3.5,18.9-11.3,28.5-17.8c5.4-3.7,10.4-6.7,14.8-11.5
  c1.9-2.1,3.7-5.5,6.5-6.5"/>
  <text>
    <textpath xlink:href="#myPath">
      Text laid out along a path.
    </textpath>
  </text>
</svg>
```

#### Animate

Then use `<animate>` and not `<animateMotion>` in the above code:

```svg
<text>
    <textpath xlink:href="#myPath">
      Text laid out along a path.

      <animate attributeName="startOffset" from="0%" to ="100%" begin="0s" dur="5s" repeatCount="indefinite" keyTimes="0;1" calcMode="spline" keySplines="0.1 0.2 .22 1"/>
    </textpath>
  </text>
```

## Transform

`<animateTransform>` is all of the above plus `type` with values and use from, by and to:

- `translate`: `<tx> [, <ty>]`
- `scale`: `<sx> [, <sy>]`
- `rotate`: `<rotate-angle> [<cx> <cy>]`
- `skewX`: `<skew-angle>`
- `skewY`: `<skew-angle>`

See the following by Sara for the details of [transform](https://www.sarasoueidan.com/blog/svg-transformations/) and then the code:

```svg
  <animateTransform
      xlink:href="#deepPink-rectangle"
      attributeName="transform"
      attributeType="XML"
      type="rotate"
      from="0 75 75"
      to="360 75 75"
      dur="2s"
      begin="0s"
      repeatCount="indefinite"
      fill="freeze"
      />
```

This is a cool example of a SVG:

```svg
<svg viewBox="0 0 160 160" width="160" height="160">
  <circle cx="80" cy="80" r="50" />
  <g transform=" matrix(0.866, -0.5, 0.25, 0.433, 80, 80)">
    <path d="M 0,70 A 65,70 0 0,0 65,0 5,5 0 0,1 75,0 75,70 0 0,1 0,70Z" fill="#FFF">
      <animateTransform attributeName="transform" type="rotate" from="360 0 0" to="0 0 0" dur="1s" repeatCount="indefinite" />
    </path>
  </g>
  <path d="M 50,0 A 50,50 0 0,0 -50,0Z" transform="matrix(0.866, -0.5, 0.5, 0.866, 80, 80)" />
</svg>
```

**Note that it recommended to use CSS animations**  
These are considered stable and better developed as the offset rules in SVG are complicated and could mess up up complex patterns.

## Set

Use `<set>` to fix any values required.
