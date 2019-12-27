# Default binding
As no object can be found in the below snippet, the fallback in non-strict mode is to default to the global.
In strict mode if a function is invoked with no other this bindings, the default behaviour is to leave "this" undefined. Hence, we get a TypeError in the askAgain function as it cannot read property teacher of undefined.
```javascript
var teacher = "kyle";

function ask(question) {
  console.log(this.teacher,question);
}

function askAgain(question) {
  "use strict";
  console.log(this.teacher,question);
}

ask("who");
// kyle who
askAgain("why");
// TypeError
```
