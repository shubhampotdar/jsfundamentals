# Modules
Modules encapsulate data and behavior (methods) together. The state (data) of a module is held by its methods via closure.

### Classic/Revealing Module Pattern
An IIFE is used so it is a singleton module.

```javascript
// Classic/Revealing module pattern
var workshop = (function Module(teacher) {
  var publicAPI = { ask };
  return publicAPI;
  // ***************

  function ask(question) {
    console.log(teacher, question);
  }
})("Shu");

workshop.ask("Helllooooo"); // Shu Helllooooo
```
