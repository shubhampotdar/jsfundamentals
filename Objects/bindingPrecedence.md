# Binding Precedence



```javascript
var workshop = {
  teacher:"kyle",
  ask: function ask(question) {
    console.log(this.teacher,question);
  },
};

new(workshop.ask.bind(workshop))("what");
// undefined what
```
