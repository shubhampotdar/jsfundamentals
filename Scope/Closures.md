# Closures
Closure is when a function remembers its lexical scope even when the function is executed outside that lexical scope.
```javascript
// closure example
function aabbcc(q) {
  setTimeout(function(){
    console.log(q);
  },1000);
}
aabbcc("Hello"); //Hello

function abc(val) {
  return function holdFunc() {
    console.log(val);
  };
}
var retFunc = abc(2);
retFunc(); //2
// closure example
function aabbcc(q) {
  setTimeout(function(){
    console.log(q);
  },1000);
}
aabbcc("Hello"); //Hello

function abc(val) {
  return function holdFunc() {
    console.log(val);
  };
}
var retFunc = abc(2);
retFunc(); //2
```
