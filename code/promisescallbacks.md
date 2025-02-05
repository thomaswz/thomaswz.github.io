# Promises and Callbacks

###### Created 10 May 2020, Updated 10 May 2020

### Under construction

## Introduction

I became confused with `promises` and `callbacks` as I did not have a foundation in `functions`; and wanted to skip over them to `async await` as that seemed to be what all the material suggests... "callback hell" is dealt with through `async await`... so why not just skip over to there!!!

> `Coding` Promises are all about **timing** and **ability**. While JavaScript starts off tasks sequentially, it does **not** wait for other tasks to finish before starting tasks. It has to be instructed to do so.

## Approach

> Its best to start with [Functions](./functions.md).  
> Then to move onto [Arrow Functions](./arrowfunctions.md);  
> Then to move onto [Promises and Callbacks ](./promisescallbacks.md); and  
> Only then to review [Async Await](./asyncetc.md).
> After all of this... comes [Try... Catch](./trycatch.md)

> It is also important to know about [this](./this.md), as it will trip you up... and then you will learn about `this` :-).

## Its all about Timing, then Ability

### Requirements

I understand a **promise** more in legal terms i.e. a commitment to perform an activity. "I promise that I will...".  
In `coding` terms, it refers to a **future** activity. The commitment to perform a future activity.

Computers are responsive to commands, i.e. _"I promise to go and fetch that data from that location and bring it back to make it available for further processing"_ will result in the computer attempting to perform the task of going to _"that location"_ and to fulfill its promise of _"fetching that data"_ and then bringing it back for the next activity.

### Sequencing - getting the ducks in a row

The task above of going to a location, performing the required activity and then returning with a result will **take time**.

_Now JavaScipt does not wait for tasks to complete..._ so other functions that _should_ wait for that activity to complete before performing their task are triggered at basically the same time and so will perform activities without the required resources (_"the fetched data"_). This will create _errors_.

This is why the **`.then`** is attached to the main promise. i.e. Once the promise has been fulfilled... **`.then`** perform the next tast... and **`.then`** the next one etc..

While the result is that this can look very messy and become confusing... **_Callback Hell_**... to work with, is it the nature of the JavaScript that requires this **coded sequencing** of activities.

### Ability

The other part of a promise is the **ability** to complete it. For all the best intentions of the task that is going to _"go to that location to fetch that data and bring it back for further processing"_; it could encounter challanges that will result in it not being able to complete the task i.e. the data could not be available, the network could go down etc..

The task is unable to be completed for factors "beyond the control of the task". This problem (**error**) has to be **recognised**, **communicated** and **responded** to; so that the whole program does not stop because this activity has "failed". i.e. all the other tasks are waiting for this activity... and without further instruction... will wait and wait. They have no ability to know otherwise.

### Timing Part B - where when what how

While the task has been setup:

- it will start when called
- it will take time to perform
- it will either succeed or fail

So its activities need to be **resolved** so the other program can know what to do next.

> This is what the promise code is setup to handle - sequencing, ability and timing.

## The Code

So the basic code of a promise is a **function expression**:
(from [tyler](https://tylermcginnis.com/async-javascript-from-callbacks-to-promises-to-async-await/))

```javascript
function onSuccess()  {
    console.log('Success')
}

function onError() {
    console.log("error")
}
let promise = new Promise( resolve, reject) {
    resolve() "deals with the task that needs to be performed",
    reject() " is the response i.e. was it completed successfully or not",
}
//  note that I am sure Max refers to (request, response, next)
// i.e. the requested task, and if it was resolved successfully;
// the response if "error" and then what to do "next"
promise.then(onSuccess)
promise.catch(onError)
```
