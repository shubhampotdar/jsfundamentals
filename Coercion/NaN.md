# NaN - invalid number (~~Not a number~~)
* Only value in JS which is not equal to itself </br>
* A NaN number with any mathematical operation results in NaN </br>
* Strings when coerced to a number return NaN </br>


```javascript
var numberVar = 2;
console.log ("isNaN for number -  " + isNaN(numberVar)); // returns false

// isNaN() coerces value to number before checking
var stringVar = "Hello";
console.log("isNAN for string - " + isNaN(stringVar)); // returns true
var na = Number("n/a");
console.log("Number() function on a string - " + Number(stringVar)); // returns NaN - strings when coerced to a number return NaN
console.log(isNaN(na)); // returns true
console.log(Number(" ")); // returns 0
console.log(isNaN(" ")); // returns false - because isNaN() first coerces it to a number and so a empty string first changes to zero which is a number

// refer - https://stackoverflow.com/questions/825402/why-does-isnan-string-with-spaces-equal-false

var octalVar = "0o46";
console.log("isNaN for octal representation -  " + isNaN(octalVar)); // returns false 
var octalVarToNum = Number(octalVar); // coercing it to a number
console.log("after coercing octal representation string to number -  "+isNaN(octalVarToNum)); // still returns false

//a NaN number with any mathematical operation results in NaN
var v1 = numberVar - stringVar; 
console.log(v1); // returns NaN ( "-" operator first coerces both operands to a number. as string is not a number, overall result in NaN )
var v2 = numberVar + stringVar;
console.log(v2); // concatenates the strings
console.log(typeof v2); // returns string
console.log(typeof v1); // returns number (as it is NaN)

// NaN is the only value in JS which is not equal to itself
console.log(v1===v1);  // returns false


//Number.is((NaN() performs no form of coercion and specifically tells if it is NaN
console.log( Number.isNaN(na) ); // returns true
console.log( Number.isNaN(stringVar) ); // returns false (would return true incase only isNaN was used)
```
