---
creation date: 2021-05-01 13:13
modification date: Saturday 1st May 2021 13:13:29
tags: ["#webdev", "#dev"]
author: Jimmy Briggs
---

# Javascript

- *getElementById*

```HTML
<html>
<body>

<h2>JavaScript in Body</h2>
<p id="demo"></p> //we can use class selctor also 
<script>
document.getElementById("demo").innerHTML = "My First JavaScript"; 
//we can use onClick() funcion also 
</script>

</body>
</html>
```

**Display properties in javascript** JavaScript can "display" data in different ways:

- Writing into an HTML element, using innerHTML.
- Writing into the HTML output using document.write().
- Writing into an alert box, using window.alert().
- Writing into the browser console, using console.log().
- we can write this code in <script> tag or in plain js code.
- A JavaScript program is a list of programming statements.
- Semicolons separate JavaScript statements.
- Add a semicolon at the end of each executable statement.
- when we write multiple variable declarations/statements in one line  then it is allowed in js but we have to separate that by using semi  colons `a=3; b=2; c=a+b;`
- javascript ignores white spaces but we can write like this `var person = "phile" `
- JavaScript statements can be grouped together in code blocks, inside curly brackets {...}.
- JavaScript keywords are reserved words. Reserved words cannot be used as names for variables.
- JavaScript as two values Variable values are called Variables.
- Fixed values are called Literals like strings in ''/"" or simple value assigned.
- assignment is operator is = and also JavaScript is Case Sensitive means Var VAR is not considered as a var.
- hyphens are not allowed in javascript those are reserved for  substractions Underscore,lower camelCase and upper CamelCase type  variables are allowed in javascript.
- comments in javascript are like this // hello i am revising javascript
- const keyword to define a variable that cannot be reassigned and let keyword to define a variable with restricted scope.and var(whole  function scope) is global scoped and can be reasigned by values // const and let only exist in the blocks they are defined in..
- if we put numbers in string like `var yup="15"` so that will be treated as string because of quotes.
- After the declaration, the variable has no value (technically it has the value of undefined).
- we can declare many variables in one statement by separating comas or else semi;.
- for concatinating stuff we can use "je"+"fe"=jefe;a and starting  with dollars also are valid variable declarations and also we can start  with _hello.

**JavaScript assignment operators**

- examples = x=y
- x += y used as a x=x+y same for x=x-y/x=x*y/%=/* *=
- typeof Returns the type of a variable
- instanceof Returns true if an object is an instance of an object type
- Multiplication (*) and division (/) have higher precedence than addition (+) and subtraction (-).and important bracket **()** has a first precedance
- Example var x = "Volvo" + 16 + 4; if the operand is string then other will be treated as a string ans=Volvo164
- JavaScript has dynamic types. This means that the same variable can be used to hold different data types

```HTML
 var x;           // Now x is undefined
x = 5;           // Now x is a Number
x = "John";      // Now x is a String 
```

- Booleans can only have two values: true or false.
- typeof "" return datatype of the respective
- typeof {name:'John', age:34}  returns //object

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Functions</h2>

<p id="demo"></p>

<script>
function myFunction(p1, p2) {
  return p1 * p2;
}
document.getElementById("demo").innerHTML = myFunction(4, 3);
</script>

</body>
</html>
```

- The code inside the function will execute when "something" invokes (calls) the function:
- When an event occurs (when a user clicks a button)
- When it is invoked (called) from JavaScript code
- Automatically (self invoked)
- farebnhit to celcious   return (5/9) * (f-32);
- Variables declared within a JavaScript function with var, become  LOCAL to the function outside the function var will be undefined .

**Obejcts**

- A car(is a object) has properties like weight and color, and methods like start and stop:

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Objects</h2>

<p id="demo"></p>

<script>
// Create an object:
var car = {type:"Fiat", model:"500", color:"white"}; //this how obejcts created in javascript

// Display some data from the object:
document.getElementById("demo").innerHTML = "The car type is " + car.type;
</script>

</body>
</html>
```

- how we can write javascript objects in different types🔽

```HTML
var person = {
 firstName: "John",
 lastName: "Doe",
 age: 50,
 eyeColor: "blue"
};
```

- we can access values in objects by using **.** objectName.propertyName/ person["lastName"]; .
- In a function definition, this refers to the "owner" of the function in the aboive person is the owner of the function.
- In other words, this.firstName means the firstName property of this object.
- Accessing Object Methods

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Objects</h2>

<p>An object method is a function definition, stored as a property value.</p>

<p id="demo"></p>

<script>
// Create an object:
var person = {
  firstName: "John",
  lastName : "Doe",
  id     : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
// Display data from the object:
document.getElementById("demo").innerHTML = person.fullName();
</script>

</body>
</html>
```

- new keyword is used to create object. **JavaScript Events**
- HTML events are "things" that happen to HTML elements.
- An HTML input field was changed
- An HTML button was clicked

```HTML
<!DOCTYPE html>
<html>
<body>

<button onclick="document.getElementById('demo').innerHTML=Date()">The time is?</button>

<p id="demo"></p>

</body>
</html>
```

**JavaScript Event Types**

- onchange =An HTML element has been changed
- onclick = The user clicks an HTML element
- onmouseover = The user moves the mouse over an HTML element
- onmouseout/onkeydown/onload **String Methods in JavaScript**
- var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
- var sln = txt.length;
- But strings can also be defined as objects with the keyword new:
- var firstName = new String("John");

```HTML
var x = "John";             
var y = new String("John");
```

- When using the == operator, equal strings are equal:
- When using the === operator, equal strings are not equal, because the === operator expects equality in both type and value.
- and objects  cannot be compared if we compared then output is definitely `false`
- example escape character `"we are the \"Vikings\""`.

**Strings**

- var ex="krishna";
- console.log(ex.length);
- var wer="krishna kakade"
- var opps=wer.indexOf("kakade")// also we can lastIndexOf()
- console.log(opps);
- var pos = str.indexOf("locate", 15); //The indexOf() method accepts a second parameter as the starting position for the search
- var pos = str.lastIndexOf("locate", 15); //astIndexOf() method  searches backwards, so position 15 means start the search at position  15, and search to the beginning 7 ans
- var pos=str.search("locate"); //returns the position of the first occurrence of a specified text in a string:

**String Methods** Code example from w3schools

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript String Methods</h2>

<p>The slice() method extract a part of a string
and returns the extracted parts in a new string:</p>

<p id="demo"></p>

<script>
var str = "Apple, Banana, Kiwi";
var res = str.slice(7,13);
document.getElementById("demo").innerHTML = res; //returns Banana
</script>

</body>
</html>
```

- var res = str.slice(7); //The slice() method extract a part of a string and returns the extracted parts in a new string.
- var res = str.substr(7);//The substr() method extract a part of a  string and returns the extracted parts in a new string this returns  Banana,kiwi if i put(6)there then that will return `,Banana, kiwi`. and If the first parameter is negative, the position counts from the end of the string.

**String replace**

- str = "Please visit Microsoft and Microsoft!";
- var n = str.replace("Microsoft", "W3Schools");
- var n = str.replace(/Microsoft/g, "W3Schools"); //globally match with the help of //g regular expressions
- var text2 = text1.toUpperCase();  // text2 is text1 converted to upper or toLowerCase()
- var text3 = text1.concat(" ",text2);  //used for combining the two strings
- var str = "       Hello World!        ";//The trim() method removes whitespace from both sides of a string:
- alert(str.trim());

**More string methods**

- let str = "5";
- str = str.padStart(4,0); // result is 0005
- let str = "5";
- str = str.padEnd(4,0); // result is 5000
- var str = "HELLO WORLD";
- str.charAt(0); //returns H
- var str = "HELLO WORLD"; //returns 72
- str.charCodeAt(0); //if we use str[0] then also return H

```HTML
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
var str = "Hello";
var arr = str.split("");
var text = "";
var i;
for (i = 0; i < arr.length; i++) {
  text += arr[i] + "<br>"
}
document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

- var str="hey" // var strs=str.split(""); // console.log(strs)
- do not initialize objects with `new` it slows down the execution
- do not compare the objects.
- toString() method converts number to the string
- var x = 9.656; x.toExponential(2);     // returns 9.66e+0
- Number(new Date("2017-09-30"));    // returns 1506729600000 Number() can also convert a date to a number:
- parseInt("10.33");      // returns 10 returns whole number // returns 10
- var x = Number.MAX_VALUE;  return largest number/ MIN_VALUE/ **JavaScript arrays**
- var car1 = "Saab"; var cars = ["Saab", "Volvo", "BMW"]; cars[0] = "Opel"; we can assign values to the array using indexes
- var cars =["figo","vista"] var y = cars.sort();   sorts the array  [fruits.length - 1]; for pushing/adding new elelment to the array we can use cars.push("cybertruck") and also we can do .pop() for removing  element from the given array.
- In JavaScript, arrays use numbered indexes. In JavaScript, objects use named indexes.
- for recongnising the array we can use  typeof cars;
- The shift() method removes the first element of an array (and  "shifts" all other elements to the left): and unshift is used to add new element to the array and .splice() is used to remove element from the  array without leaving holes some unwanted memory etc.

```HTML
<script>
var points = [40, 100, 1, 5, 25, 10];
document.getElementById("demo").innerHTML = points;  

function myFunction() {
  points.sort(function(a, b){return a - b});
  document.getElementById("demo").innerHTML = points;
}
</script>
```

- above code example is used for the returning number in asending  order and for returning element in desending order we can do b-a.//If  the result is negative a is sorted before b.If the result is positive b  is sorted before a.
- The map() method creates a new array by performing a function on  each array element.reduce() method reduces the array into single value.
- cars.indexOf("Volvo") return index of that array element
- var d = new Date(); returns the date // for getting full year we can use .getFullYear()
- there are to many methods for for .Math() function like Math.ceil() // return round up numbernearest number // Math.round()
- variablename = (condition) ? value1:value2  ternary operator

**Conditionals in javascript**

- if else simple logic
- else when we are going to return the result if code doesn't work according to us
- else if for multiple conditions checking
- in switch case we can return result according to the different cases

```HTML
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
} 
```

- loops
- for (statement 1; statement 2; statement 3) { // code block to be executed }
- for - loops through a block of code a number of times
- for/in - loops through the properties of an object
- for/of - loops through the values of an iterable object
- while - loops through a block of code while a specified condition is true
- do/while - also loops through a block of code while a specified condition is true **Syntax**
- while (condition) { // code block to be executed }
- do { // code block to be executed } while (condition);
- The break statement "jumps out" of a loop.
- The continue statement "jumps over" one iteration in the loop.
- bit wise operators are `and ,or ,not~,xor/^,shifts`

**JavaScript Regular Expressions**

- A regular expression is a sequence of characters that forms a search pattern.
- Regular expressions can be used to perform all types of text search and text replace operations.
- var str = "Visit W3Schools";var n = str.search(/w3schools/i); //i denotes case sensitive and g for global matching
- test is the javascript regular expression object **Try and catch**

```HTML
try {
  Block of code to try
}
catch(err) {
  Block of code to handle errors
}
finally {
  Block of code to be executed regardless of the try / catch result
} 

var num = 1;
try {
  num.toUpperCase();   // You cannot convert a number to upper case
}
catch(err) {
  document.getElementById("demo").innerHTML = err.name;
}
```

- variables declared inside the function those are local variables to  the function and those are declared outside the function are global  variables.

**JavaScript hoisting**

- Variables defined with let and const are hoisted to the top of the block, but not initialized.
- In JavaScript, a variable can be declared after it has been used.In  other words; a variable can be used before it has been  declared.Variables defined with let and const are hoisted to the top of  the block, but not initialized.Meaning: The block of code is aware of  the variable, but it cannot be used until it has been declared.Using a  let variable before it is declared will result in a ReferenceError.
- Declare Your Variables At the Top !
- Hoisting is (to many developers) an unknown or overlooked behavior of JavaScript.
- If a developer doesn't understand hoisting, programs may contain bugs (errors).
- To avoid bugs, always declare all variables at the beginning of every scope.
- Since this is how JavaScript interprets the code, it is always a good rule.
- With `strict mode`, you can not, for example, use undeclared variables.
- because of strict mode we can write secure javascript if Declared at the beginning of a script, it has global scope (all code in the script  will execute in strict mode):and we didn't declared variables then that  will cause erros. **This keyword**
- The JavaScript this keyword refers to the object it belongs to. In a function, this refers to the global object.
- JavaScript strict mode does not allow default binding. So, when used in a function, in strict mode, this is undefined.
- **const** array can be changed.

**Arrow functions**

```HTML
simple functions
hello = function() {
  return "Hello World!";
}
arrow function
hello = () => {
  return "Hello World!";
  
  simple one with return default is return  hello = () => "Hello World!"; 
  
```

- **JavaScript class examples**

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Class</h2>

<p>How to use a JavaScript Class.</p>

<p id="demo"></p>

<script>
class Car {
constructor(name, year) {
  this.name = name;
  this.year = year;
}
}

myCar = new Car("Ford", 2014);
document.getElementById("demo").innerHTML =
myCar.name + " " + myCar.year;
</script>

</body>
</html>
```

- If your browser supports debugging, you can use console.log() to  display JavaScript values in the debugger window:and The debugger  keyword stops the execution of JavaScript, and calls (if available) the  debugging function.and debugger tools are devtools of any browser we can those things in console
- **JavaScript best practices **
- Global variables and functions can be overwritten by other scripts.  Use local variables instead, and learn how to use closures.end switches  with defaults.
- **JavaScript Performance**
- Reduce Activity in Loops:-

```HTML
var i;
for (i = 0; i < arr.length; i++) { //bad code
var i;
var l = arr.length;
for (i = 0; i < l; i++) { //better code
```

- **closures** It’s kind of like when a car is  manufactured (defined) it comes with a few functions like start,  accelerate, decelerate. These car functions get executed by the driver  every time they operate the car. Closures for these functions come  defined with the car itself and they close over variables they need to  operate.
- JavaScript has the 5 primitive datatypes
- string ,number,boolean, null, undefined.
- JavaScript Objects are Mutable Objects are mutable: They are  addressed by reference, not by value. Any changes to x will also change  person, because x and person are the same object.
- The delete keyword deletes a property from an object.

```HTML
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
delete person.age;   // or delete person["age"]; 
```

- Accessing Object Methods in JavaScript code

```HTML
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
var person = {
  firstName: "John",
  lastName : "Doe",
  id     : 5566,
};
person.name = function() {
  return this.firstName + " " + this.lastName;
};

document.getElementById("demo").innerHTML =
"My father is " + person.name(); 
</script>

</body>
</html>
```

- Object.values() converts an object to an array.

**JavaScript Object Accessors**

- // Display data from the object using a getter:

```HTML
var person = {
  firstName: "John",
  lastName : "Doe",
  language : "",
  set lang(lang) {
    this.language = lang;
  }
};

// Set an object property using a setter:
person.lang = "en";

// Display data from the object:
document.getElementById("demo").innerHTML = person.language;
```

- JavaScript Object Constructors

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Object Constructors</h2>

<p id="demo"></p>

<script>
// Constructor function for Person objects
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}

// Create a Person object
var myFather = new Person("John", "Doe", 50, "blue");

// Display age
document.getElementById("demo").innerHTML =
"My father is " + myFather.age + "."; 
</script>

</body>
</html>
```

- another way to use constructor

```HTML
class Polygon {
  constructor() {
    this.name = 'Polygon';
  }
}

const poly1 = new Polygon();

console.log(poly1.name);
// expected output: "Polygon"
```

- The JavaScript prototype property allows you to add new properties to object constructors and The JavaScript prototype property also allows  you to add new methods to objects constructors.Prototypes are the  mechanism by which JavaScript objects inherit features from one another. In this article, we explain how prototype chains work and look at how  the prototype property can be used to add methods to existing  constructors.
- call(), an object can use a method belonging to another object.
- **javascript closures** A closure is a function having access to the parent scope, even after the parent function has closed.
- **JavaScript Classes**
	
```HTML
  constructor() { ... }
}
```

**class inheritance**

```HTML
class Car {
  constructor(brand) {
    this.carname = brand;
  }
  present() {
    return 'I have a ' + this.carname;
  }
}

class Model extends Car {
  constructor(brand, mod) {
    super(brand);
    this.model = mod;
  }
  show() {
    return this.present() + ', it is a ' + this.model;
  }
}

let myCar = new Model("Ford", "Mustang");
document.getElementById("demo").innerHTML = myCar.show();
```

- The super() method refers to the parent class.By calling the super() method in the constructor method, we call the parent's constructor  method and gets access to the parent's properties and  methods.Inheritance is useful for code reusability: reuse properties and methods of an existing class when you create a new class.

**JavaScript Callbacks**

- "I will call back later!" A callback is a function passed as an  argument to another function This technique allows a function to call  another function A callback function can run after another function has  finished.
- A callback is a function passed as an argument to another function.
- Functions running in parallel with other functions are called asynchronous. A good example is JavaScript setTimeout()
- async makes a function return a Promise and await makes a function wait for a Promise
- .includes() method checks that number or something is in the array & according to that it returns true.
- global scoped variables are declared on the top function in javascript
- anonymous function is function without name

```HTML
// This is how we write normal or declaration function
// Let us change this declaration function to an arrow function
function square(n) {
  return n * n
}

console.log(square(2)) // 4

const square = (n) => {
  return n * n
}

console.log(square(2)) // -> 4

// if we have only one line in the code block, it can be written as follows, explicit return
const square = (n) => n * n // -> 4
```

- ... spread operator can be use to copy the elements of the array to another array and also we can copy objects also.

- **JavaScript coding questions** ``  var A = new Date('October 15, 1996 05:35:32');

  // Day of the week from above Date Object is // being extracted using getDay() var Day = A.getDay(); console.log(Day) ``

- Print this page `function print_current_page() { window.print(); }`

***
Links: 
Source:

