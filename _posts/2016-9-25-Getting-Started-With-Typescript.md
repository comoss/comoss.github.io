---
layout: post
title: Getting Started with Typescript
---

Now that Angular 2 has been released you may have noticed, while looking over the docs, that Angular 2 uses Typescript. While I initally found it strange, Typescript is something that has grown on me, and I have started incorporating it into my non-Angular 2 projects at work. 

### What is Typescript? 

Essentially, Typescript is an extension to Javascript that gives you many of the same benefits strongly typed languages, like Java and C#, enjoy like static checking, classes, and interfaces. 

### Why should I use Typescript?

Since most of code that I am currently writing at work revolves around our new ecommerce site that we are building, I enjoy the extra securing that comes from type checking. For example, if I were adding the price of a product plus the price of shipping in regular Javascript:

    function addTotal (price, shipping) {
        return price + shipping;  
    } 
    
    addTotal(10, 5); // 15 :) 
    addTotal(10, '5'); // 105 :(
    
We can see that if two numbers are passed in then things work out well and `addTotal` returns the value we were expecting. However, if a string were to accidentally get passed in, Javascript will concat those two values into a string and return a value that we were not expecting. Now let's take a look at Typescript:

     function addTotal (price: number, shipping: number) : number {
         return price + shipping;
     }

     addTotal(10, 5); // 15
     addTotal(10, '5'); // Argument of type 'string' is not assignable to parameter of type 'number'.

Our first function ran great! We can also see that at the time of compiling down to regular Javascript, Typescript returns a type error stating that we cannot pass a string in for a parameter that should be a number! This is great because now, we know that before anything ran, we have an error and that we need to introduce code to ensure that we are passing in the correct data types. For example we could make sure that we aways pass in a number by doing something like this: 

    addTotal(10, Number('5')) // 15 - tears of joy - ( ͡↑ ͜ʖ ͡↑) 

In addition to having the extra security of type checking, and as we saw above, Typescript compiles down to just regular Javascript and supports many of the es6 features that are currenly only available through using compilers like babel. The provides an enhanced programmer experience. 

In ending, I like Typescript, I like how easy it has been for me to be able to start integrating it into our already exsisting codebase, and the security it provides by ensuring consistency across our codebase. 
