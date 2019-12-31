# call(), apply() and bind()

These 3 functions are all designed to set context, or more specifically, what __this__ refers to.

</br></br>

## call()
The call() method invokes the function immediately. The first parameter in call() method sets the "this" value, which is the object, on which the function is invoked upon. 
The rest of the parameters are the arguments to the actual function.

```javascript
var obj = {
  name: "Shubham"
};

function abc(prof) {
  console.log(`${this.name} is an ${prof}`);
}

abc.call(obj, "intern");
// Shubham is an intern
```


