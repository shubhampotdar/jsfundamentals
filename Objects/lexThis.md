# Arrow functions and Lexical this
An arrow function does not define a this keyword at all. So if a this keyword is put inside an arrow function, it is going to behave like any other variable (lexically resolve to an enclosing scope that does define a this keyword).

```javascript
var workshop = {
  teacher: "kyle",
  ask(question) {
      setTimeout(() => {
        console.log(this.teacher,question);
      },100);
  },
};

workshop.ask("lexical this");
// kyle lexical this
```
