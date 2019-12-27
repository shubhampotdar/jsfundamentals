# new Keyword
The following happens when the new keyword is used to invoke a function:
1. Create a brand new empty object
2. Link that object to another object.*
3. Call function with this set to the new object.
4. If function does not return an object,assume return of this.

Constructor call:
```javascript
function ask(question) {
  console.log(this.teacher,question);
}

var newEmptyObject = new ask("howw");
// undefined "howw"
```
