# typeof operator
* Returns type of the string </br>
* Return type is a non-empty string
</br>

```javascript
var nullVar = null;
console.log("typeof null variable " + typeof nullVar); //returns "object" - to unset a number use undefined and to unset an object use null

var funcVar = function() {};
console.log("typeof function " + typeof funcVar); //returns "function"

var arrayVar = [1,2,3];
console.log("typeof array " + typeof arrayVar); // returns object
var singleElementArray = [1];  // returns object
console.log(typeof singleElementArray);

console.log(typeof " "); // returns string

console.log( typeof NaN ); // returns a number

```
