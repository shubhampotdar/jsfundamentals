# Prototypal Class

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
</br>

The prototype chain for the above snippet is shown below:

</br></br>

<img src="./prototypeChain.png">

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

