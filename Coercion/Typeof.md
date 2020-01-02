# typeof operator
* Returns type of the string </br>
* Return type is a non-empty string
</br>

## typeof null
```javascipt
var nullVar = null;
console.log("typeof null variable " + typeof nullVar); // object
```
So __null__ can be used to unset an object (similarly __undefined__ can be used to unset a number).

</br></br>

## typeof on a function
```javascript
var funcVar = function() {};
console.log("typeof function " + typeof funcVar); // function
```
</br></br>

## typeof on arrays
```javascript
var arrayVar = [1,2,3];
console.log("typeof array " + typeof arrayVar); // object
var singleElementArray = [1];  
console.log(typeof singleElementArray); // object
```

</br></br>

## Other examples:
```javascript
console.log(typeof " "); // string
console.log( typeof NaN ); // number
var aa;
console.log(typeof aa); // undefined
```
