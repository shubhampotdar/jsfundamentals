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
</br>
### Resolving this in arrow functions
```javascript
var workshop = {
  teacher: "kyle",
  ask: (question) => {
      console.log(this.teacher,question);
  },
};

workshop.ask("why");
workshop.ask.call(workshop,"whyyyy");

// undefined why
// undefined whyyy
```
In this example, the this keyword is inside an arrow function. So it behaves like a normal variable and lexically searches for its context. There are only two scopes in the above example - the arrow function and the global scope (objects are not scopes). So it lexcially falls back to the global scope in search of the this keyword and therefore returns undefined.
