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

So in the arrow function (callback of setTimeout), 
there is no this defined no matter how it ges invoked. 
So we lexically go up one level of scope which is the "ask"
function (enclosing scope). The this keyword inside of ask 
is determined by its call-site i.e. workshop.ask() . And then when 
that callback is later invoked it is essentially closed over 
that parent scope that had a this keyword pointing at the workshop object. So it is not a hard bound function.
