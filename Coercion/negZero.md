# Negative Zero (-0)

### Triple equating -0 with 0 returns true
```javascript
var negZeroVar = -0;
console.log(negZeroVar===-0); //returns true (ofcourse)
console.log(negZeroVar===0); // returns true
```

</br>

### Coercion of -0 to string eliminates minus sign
```javascript
console.log(negZeroVar.toString()); // returns 0
```
</br>

### Object.is can be used to check for -0
```javascript
console.log(Object.is(negZeroVar,0)); // returns false
console.log(Object.is(negZeroVar,-0)); // returns true
```
</br>

### Math.sign 
Math.sign returns -1 for negative numbers and 1 for positive numbers. For -0 it returns -0 and 0 for 0.
```javascript
console.log( Math.sign(3) +" " + Math.sign(-3) + " " + Math.sign(0) ); // returns 1 -1 0
console.log( Math.sign(-0) ); // returns -0
```
</br>
The following snippet is a fix for returning -1 or 1 for zero and negative zero as well.
```javascript
var v = numBeChecked => {
	return numBeChecked !== 0 ? Math.sign(numBeChecked) : Object.is(numBeChecked,-0) ? -1:1;

}
```

</br>

### Other examples
```javascript
console.log(negZeroVar<0); // returns false
console.log(negZeroVar>0); // returns false
```
```javascript
console.log( " " + Math.sign(-0)); // returns 0 
```
The last statement evaluates to console.log(" "-0)). as strings cannot be subtracted, the space is coerced to a number and then 0-0 is performed. </br>
Refer : <https://stackoverflow.com/a/24383847>   (difference in behaviour of + and - operators in between strings)


