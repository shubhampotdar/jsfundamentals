# Modules
Modules encapsulate data and behavior (methods) together. The state (data) of a module is held by its methods via closure.
</br></br>
### Classic/Revealing Module Pattern
Javascript does not have the typical 'private' and 'public' specifiers. However, you can achieve the same effect through the clever application of Javascript's function-level scoping. The Revealing Module pattern is a design pattern for Javascript applications that elegantly solves this problem. The central principle of the Revealing Module pattern is that all functionality and variables should be hidden unless deliberately exposed. The best way to avoid exposing your top-level function to the global scope is to wrap everything in an IFFE. 
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



 
