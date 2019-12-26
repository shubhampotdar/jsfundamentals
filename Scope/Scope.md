# Scoping

* var is functionally scoped not blocked scoped.
* Js automatically creates undeclared variables (existing inside of functions and blocks) to global scope (but during phase 2) (also only if strict mode isn’t enabled)
```javascript

var name = "Shubham";

function f1() {
  console.log(name);
  name = "changed name";
  console.log(name);
   age = 21;        // auto creates in global scope as it has not been declared (if strict mode isn't enabled)
   function abc() {
   	gpa = 9; // also auto created in global scope
   }
   abc();
   console.log(gpa);
}



{
	fav = 66;
}

console.log("fav ="+fav); // returns fav =66


//console.log(age);  will return reference error
console.log(name);
f1();
console.log(age);
console.log(name);
console.log(gpa);
/* (if strict mode isn't enabled )
console output for lines 259 - 272 
>> Shubham
>> Shubham
>> changed name
>> 9 
>> 21
>> changed name
>> 9
 */
 ```
* Js is a lexically scoped language I.e. all scopes are decided during compile time.
* JS program runs in two phases: compilation phase and execution phase. In the first phase all the formal declarations and statements starting with “function” are compiled and their scope is set. During the second phase all the assignments, function calls etc are executed ( source and target references are decided)
* IIFE - immediately invoked function expression. Variables declared inside it cannot be accessed outside the life scope. Prevents polluting scope.
```javascript
// IIFE - immediately invoked function expressions--------------------
var v1 = 1;
var rrr = 1;
(function h(v1) {
  var v2 = 22;
  console.log("rrr" + rrr); // 1
  rrr++;
  console.log(rrr); // 2
  v1 = 24;
})(5);

console.log("rrr outside iife " + rrr); // rrr outside iife 2
//console.log(v2); - error (not defined)
// h();   - gives reference error
console.log(v1); //  1

/* Assigning the IIFE to a variable 
stores the function's return value, 
not the function definition itself. */
var iifeVar = (function() {
  return 1;
})();

console.log("iifeVar = " + iifeVar); // iifeVar = 1
```
* Let and const are block scoped.
* Const variables cannot be reassigned and have to be assigned a value when they are declared. (They can be mutated though like changing a particular index of a const array.)
* Function declarations are hoisted. 
* Function expressions are not hoisted as the assignment takes place in the execution phase (target reference). But it should be remembered that the function on the RHS of an function expression is compiled and assigned scope in the compilation phase. Also function part of a function expression takes its own scope.
* When var hoists, js assigns it to undefined
```javascript

f2();
var fe1 = 1;
function f2() {
	console.log(fe1);    // undefined
 	var fe1 = 2;
	console.log(fe1);   //   2

	function abc() {
		console.log(fe1);    // 2
	}

	abc();
}
```
* When let hoists, js creates a space in memory by the name of the identifier but doesn’t assign it any value.

