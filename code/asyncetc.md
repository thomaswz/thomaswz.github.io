# Async, Await...

###### Created 10 May 2020, Updated 10 May 2020

**under construction**

## Introduction

Wow! It is difficult to start here, without a foundation of the parts below.

## Approach

> Its best to start with [Functions](/code/functions).  
> Then to move onto [Arrow Functions](/code/arrowfunctions);  
> Then to move onto [Promises and Callbacks ](/code/promisescallbacks); and  
> Only then to review [Async Await](/code/asyncetc).  
> After all of this... comes [Try... Catch](/code/trycatch)

> It is also important to know about [this](/code/this), as it will trip you up... and then you will learn about `this` :-).

## Statements

I need to qualify this page! I am learning, and this is what I have learnt. It does not mean that it is correct, efficient or accepted practice. In Javascript, not everything is as it seems... or is explained.

## Bundled thinking

For some reason I bundled them together when thinking about these topics... it may have been because they are thought of as advancements to old coding challanges.

## Current approach

I find the history noise... and it leads to some confusion.

### Promises

When I `request` something, then I will get a `response`. I will `then` do the `next` thing that I wanted to do.

If my `request` is confused, and so does not resolve itself so I don't get a `response`, it means that I have probably 'dropped the ball'... luckily I can `catch` the error before it before the code breaks..

```javascript
var promise = new Promise().then().catch()
var promise = new Promise(function(resolve, reject, next){})
.then(return...)
.catch(function(e) {console.log(e)})
```

### Try catch

If I want to `try` something out, and it has issues... then I can at least `catch` them before the code breaks.

### Async await

Some functions can run and return before others are finished. If this needs to be controlled then we must tell the asynchronous `asyn` code to `await` until some code has run before other code runs... like please wait for me to get your details before I tell you what to do next.
