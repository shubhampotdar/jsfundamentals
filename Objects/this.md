# this keyword
A function's references the execution context for that call, determined entirely by how the function was called (the definition of the keyword doesn't matter at all in this case).

```javascript
var teacher = "kyle"; 
 
 function ask(question) {
   console.log(teacher,question);
 }

 function otherClass() {
   var teacher = "suzy";
   ask("why");
 }
 otherClass();

 //-------------

 function ask2(question) {
   console.log(this.teacher,question);
 }

 function otherClass2() {
   var myContext = {
     teacher: "Suzy"
   };
   ask2.call(myContext,"Why");
 }

 otherClass2(); 

/* Console Output:
kyle why
Suzy why
*/
```

## Implicit binding

```javascript
var teacher = "abc";
var workshop = {
  teacher: "Shu",
  ask(question) {
    console.log(this.teacher,question);
  },
};

workshop.ask("Implicit binding");

//Shu Implicit binding
```

