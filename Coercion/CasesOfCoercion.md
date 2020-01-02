# Cases Of Coercion
* Plus operation with a string returns string.

```javascript
var a;
a= 1;
console.log(a); // 1
console.log(typeof a); // number
a = 1+"";
console.log(a); // "1"
console.log(typeof a); // string
```
</br>

* Identifiers are coerced to string in back ticks in console.log (toString() called for the non-string values)
```javascript
console.log(`Hello ${a}`); // type coercion taking place here (toString() called for the non-string values)
```

var numStringVar = "121";
function plusOne(num) {
	return num+1;
}
console.log(plusOne(numStringVar)); // returns "1211". i.e. performs string concatenation
console.log(plusOne(+numStringVar)); //returns 122 (the Unary Plus operator performs the ToNumber() operation)
function minusOne(num) {
	return num-1;					// automatically coerces to number as '-' operator is used
}  
console.log(minusOne(numStringVar)); // 120

var emptyStringVar = "";
var whiteSpaceVar = " ";
if(emptyStringVar)        // toBoolean called. "" is falsy so condition fails
	console.log("hello");
if(whiteSpaceVar)         // " " is whitespace which is not a falsy value so condition passes 
	console.log("bye");

console.log(stringVar.length); // string is a primitive type but yet has methods as it is implicitly coerced to its object counterpart (Boxing)

```
