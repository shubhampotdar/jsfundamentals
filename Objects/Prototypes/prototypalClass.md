# Prototypal Class

```javascript
function Workshop(teacher) {
  this.teacher = teacher;
}

Workshop.prototype.ask = function(question){
  console.log(this.teacher,question);
}

var aa = new Workshop("shu");
var bb = new Workshop("kyle");

aa.ask("what");
// shu what

bb.ask("why");
// kyle why
```
