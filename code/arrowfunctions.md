# Arrow Functions

###### Created 10 May 2020, Updated 10 May 2020

## Introduction

Wow! I really did not understand arrow functions... it was so difficult to find a clear explanation about them as there are a couple of variations that can be intimidating when trying to work out what is going on. I was really helped by the following video and link: [Arrow Functions in JavaScript](https://tylermcginnis.com/arrow-functions/) by [Tyler McGinnis](https://tylermcginnis.com/).

Arrow functions are used to make the code shorter. Note that they handle **`this`** differently i.e. context.

## Approach

> Its best to start with [Functions](functions.md).  
> Then to read this;  
> Then to move onto [Promises and Callbacks ](./promisescallbacks.md); and  
> Only then to review [Async Await](./asyncetc.md).  
> After all of this... comes [Try... Catch](/trycatch.md).

> It is also important to know about [this](./this.md), as it will trip you up... and then you will learn about `this` :-).

## To Recap

<dl>
<dt>Function Declaration</dt>
<dd><code> function myFunction(a, b) { return a * b }</code></dd>
<dt>Function Expression</dt>
<dd><code> let multiply = function (a, b) { return a * b }</code></dd>
</dl>

In the above, `function` requires a `return`.

## Arrow Functions

Translating the above to arrow functions, the **function expression** becomes:  
`let multiply = (a, b) => { return a * b}`

## One Line Arrow Functions

One line (one statement) arrow functions can leave out the **`return`**.  
`let multiply = (a, b) => a * b`

Note that for one line functions, the `( )` can also be left out:  
`let multiply = a, b => a * b`

## Dealing with context and `this`

( Please see the [this](./this.md) when referring to `this`)

Arrow functions don't create their own context, so the this does not have to be as restrictive.

> The following is to be taken under caution... I need to have worked more with arrow functions to understand the content below...

To create a function that retuns an `object` without using the `function... return` syntax, the arrow function syntax requires wrapping the function body in `( )`.

```javascript
this.setState(() => ({ object: object }));
```

The **_`( )`_** aound the **`{ }`**.

## Further ES6 shortening

ES6 allows further shorthand (as the names are the same... I need to understand this better) and so the above code can be further shortened:

```javascript
this.setState(() => object);
```

and... with the ongoing qualification:

```javascript
this.setState((nextState) => console.log(nextState) || { object: object });
```
