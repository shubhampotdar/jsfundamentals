# Default binding

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
