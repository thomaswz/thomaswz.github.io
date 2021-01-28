# `this`

###### Created 10 May 2020, Updated 10 May 2020

## Introduction

I was hit with this... as I am sure most beginner coder's are... working with a function that returns `undefined` when the code all looks fine, there are just a few functions nested together.

** Under Construction **... read up on [this](https://tylermcginnis.com/this-keyword-call-apply-bind-javascript/) before completing.

## Context

`function` creates its own context... and so a nested function i.e.

```javascript
function addAnd() {
    function() { return this and that...}
}
```

The inner function will be difficult to reach and it will have its own _inner context_.

**Vue / Nuxt** can deal with this by declaring a variable in the top function as follows:

```javascript
data() {
    return {
        a: ''
    }
},
methods: {
function addAnd() {
    let _self = this
    function() {
        _self.a = 'catfish'
        return this and that...
        }
console.log(a) // 'catfish'
   }
}
```

## Arrow Functions

[Arrow Functions](./code/arrowfunctions.md) **don't** create their own context.
