# Binding Precedence
new > call()/apply() > function called on a context object(eg. workshop.ask()) > default:global object (except strict mode)
</br>
(Note: bind() effectively uses apply())



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
