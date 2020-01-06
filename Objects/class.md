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
</br>

#### super keyword
The super keyword can be used to perform relative polymorphism.
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
   ask(msg) {
     super.ask(msg.toUpperCase());
   }
 }

 var aa =new AnotherWorkshop("kyle");
 aa.ask("what");
 // kyle WHAT 
 ```
 </br></br>
 
 ### Still dynamic this
 
 ```javascript
 class Workshop {
  constructor(teacher) {
    this.teacher = teacher;
  }
    ask(question) {
        console.log(this.teacher, question);
    }
}


var aa = new Workshop("shu");

setTimeout(aa.ask,100,"still losing this");
// undefined still losing this
```
</br>

Fixing the above problem:
```javascript
class Workshop {
  constructor(teacher) {
    this.teacher = teacher;
    this.ask = question => console.log(this.teacher,question);
  }
}


var aa = new Workshop("shu");

setTimeout(aa.ask,100,"this fixed");
// shu this fixed
```

### Other resources:
* [Static methods](https://javascript.info/static-properties-methods)
