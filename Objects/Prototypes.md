## Prototypal Class

The following snippet resembles a class as implemented using prototypes.
```javascript
function Workshop(teacher) {
  this.teacher = teacher;
}

Workshop.prototype.ask = function(question){
  console.log(this.teacher,question);
}

var deepJS = new Workshop("shu");
var reactJS = new Workshop("kyle");

deepJS.ask("what");
//shu what

reactJS.ask("why");
// kyle why
```
The name of a constructor function usually starts with an uppercase letter to draw the distinction between regular functions. 
Here the __Workshop()__ method is the function constructor. All the data members are declared here. Every function has an object associated with it called its prototype (Function.prototype). We can add methods to this prototype. In the above snippet, the __ask()__ method is added to the prototype of the Workshop constructor function. This constructor function can be used to instantiate objects. </br>
</br>
The __ask()__ function could be added to the constructor function directly instead of adding it to its prototype, but that would lead to the creation of a new ask method for every object which is unnecessary waste of memory.
</br> </br>
To understand the benefit of using prototypes refer the following article:
[A Beginner's Guide to JavaScript's prototype](https://tylermcginnis.com/beginners-guide-to-javascript-prototype/)
</br>

The prototype chain for the above snippet is shown below:
</br> (Circles are functions and squares are objects.)

</br></br>

<img src="./prototypeChain.png">

</br>
Let us understand how this chain is built by the JS engine.
</br></br>
Firstly, even before the execution starts, i.e. at line zero, JS creates the __Object__ function which has an object linked to it which can be referenced using the __.prototype__ property (`Object.prototype`) which in-turn has a __.constructor__ property which references back to __Object__. 
</br></br>
When the __Workshop__ constructor function is declared, an empty object is created which can be referenced via
```Workshop.prototype```
. This object is internally linked to the prototype of __Object__. Line 5 adds the ask method to the prototype of the 
```Workshop```
constructor function.
</br></br>
The objects (
```deepJS```
and 
```reactJS```
) are instantiated via the __new__ keyword which:

* Creates a brand new empty object

* Links this object to the prototype of is constructor function

* Call the constructor function with this set to the new object

* If the function does not return an object, assume return of this.

So when the `deepJS.ask(parameter)` line runs, JS looks for the `ask` method in the `deepJS` object. It doesn’t find it there so it moves one level up the prototype chain to the prototype of the __Workshop__ where it finds the __ask__ method.


At the top level of the prototype chain is hierarchy is the __Object__ object. It's own prototype points to null as there is nothing above it.

```javascript
console.log(Object.prototype);
//null
```

</br></br>

## Dunder proto
Dunder proto i.e. Object.__proto__  is used to move one object up the prototype chain. Dunder proto is basically a getter function in Object.prototype
```javascript
console.log(
  deepJS.constructor === Workshop
); // true
console.log(
  deepJS.__proto__ === Workshop.prototype
); // (dunder proto) true

console.log(
  Object.getPrototypeOf(deepJS) === Workshop.prototype
); // true
```

</br></br>

## Shadowing of prototypes
Here, we are adding a ask function to the deepJS object when there already is an ask function in the prototype of Workshop.
The following code would lead to an infinite recursion as it keeps calling the ask function in the deepJS object.

```javascript
function Workshop(teacher) {
  this.teacher = teacher;
}

Workshop.prototype.ask = function(question){
  console.log(this.teacher,question);
}

var deepJS = new Workshop("shu");
deepJS.ask = function(question) {
  this.ask(question);
}
deepJS.ask("Infinite recursion");
```
</br>
The following fix can allow polymorphism to be performed:

```javascript
function Workshop(teacher) {
  this.teacher = teacher;
}

Workshop.prototype.ask = function(question){
  console.log(this.teacher,question);
}

var deepJS = new Workshop("shu");
deepJS.ask = function(question) {
  this.__proto__.ask.call(this,question);
}
deepJS.ask("why");
```

</br></br>

## Prototypal inheritance
Inheritance can be performed in prototypes by liking their objects together.
```javascript
function Workshop(teacher) {
  this.teacher = teacher;
}

Workshop.prototype.ask = function(question){
  console.log(this.teacher,question);
};

function AnotherWorkshop(teacher) {
  Workshop.call(this,teacher);
}

AnotherWorkshop.prototype = Object.create(Workshop.prototype);

AnotherWorkshop.prototype.speakUp = function(msg) {
  this.ask(msg.toUpperCase());
};

var aa = new AnotherWorkshop("kyle");
aa.speakUp("inheritance");
// kyle INHERITANCE
```


