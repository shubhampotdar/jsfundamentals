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

</br></br>
### Extending classes
```javascript
 class Workshop {
   constructor(teacher) {
     this.teacher = teacher;
   }
   ask(question) {
     console.log(this.teacher,question);
   }
 }

 class AnotherWorkshop extends Workshop {
   speakUp(msg) {
     this.ask(msg);
   }
 }

 var aa = new AnotherWorkshop("kyle");
 aa.speakUp("what");

//kyle what
```
