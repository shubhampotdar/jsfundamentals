# NaN 
__NaN__ should be considered as an invalid number rather than Not a Number. This can be seen by performing the __typeof__ operation on NaN which returns "number".

</br>

## isNaN()
Determines whether the passed value is NaN. It coerces the value to number before checking(Number.is(NaN()) performs no form of coercion and specifically tells if it is NaN).
```javascript
var numberVar = 2;
console.log ("isNaN for number -  " + isNaN(numberVar)); // returns false

var stringVar = "Hello";
console.log("isNAN for string - " + isNaN(stringVar)); // returns true
```
</br></br>

Strings when coerced to a number return __NaN__.
```javascript
var stringVar = "Hello";
console.log(Number(stringVar)); // NaN 
```
Except,
```javascript
console.log(Number(" ")); // returns 0
console.log(isNaN(" ")); // returns false
```
This is because isNaN() first coerces it to a number and so a empty string first changes to zero which is a number
Refer: <https://stackoverflow.com/questions/825402/why-does-isnan-string-with-spaces-equal-false>

Also except when string is the representation of a decimal number in another base.
```javascript
var octalVar = "0o46";
console.log(isNaN(octalVar)); // returns false 
```

</br></br>

### A NaN with any mathematical operation results in NaN
```javascript
var numberVar = 2;
var stringVar = "Hello";

var v1 = numberVar - stringVar; 
console.log(v1); // returns NaN 

var v2 = numberVar + stringVar;
console.log(v2); // concatenates the strings

console.log(typeof v2); // returns string
console.log(typeof v1); // returns number (as it is NaN)
```
This is because the "-" operator first coerces both operands to a number. As string is not a number, overall result in NaN.

</br></br>

#### NaN is the only value in JS which is not equal to itself
```javascript
console.log(v1===v1);  // returns false
```




