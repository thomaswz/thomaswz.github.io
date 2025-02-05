# CSS Animation

###### Created 9 Jan 2021, Updated 9 Jan 2021

## Introduction

This was created as an extention of the [SVG notes](/svg).

## Code

CSS code uses `@keyframes` as below:

```css
@keyframes example {
  0% {
    left: 0;
  }
  50% {
    left: 320px;
  }
  80% {
    left: 270px;
  }
  100% {
    left: 300px;
  }
}
```

## SMIL

CSS also uses SMIL as the animation framework.  
Note that 1
In the `@keyframes` the timing values can be set for each keyframe, within the keyframe.
