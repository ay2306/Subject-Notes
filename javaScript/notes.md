<center>
<h1>JavaScript</h1>
</center>

**Question 1:** What are anonymous functions?

**Answer:** 

```javascript
const f1 = function(x){
    return x;
}
```
Functions without names are called anonymous functions. They are helpful in callbacks.

 
**Question 2:** What is argument objects in javascript?

**Answer:**

```javascript
function f(){
    console.log(arguments);
}
f(1,2,3,"name")
/*
OUTPUT
{
    0: 1
    1: 2
    2: 3
    3: "name"
}
*/
```

**Note:** Arrow functions do not have arguments object.

**Question 3:** How to get type of a variable in javascript?

**Answer:** Use typeof

```javascript
var x = "ayush"
console.log(typeof x);
/*
OUTPUT
string
*/
```
 
**Question 4:** Explain `this` in javascript.

**Answer:** 

```javascript
function hello(){
    return "Hello " + this.name;
}
var obj = {
    name : "random dude"
}
obj.f = hello;
obj.f();
/*
OUTPUT: hello random dude
*/
```
- **Problem with using variable name**
```javascript
var user = {
    name : "ABC",
    f : function(){
        console.log("Hello " + user.name)
    }
}
var other = user;
user.name = "DEF";
other.f();
user.f();
/*
OUTPUT:
Hello DEF
Hello DEF
*/
```

- **Arrow function do not have this:** They do not have their own this and refers to closest this in their outermost context 

**Question 5:** What is callback? (very important)

**Answer:** A callback is a plain JavaScript function passed to some method as an argument or option. It is a function that is to be executed after another function has finished executing, hence the name ‘call back‘. In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions.

Example

```javascript
function errorHandler(error){
    if(error.status == 404)console.log("Not found error");
    ...
}
function display(page){
    ...
}
function displayWebPage(filename, correctCallback, errorCallback){
    const int status = read(filename);
    if(status == 200)correctCallback(filename);
    else errorCallback(status);
} 
displayWebPage("home.html",display,errorHandler);
```

**Question 6:** What are closures and how can we use closure property to implement private access scope in javascript?

**Answer:** See this code

```javascript
function f(){
    var name = "ABC"
    function printName(){
        console.log(name);
    }
    return printName();
}
const access = f();
access();
/*
Output: ABC
*/
```

See how printName had access to name variable even when it was imported outside. This property is called closure in javascript. This is a hint towards using class property of javascript.

We can create private access like this

```javascript
const classObject = (function(){
    var privateCounter = 0;
    function changeByValue(x){
        privateCounter+=x;
    }
    return {
        increment : function(){
            changeByValue(1);
        },
        decrement : function(){
            changeByValue(-1);
        },
        getValue : function(){
            return privateCounter;
        }
    }
})()
classObject.increment();
classObject.increment();
console.log(classObject.getValue());
classObject.decrement();
classObject.decrement();
classObject.decrement();
console.log(classObject.getValue());
```
 
**Question 7:** What are cookies? How do you write, read and delete cookies in javascript?

**Answer:** Cookies are data, stored in small text files, on your computer. When a web server has sent a web page to a browser, the connection is shut down, and the server forgets everything about the user. Cookies were invented to solve the problem "how to remember information about the user":
- When a user visits a web page, his/her name can be stored in a cookie.
- Next time the user visits the page, the cookie "remembers" his/her name.
1. **Write-**
```javascript
document.cookie =  "name=random"
document.cookie =  "age=15"
```
2. **Read-**
```javascript
document.cookie.split(';')
```
3. **Delete-** Some browsers do not let you delete cookies manually, though you can simply add expiry date to that. 


**Question 8:** What is the difference between Attributes and Property?

**Answer:**
- **Attributes-**  provide more details on an element like id, type, value etc.
- **Property-**  is the value assigned to the property like type=”text”, value=’Name’ etc
 
**Question 9:** Different ways HTML can accessed using javascript.

**Answer:**
1. getElementById `document.getElementById("id")`
2. getElementsByClassName `document.getElementsByClassName("className")`
3. getElementsByTagName `document.getElementsByTagName("p")`
4. querySelector `document.querySelector("p.example");`
 
**Question 10:** Different ways to declare variable in javascript

**Answer:**
1. `var` : The JavaScript variables statement is used to declare a variable and, optionally, we can initialize the value of that variable.
2. `const` : The idea of const functions is not allow them to modify the object on which they are called. When a function is declared as const, it can be called on any type of object.
3. `let` : It is a signal that the variable may be reassigned, such as a counter in a loop, or a value swap in an algorithm. It also signals that the variable will be used only in the block it’s defined in.

**Issue with var:** Try this code
```javascript
for(var i = 0; i < 5; ++i)
    console.log(i)
console.log(i) // Does not throw error
```
 
**Question 11:** What is the difference between `null` and `undefined`?

**Answer:** `undefined` means a variable has been declared but has not yet been assigned a value. On the other hand, `null` is an assignment value. It can be assigned to a variable as a representation of no value. Also, `undefined` and `null` are two distinct types: undefined is a type itself (undefined) while `null` is an object.
 
**Question 12:** What is event bubbling?

**Answer:**
1. Event Bubbling: Consider this HTML
```html
<div>
    <button>Click me</button>
</div>
<script>
    document.querySelector('div').addEventListener('click',function(){
        console.log('div');
    })
    document.querySelector('button').addEventListener('click',function(){
        console.log('button');
    })
</script>
```
When I click on button, trigger happens for div. This is called **event bubbling**.
2. Event Capturing: Consider this HTML
```html
<div>
    <button>Click me</button>
</div>
<script>
    document.querySelector('div').addEventListener('click',function(){
        console.log('div');
    },true)
    document.querySelector('button').addEventListener('click',function(){
        console.log('button');
    },true)
</script>
```
When I click on button, trigger happens for both div and button. This is called **event capturing**.

3. Event StopPropagation: Consider this HTML code
```html
<div>
    <button>Click me</button>
</div>
<script>
    document.querySelector('div').addEventListener('click',function(){
        console.log('div');
    })
    document.querySelector('button').addEventListener('click',function(event){
        event.stopPropagation();    
        console.log('button');
    })
</script>
```
When I click on button, trigger happens for button only. This is called **event stopPropagation**.

4. Event StopImmediatePropagation: Consider this HTML code
```html
<div>
    <button>Click me</button>
</div>
<script>
    document.querySelector('button').addEventListener('click',function(event){
        event.stopImmediatePropagation();    
        console.log('button');
    })
    document.querySelector('button').addEventListener('click',function(event){
        console.log('button 1');
    })
</script>
```
When I click on button, trigger happens for button only and stops there. This is called **event stopImmediatePropagation**.


**Question 13:** Explain pass by value and pass by reference in javaScript.

**Answer:** In javascript primitive data types are passed by value, while user defined ones like objects are passed in reference

For example

```javascript
function f1(x){
    x = 20
}
function f2(x){
    x.x = 20
}
function f3(x){
    x[2] = 10;
}

var a = {
    x : 10,
    y : 10
};
var b = 10;
var c = new Array(1,2,3);
f1(b);
f2(a);
f3(c);
console.log(a);
console.log(b);
console.log(c);
/*
Output:
{x : 20, y : 10} By reference
10 By value
[1,2,10] By Reference
*/
```
 
**Question 14:** What is parseint?

**Answer:** ParseInt converts string to integer
- Prototype: `parseInt(str,base)`
 
 **Question 15:** Is JavaScript compiled or Interpreted?
 
 **Answer:** JavaScript being a fairly mordern language falls in between the two steps hence confusion regarding compiled or Interpreted.
Lets consider the flow of a program:
1. Source code is transpiled (Babel) and packaged (Webpack).
2. JS engine(V8 in chrome, SpiderMnokey in firefox, JavaScriptCore in Safari, Chakra in Internet Explorer) converts the packaged code to Abstract Syntax Tree(AST).
3. JS engine then converts AST to "Kind of byte code" which is used by JIT compiler
4. JS Virtual Machine executes the program.

**Note:** The reason some times compiling JS doesn't give error in unused functions is due to the concept of lazy loading, i.e. engine (especially V8 uses this optimisation) partially parses functions before there first use and can miss some info error in them. These partailly parsed functions are parsed completely on first call and then is when any error missed during partial parsing will come up. (Read more about it [here](https://www.mattzeunert.com/2017/01/30/lazy-javascript-parsing-in-v8.html)).

**Question 15:** What is Reactor Pattern in Node.JS?

**Answer:** Reactor pattern is an idea of non-blocking I/O operations in Node.js. It provides a handler for each I/O operation and when an I/O request is generated, handler assosiated with it is submitted to demultiplexer. 

**Demultiplexer** is a notification interface that is used to handle concurrency in non-blocking I/O operations. The demultiplexer provides an **Event Queue** and thus when an handler is recieved by the demultiplexer it returns the control to the program. There is an **Event Loop** which iterates over the **Event Queue** triggering the handler(callback in case of JavaScript). When all items in **Event Queue** are processed and no pending operations are left, Node.js terminates the application.



More Node.js questions [here](https://www.edureka.co/blog/interview-questions/top-node-js-interview-questions-2016/).
