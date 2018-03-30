# Front-End Interview Questions
   
  There are some static questions which needs to be known by every front end Developer. I am listing down all those questions here. I will update this page whenever I find some new and interesting concept as a question so that we can keep on refreshing the concepts. Initally, I thought to maintain this page for me alone so that I can refer it whenever needed. Later I think others too can refresh their minds with this page.
  
  This page will be useful for freshers to learn the important concepts whereas for experienced, to test/refresh their minds. Happy Learning!!

## HTML

*What is HTML5?*

 HTML5 is a specification which has following features

  - delivers rich content without the need of additional plugins like FLASH
  - introduced a new concept "web workers"
  - 

 *Standard and Quirks mode* 


 *Explain the difference between SVG and Canvas?*
 
 
 *Explain the difference between HTML4, XHTML and HTML5?*

 



## CSS

*what is the difference between ID and class?*

*what is CSS Box model?*

*what is CSS transition?*

*what is specificity?*

*what are CSS Preprocessors?*

*what are CSS filters?*

*what does a float do?*





## Javascript

*what is 'this' in Javascript?*

 At the time of execution of every function, JavaScript engine sets a property to the function called this which refer to the current execution context. this is always refer to an object and depends on how function is called. There are 7 different cases where the value of this varies. 
1.	In the global context or inside a function this refers to the window object.
2.	Inside IIFE (immediate invoking function) if you use "use strict", value of this is undefined. To pass access window inside IIFE with "use strict", you have to pass this.
3.	While executing a function in the context of an object, the object becomes the value of this
4.	Inside a setTimeout function, the value of this is the window object.
5.	If you use a constructor (by using new keyword) to create an object, the value of this will refer to the newly created object.
6.	You can set the value of this to any arbitrary object by passing the object as the first parameter of bind, call or apply
7.	For dom event handler, value of this would be the element that fired the event


*what are closures?*


Closures are the combination of the function and the lexical environment where the function will be invoked.In full terms, closures are the inner functions which has access to the local variables and outer variables declared either in parents scope or declared gobally.
 
 ```javascript
 // constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  setTimeout(function() {
    this.scoops++;
    console.log('scoop added!');
  }, 500);
};
````
After running the code above, you'd think that dessert.scoops would be 1 after half a millisecond. But, unfortunately, it's not:

      console.log(dessert.scoops);

   Prints:
   0

   Can you tell why?

   The function passed to setTimeout() is called without new, without call(), without apply(), and without a context object. That means the value of this inside the function is the global object and NOT the dessert object. So what actually happened was that a new scoops variable was created (with a default value of undefined) and was then incremented (undefined + 1 results in NaN):

      console.log(scoops);

   Prints:
   NaN

One way around this is to use closure:

``` javascript
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  const cone = this; // sets `this` to the `cone` variable
  setTimeout(function() {
    cone.scoops++; // references the `cone` variable
    console.log('scoop added!');
  }, 0.5);
};
```
      const dessert = new IceCream();
      dessert.addScoop();

   The code above will work because instead of using this inside the function, it sets the cone variable to this and then looks up the cone variable when the function is called. This works because it's using the value of the this outside the function. So if we check the number of scoops in our dessert right now, we'll see the correct value of 1:
const dessert = new IceCream();
dessert.addScoop();

      console.log(dessert.scoops);

   Prints:
   1

 
*what is hoisting?*

*what is the difference between Window.onload and Document.onReady?*

*what is Shadow DOM?*

*when can we use document create Fragment?*

*what is a promise?*

*what is a callback and what are its disadvantages?*

*what is the difference between Function Expression and Function declaration?*

    Function Declaration defines a named function ie., "function" keyword followed by the name of the function. When using function declarations, the function definition is hoised,thus allowing the function to be used before it is defined.
         Syntax:      
            function name(parameters) {
               // write logic here
            }

         Eg: 
           function add(x, y) {
               return x + y;
             }
   
      Function Expressions defines a named or anonymous function. An anonymous function is a function that has no name. Function expressions are not hoised and therefore this function cannot be used before they are defined.
      In the below example, we are seeting anonymous function object equal to a variable

      Syntax:
        let name = function(parameters) {
                     //logic               
                   };
      
       Eg: 
         var sum = function ( x, y) {
                        return x + y;
                     }

      
        Calling a function:-  sum(5, 10);

*call vs bind vs apply?*

*what is the output of the below question?*

      var namesInHat = ["Ron", "Tom", "April", "Ben"];
      namesInHat[999] = "Jean-Ralphio";
      console.log(namesInHat.length)
      console.log(namesInHat[200]);

Solution: 

Length of the array is 1000 and namesInHat[200] is undefined.
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array
https://stackoverflow.com/questions/6499352/does-null-occupy-memory-in-javascript.


## jQuery

*what is the difference between children and find methods in jQuery?*



## General Questions

*what is CORS?*

*what is FOUC?*

*what are your strengths?*

*what are your weaknesses?*

*How can you handle important decisions?*

*How well can you work under Pressure?*

*How best can you integrate multiple stylesheets in your approach?*

*what is the difference between Progressive Enhancement and graceful degradation?*

*How do you clone an object?*

*what is the significance of wrapping JS source file?*

*what is the importance of 'use strict' in javascript?*

*How do you check whether a given input is a number or NOT?*






