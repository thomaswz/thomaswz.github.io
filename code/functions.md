# Functions

###### Created 10 May 2020, Updated 10 May 2020

## Introduction

Wow! I really did not understand functions... it was so difficult to find a clear explanation about Functions. They are used in so may ways that when looking at them, they are not easily understood intuitively.

> Its best to start here.  
> Then to move onto [Arrow Functions](/code/arrowfunctions);  
> Then to move onto [Promises and Callbacks ](/code/promisescallbacks); and  
> Only then to review [Async Await](/code/asyncetc).  
> After all of this... comes [Try... Catch](/code/trycatch).

> It is also important to know about [this](/code/this), as it will trip you up... and then you will learn about `this` :-).

## Statements

<dl>
<dt>Statements</dt>
<dd>Statements are <b>instructions</b> to be "executed" by a computer. Statements are <u>not</u> functions.  An example of a statement is:<code> a = 5; b = 4; c = a + b </code> </dd>

<dt>Functions</dt>
<dd>Functions are groups of statements.  Functions are groups of code blocks.<br>
<i>Statements</i> grouped together in <i>code blocks</i> to be executed together are <i>functions</i>. Code blocks are <code>{ }</code>.</dd>

<dt>Invoking / Calling Functions</dt>
<dd><i> Calling </i> a function is asking for it to be executed i.e. to run. <i> Invoking </i> a function is running the functions.<br>
Functions need to be invoked.  They can be run by an <i>event, invoked or self-invoked</i>(see below).<br>
A <code> return </code> value is then "returned" back to the caller. <code> Return </code> exits the function.</dd>

<dt>The Operator <code>( )</code></dt>
<dd>Referred to as the <i>operator</i>: "<code> ( ) </code>" invokes the function i.e. <code> add() </code> would call/invoke the <code> add </code> funtion. 
<br> A function can be self invoked by putting the <i>operator</i> at the end of the function i.e. <code> function add(x, y) { return x + y}() </code>
</dd>

<dt> Declaring a Function </dt>
<dd> A function is declared as follows: <br>
<code> function myFunction(a, b) { return a * b }</code> <br>
<code>"function" </code> <i>declares</i> the function. <br>
<code>"myFunction"</code> is the <i>name</i> of the function. <br>
<code>"(a, b)"</code> the <code>"( )"</code> contain the function <i>parameters</i>.<br>
<code>"{ }"</code> inside the <code> { } </code> are the <i> code arguments </i> to be executed. <b> Local variables </b> are created and deleted in the function <i>code arguments</i>.</dd>

<dt>Function Expression</dt>
<dd>We have reviewed a <i>function declaration above</i> i.e. <code> function myFunction(a, b) { return a * b }</code>. <br> </dd>
A <i> function expresssion </i> is as follows: <code> let multiply = function (a, b) { return a * b }</code> <br>
A <i> function expression </i> is declaring a function as a <b>variable</b>.</dd>

<dt>Context</dt>
<dd>Functions <b>create their own context</b>. This means that when <code> const and let </code> are used within a function, they remain in the function. Note that <code> var </code> creates a global reference and so should be avoided. <br>
The <code>this</code>, when used in the function, refers to the context within the function... unless it is an <a href="./arrowfunctions"> arrow function</a>. <br>
This means that functions, and certainly imbedded functions i.e. functions within functions often can't be <i> reached </i>. The <code> return </code> exits the the function, and provides it with the <b>output</b> that will be expected when calling the function. i.e. <code>{ return a * b } </code> or <code>{... return a }</code>.<br>
Please refer to the <a href='./this'> this</a> page for a further explanation of accessing functions context.<br>
<a href='./arrowfunctions'>Arrow functions</a> create don't create their own context</dd>

<dt>Keywords</dt>
<dd>Function key words are: <code>break, continue, debugger, do... while, for, function, if... else, return, switch, try... catch.</code><br>
<code> return </code> exits the function. <br>
<code> try... catch </code> is for error handling.</dd>
</dl>
