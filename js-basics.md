<h1>JAVASCRIPT CONCEPTS</h1>



[TOC]

------

## JAVASCRIPT BASICS

### THE GLOBAL OBJECT

In JS all code that is not inside any function is associated to the Global object.
In the browser, the global object is the window object.
When we create a variable lastName -> lastName === windows.lastName

### THE STATE VARIABLE

A state variable tells us the condition of a system. We need a state variable when we need to remember the state of something.
For ex. : the variable gamePlaying = true if a game is playing or gamePlaying = false if a game is not playing.

### THE THIS VARIABLE

- In a regular function call: the ***this*** keyword points at the Global object (the window object in the browser)
- In a method (=a function inside an object) call: the ***this*** object points to the object that is calling the method.
- The this keyword is not assigning a value until a function where it is defined is actually called.

```javascript
var john = {
    firstName: 'John',
    lastName: 'Smith',
    birthYear: 1992,
    isMarried: false,
    calcAge: function() {
        this.age = 2018 - this.birthYear;
    }
};
```

### IF / ELSE STATEMENTS

```javascript
if (civilStatus === 'married') {
    console.log(firstName + ' is married!');
} else {
    console.log(firstName + ' will hopefully marry soon :)');
}
```

### BOLEAN LOGIC

```javascript
if (age < 13) {
    console.log(firstName + ' is a boy.');
} else if (age >= 13 && age < 20) {
    console.log(firstName + ' is a teenager.');
} else if (age >= 20 && age < 30) {
    console.log(firstName + ' is a young man.');
} else {
    console.log(firstName + ' is a man.');
}
```

### THE TERNARY OPERATOR

```javascript
age >= 18 ? console.log(firstName + ' drinks beer.') : console.log(firstName + ' drinks juice.');
```

### THE SWITCH STATEMENT

```javascript
var job = 'instructor';
switch (job) {
    case 'teacher':
    case 'instructor':
        console.log(firstName + ' teaches kids how to code.');
        break;
    case 'driver':
        console.log(firstName + ' drives an uber in Lisbon.');
        break;
    case 'designer':
        console.log(firstName + ' designs beautiful websites.');
        break;
    default:
        console.log(firstName + ' does something else.');
}
```

### AND - OR - NOT

```javascript
&& - || - !
```

### TRUTHY AND FALSY VALUES

- Falsy values: undefined, null, 0, '', NaN
- Truthy values: NOT falsy values

### FUNCTION

* A function is an instance of the Object type.
* A function behave like any other object.
* We can store functions in a variable.
* We can pass a function as an argument to another function (this function is called a call-back function).
* We can return a function from a function
=> They are First-class functions

**Example of first-class functions called as argument:**

```javascript
var years = [1990, 1965, 1937, 2005, 1998];

function arrayCalcl(array, fn) {
	var arrRes = [];
	for (var i = 0; i < array.length; i++) {
		arrRes.push(fn(array[i]));
	}
	return arrRes;
}

function calculateAge(el) {
	return 2020 - el;
}

function isFullAge(el) {
	return el >= 18;
}

function maxHeartRate(el) {
	if (el >= 18 && el <= 81) {
		return Math.round(206.9 - 0.67 * el);
	} else {
		return -1;
	}
}

var ages = arrayCalcl(years, calculateAge);
console.log(ages);

var fullAges = arrayCalcl(ages, isFullAge);
console.log(fullAges);

var rates = arrayCalcl(ages, maxHeartRate);
console.log(rates);
```

**Example of first-class function return from another function:**

```javascript
function interviewQuestion(job) {
	if (job === 'designer') {
		return function (name) {
			console.log(name + ', can you please explain what UX design is?');
		};
	} else if (job === 'teacher') {
		return function (name) {
			console.log(name + ', What subject de you teach?');
		};
	} else {
		return function (name) {
			console.log('Hello ' + name + ', what do you do?');
		};
	}
}

var teacherQuestion = interviewQuestion('teacher');
var designerQuestion = interviewQuestion('designer');

teacherQuestion('John');
designerQuestion('John');
// or we can write it shortly
interviewQuestion('teacher')('Mark');
```

### FUNCTION EXPRESSION

A function that return something.

```javascript
calcAge: function(birthYear) {
    return 2020 - birthYear;
}
```

### FUNCTION STATEMENT

A function that not return something.

```javascript
function showMessage() {
  alert( 'Hello everyone!' );
}
```

### ARRAY

Like Python tuple: a list that can contains different types of variables but with a specific order.

```javascript
var myArray = [3, 8, 'nico', false]
```

### OBJECT

Like an array but without any order, we can put everything inside, functions also. An object contains properties and each property as is own key. Properties are variables attached to an object.

```javascript
Properties are only variables attached to objects.
var myObject = {
    firstName: 'John', //firstName is a key
    lastName: 'Smith',
    birthYear: 1990,
    family:['Jane', 'Mark', 'Bob', 'Marie'],
    job: 'teacher',
    isMarried: false
};
```

To call or mutate a key we use:

```javascript
myObject.firstName or myObject['firstName']
```

### METHOD 

A method is a function inside an object. Only objects have methods (so arrays are objects...) 

```javascript
var myObject = {
    firstName: 'John',
    lastName: 'Smith',
    birthYear: 1990,
    family:['Jane', 'Mark', 'Bob', 'Marie'],
    job: 'teacher',
    isMarried: false,
    calcAge: function() {
        return 2020 - this.birthYear; //this signifie la clé birthYear de cet objet (l'objet ou se trouve la méthode calcAge)
    }
};
```

To call a method : 

```javascript
myObject.calcAge();
```

### LOOPS AND ITERATION

**The FOR loop**

```javascript
for (var i = 0; i < 10; i++) {
    console.log(i);
}

var john = ['John', 'Smith', 1990, 'designer'];
for (var i = 0; i < john.length; i++) {
    console.log(john[i]);
}
```

**The WHILE loop**

```javascript
var i = 0;
while (i < john.length) {
    console.log(john[i]);
    i++;
```

**CONTINUE and BREAK statement**

```javascript
var john = ['John', 'Smith', 1990, 'designer'];
for (var i = 0; i < john.length; i++) {
    if (typeof john[i] !== 'string') continue;
    console.log(john[i]);
}

var john = ['John', 'Smith', 1990, 'designer'];
for (var i = 0; i < john.length; i++) {
    if (typeof john[i] !== 'string') break;
    console.log(john[i]);
}
```

**Looping backwards**

```javascript
var john = ['John', 'Smith', 1990, 'designer'];
for (var i = john.length-1; i >= 0; i--) {
    console.log(john[i]);
}
```

------

### THE DOM => DOCUMENT OBJECT MODEL

The DOM is a structured representation of an HTML document.
The DOM is used to connect webpages to scripts like JS.
For each HTML box (`<body>, <section>, <p>`...), there is an object in the DOM that we can access and interact with.
The HTML webpage content is stored in the DOM, which can be accessed and manipulated by the JavaScript.
JS and the DOM are really different.

### EVENTS

- Events are notifications that are sent to notify the code that something happened on the webpage.
  *Ex. clicking a button, resizing a window, scrolling down or pressing a key...*
- Event listeners are functions that perform an action based on a certain event. They wait for a specific event to happen.
  *Ex. opening a popup windows, showing animations...*

------



## JAVASCRIPT ADVANCED

### OBJECT-ORIENTED PROGRAMMING

- Objects interact one another through methods and properties.
- Objects are used to store data, to structure applications into modules and keeping code clean.

### CONSTRUCTORS AND INSTANCES

Constructor (or function constructor) = Python classes.

### INHERITANCE => PROTOTYPE AND PROTOTYPE CHAIN

It happens when one object is base on one another object. When one object can access one another object properties and method.
In JS, inheritance is made possible by the prototype property. Every object has a prototype property.
The prototype property of an object is where we put method and properties that we want other objects to inherit.
The constructor's prototype property is NOT the prototype of the constructor itself, it's the prototype of ALL instances that are created through it.
When a certain method (or property) is called, the search starts in the object itself, and if it cannot be found, the search moves on to the object's prototype. This continues until the method is found: this is called the prototype chain.

### FUNCTION CONSTRUCTOR TO CREATE NEW OBJECTS

Always starts with a capital letter.
Example:

```javascript
//We want to create the john object:
var John = {
    name: 'John',
    yearOfBirth: 1981,
    job: 'teacher'
};

//We implement a function constructor:
var Person = function(name, yearOfBirth, job) {
    this.name = name;
    this.yearOfBirth = yearOfBirth;
    this.job = job;
}

//And now we can instanciate as many object as we want calling the new operator:
var john = new Person('John', 1981, 'teacher'); // An instance of the Person object
var Jane = new Person('Jane', 1983, 'cook') // Also an instance of the Person object
var mark = new Person('Mark', 1978, 'designer'); // Also an instance of the Person object
```

Let's add some inheritance:

```javascript
Person.prototype.calcAge = function () {
	console.log(2020 - this.yearOfBirth);
};
```

We put this method in the prototype property of our function constructor -> This is inheritance, all the instances of this class will inherit this method.
It works also with properties, for example:

```javascript
Person.prototype.lastName = 'Smith';
```

### Object.create METHOD TO CREATE OBJECT

This method is used to create object with complex inheritance patterns.

Object.create method exemple:

```javascript
//We start by creating the prototype of our constructor

var personProto = {
	calcAge: function () {
		console.log(2020 - this.yearOfBirth);
	},
};

//Then we call the Object.create method to create new instances
//option 1:
var john = Object.create(personProto);

john.name = 'John';
john.yearOfBirth = 1981;
john.job = 'teacher';

//option 2:
var jane = Object.create(personProto, {
	name: { value: 'Jane' },
	yearOfBirth: { value: 1981 },
	job: { value: 'designer' },
});
```

*BUT the FUNCTION CONSTRUCTOR way to create objects is the most common one.*

### IMMEDIATLY INVOKED FUNTION EXPRESSIONS - IIFE

IIFE is usually used for data pricacy:

Example:

```javascript
//A simple function that print in the console if a random score is >= 5:
function game() {
	var score = Math.random() * 10;
	console.log(score >= 5);
}
game();


//An IIFE function that do the same thing:
(function () {
	var score = Math.random() * 10;
	console.log(score >= 5);
})();
```

### CLOSURES

An inner function has always access to the variables and parameters of its outer function, even after the outer function has returned.

Example:

```javascript
function retirement(retirementAge) { //OUTER FUNCTION
	var a = ' years left until retirement.';
	return function (yearOfBirth) { //INNER FUNCTION
		var age = 2020 - yearOfBirth;
		console.log(retirementAge - age + a);
	};
}

var retirementUS = retirement(66);
retirementUS(1990);
```

### CALL, APPLY AND BIND FUNCTIONS

Example:

Let's create a some objects:

```javascript
var john = {
	name: 'John',
	age: 26,
	job: 'teacher',
	presentation: function (style, timeOfDay) {
		if (style === 'formal') {
			console.log(
				'Good ' +
					timeOfDay +
					" ladies and gentlemen! I'm " +
					this.name +
					", I'm " +
					this.age +
					" years old and I'm a " +
					this.job +
					'.'
			);
		} else if (style === 'friendly') {
			console.log(
				"Hey guys! I'm " +
					this.name +
					", I'm " +
					this.age +
					" years old and I'm a " +
					this.job +
					'. Have a nice ' +
					timeOfDay +
					'.'
			);
		}
	},
};

john.presentation('formal', 'morning');

var emily = {
	name: 'Emily',
	age: 39,
	job: 'deigner',
};
```

- Hereafter is the CALL FUNCTION => This function allows us to set the THIS variable to an other object (in this case emily):

```javascript
john.presentation.call(emily, 'friendly', 'afternoon'); // We use john presentation method on emily object
```

- Hereafter is the APPLY FUNCTION => the only difference is that the 2d argument is an array (but it won't work here because our method doesn't expect an array as an argument)

```javascript
john.presentation.apply(emily, ['friendly', 'afternoon']);
```

- Hereafter is the BIND FUNCTION => this function allows us to set the THIS variable to another object. But the bind function doesn't execute the function so we can store the result function into a variable.

```javascript
var johnFriendly = john.presentation.bind(john, 'friendly');
johnFriendly('morning');
johnFriendly('night');
```

