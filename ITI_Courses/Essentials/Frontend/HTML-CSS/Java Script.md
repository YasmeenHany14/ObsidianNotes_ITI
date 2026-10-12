---
notion-id: 11fba0f393fd80c1a435ec54394e7fa5
---
[JavaScript](https://app.notion.com/p/JavaScript-fb2d772917ac450b85684e30c846517a?pvs=21)
  
### Weak and Dynamic typing
- Weak typing: specifing the value datatype at declaration
- Dynamic typing: allows a variable  
	to hold any type of value at any time. It’s typically cited as a benefit  
	for program flexibility by allowing a single variable to represent a value no matter what type form that value may take at any given  
	moment in the program’s logic flow
  
typed values, not typed  
variables. The following built-in types are available:  
• string  
• number  
• boolean  
• null and undefined  
• object  
• symbol (new to ES6)
  
To check variable type use `typeof(var)`
  
- If either value (aka side) in a comparison could be the true or  
	false value, avoid == and use ===.  
	• If either value in a comparison could be of these specific values  
	(0, "", or []—empty array), avoid == and use ===.  
	• In all other cases, you’re safe to use ==. Not only is it safe, but in  
	many cases it simplifies your code in a way that improves read‐  
	ability
  
  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_escape
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence#table
https://www.geeksforgeeks.org/difference-between-array-and-array-of-objects-in-javascript/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode
[Difference between `let` and `var` in JavaScript | Sentry](https://sentry.io/answers/difference-between-let-and-var-in-javascript/#:~:text=The%20difference%20between%20let%20and,in%20which%20they're%20declared.)
https://262.ecma-international.org/5.1/
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects
- Go throught MDN Number - Math - Date - String objects
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects
https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model
https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API
https://developer.mozilla.org/en-US/docs/Web/API
  
One important diff is that
```jsx
func(x);
var x = 10;
// this will not throw an error it will consider x to be undefined which is not correct
func(x);
let x = 10;
// this will throw an undefined error which is the correct behavior
```
  
  
  
search for number.parsefloat
==behavior delegation → search== ⇒ Classes and inheritance?
  
## What is considered true and false
### False
- NaN
- Empty strings
- false
- 0
- null
- undefined
### True
Everything not a false
true
0.5
“0” as a string is not false
Inaccurate float numbers percision will always lead to a false expression because it is not accurate
```jsx
let x = 1.1 + 1.4;
// you would expect the answer to be 2.5 but if you run it on console you get 2.500000000000005
// not quite accurate so
if (1.1 + 1.4 == 2.5) // => false
if ( +(1.1 + 1.4).toFixed(2) !== 2.4) // => true
```
- ==The `+` is a simple way to convert a string returned by `toFixed` back to a number==
  
- Assigning function to a variable is called a function expression
```jsx
let x = function dosmthing() {
}
let x = function() {
}
// adding a name is preferd (refer to chatgpt table listing the diff)
let x = () => console.log('btats')'
```
  
  
![[image 9 3.png]]
Thats just not possible because as long as you are in the inner function the outer function cannot be gone
  
## Polyfilling
- Taking the definition of a newer feature and producing a  
	piece of code that’s equivalent to the behavior, but is able to run in  
	older JS environments.
    
	```jsx
	if (!Number.isNaN) {
	 Number.isNaN = function isNaN(x) {
	 return x !== x;
	 };
	}
	// if Number.isNan not defined in this env, define it
	```
    
- It is better to use an already vetted set of polyfills that you can trust,  
	such as those provided by https://github.com/es-shims/es5-shim and [ES6-Shim](https://github.com/es-shims/es6-shim)
  
## Transpiling
- Taking a piece of code written in a new syntax that old js versions doesn’t support, and converting it to it’s equivilant in the older version syntax.
- You can’t just polyfill new syntax that has been added to the language, it would just throw a syntax error.
- So the better option is to use a tool that converts your newer code  
	into older code equivalents. This process is commonly called “tran‐  
	spiling,” a term for transforming + compiling.
- ==For more refer to You dont know js book page 70==
## substr, slice and substring
https://chatgpt.com/share/670e4cbf-c40c-800d-a787-1ceb94f8d065 ⇒ Chat that shows the diff
  
Primitive types are sent by value but objects are sent by reference (check what is mutable and what is not)
  
  
- It is a good practice to use double quotes inside single or the opposite when the need arises instead of using two of the same type
    
	![[image 1 3 1.png]]
    
# DOM
- querySelector
- querySelectorAll
- getElementById
![[image 2 2 1.png]]
This code adds the target attribute to _blank for all elements with the .tag class
  
# HTML API
- `classList` (add or remove)
- `addEventListener(”event name”, functionToExecute(event oject) ⇒ { ));`
  
# Window
- Used to access the built in functionality of the browser
https://www.geeksforgeeks.org/how-are-the-javascript-window-and-javascript-document-different-from-one-another/
## localStorage API
- A place to store info in the browser rather than to send data to for saving
    
	```jsx
	localStorage.setItem("key", {value});
	localStorage.setItem("key", JSON.stringify(order));
	```
    
- Local storage cannot save objects as objects we need to convert them to strings before saving
  
# Event Listeners
![[image 3 2 1.png]]
https://stackoverflow.com/questions/73425012/window-domcontentloaded-vs-document-domcontentloaded
  
  
- Diff between window and html
	- https://www.geeksforgeeks.org/how-are-the-javascript-window-and-javascript-document-different-from-one-another/
- Diff between inner text and text content
	- https://www.freecodecamp.org/news/innerhtml-vs-innertext-vs-textcontent/
- Diff between parent node and parent element
	- https://www.geeksforgeeks.org/difference-between-dom-parentnode-and-parentelement-in-javascript/
- Diff between window and document DOMContentLoaded
	- https://stackoverflow.com/questions/73425012/window-domcontentloaded-vs-document-domcontentloaded