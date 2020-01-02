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

Here is another example to understand closures better:
```javascript
function adder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = adder(5);

console.log(add5(4)); // 9

var add6 = adder(6);

console.log(add6(7)); // 13

console.log(add5(21)); // 26
```
</br></br>
### Example of closure with for loop

```javascript
for(var i=1;i<=3;i++)
{
  setTimeout(function(){
    console.log(i);
  },0);
}
// 4
// 4
// 4
```
Here is a scoped based solution to the above problem:  a let(block-scoped) j is assigned to i. Then:
``` javascript
for(var i=1;i<=3;i++)
{
  let j=i;
  setTimeout(function(){
    console.log(j);
  },0);
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
  },0);
}
// 1
// 2
// 3
```
The closure based  approach to solving this problem is through an IIFE :
```javascript
for(var i=1;i<=3;i++) {
  (function(i){
    setTimeout(function(){
    console.log(i);
  },0);
  })(i);
}
// 1
// 2
// 3
```


