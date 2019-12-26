# ToPrimitive(hint)

* If hint is "number" then invokes valueof() -> toString()
* If hint is "string" then invokes toString() -> valueOf()


# ToString()

```javascript
console.log(negZeroVar.toString()); // returns zero
// ToString(object/array) invokes ToPrimitive(string)

var emptyArrVar = [];
console.log( emptyArrVar.toString() ); // returns empty string ""
```
