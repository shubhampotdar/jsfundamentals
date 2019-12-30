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

