# Modules
Modules encapsulate data and behavior (methods) together. The state (data) of a module is held by its methods via closure.
</br></br>
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
</br></br>

### Module Factory

```javascript
//Module Factory 
function WorkshopModule(teacher) {
  var publicAPI = { ask, };
  return publicAPI;

  //******* 
  function ask(question) {
    console.log(teacher,question);
  }
};

var ws = WorkshopModule("Shu");
ws.ask("Module?"); // Shu Module?
```
</br></br>
### ES6 module pattern

#### workshop.mjs
```javascript
var teacher = "Shu";

export default function ask(question) {
  console.log(teacher,question);
};
```

#### Importing a module
* Named import syntax:
```javascript
import ask from "workshop.mjs";

ask("Default import");
```
* Namespace import syntax:
```javascript
import * as workshop from "workshop.mjs";

workshop.ask("Namespace import");
```



 
