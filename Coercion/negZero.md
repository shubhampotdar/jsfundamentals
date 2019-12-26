,,,javascript
var negZeroVar = -0;
console.log(negZeroVar===-0); //returns true (ofc)
console.log(negZeroVar===0); // returns true

console.log(negZeroVar.toString()); // returns 0

console.log(negZeroVar<0); // returns false
console.log(negZeroVar>0); // returns false

console.log(Object.is(negZeroVar,0)); // returns false
console.log(Object.is(negZeroVar,-0)); // returns true

console.log( Math.sign(3) +" " + Math.sign(-3) + " " + Math.sign(0) ); // returns 1 -1 0
console.log( Math.sign(-0) ); // returns -0
console.log( " " + Math.sign(-0)); // returns 0  (this statement evaluates to console.log(" "-0)). as strings cannot be subtracted, the space is coerced to a number and then 0-0 is performed
// refer : https://stackoverflow.com/a/24383847   (difference in behaviour of + and - operators in between strings)

// fixing math.sign method
var v = numBeChecked => {
	return numBeChecked !== 0 ? Math.sign(numBeChecked) : Object.is(numBeChecked,-0) ? -1:1;

}
,,,
