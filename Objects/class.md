# class keyword
A class is the syntactic sugar layered upon the prototype model.

```javascript
class Workshop {
  constructor(teacher) {
    this.teacher = teacher;
  }
  ask(question) {
    console.log(this.teacher,question);
  }
}

var aa = new Workshop("kyle");
var bb = new Workshop("sss");

aa.ask("what");
// kyle what
bb.ask("why");
// sss why
```
