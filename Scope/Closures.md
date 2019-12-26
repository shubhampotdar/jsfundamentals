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
```
</br>

Closure doesnt store a snapshot of closed variables but stores a linkage. so when a closed variable is accessed, it returns the value that variable holds at that particular time.
```javascript
var v1 = "aaa";
var clf = function() {
  console.log(v1);
};
v1 = "bbb";
clf(); //bbb
```
</br>

### Example of closure with for loop

```javascript
for(var i=1;i<=3;i++)
{
  setTimeout(function(){
    console.log(i);
  },1000);
}
// 4
// 4
// 4
```

But if in every iteration, a let(block-scoped) j is assigned to i. Then:
``` javascript
for(var i=1;i<=3;i++)
{
  let j=i;
  setTimeout(function(){
    console.log(j);
  },1000);
}
// 1
// 2
// 3
```
In ES6, this was changed to:
```javascript
for(let i=1;i<=3;i++)
{
  setTimeout(function(){
    console.log(i);
  },1000);
}
// 1
// 2
// 3
```

