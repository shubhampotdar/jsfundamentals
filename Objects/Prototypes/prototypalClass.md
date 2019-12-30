# Prototypal Class

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
