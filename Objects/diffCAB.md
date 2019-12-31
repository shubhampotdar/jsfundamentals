# call(), apply() and bind()

These 3 functions are all designed to set context, or more specifically, what __this__ refers to.

</br>

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

</br>

## apply()
apply() works in the same way as call(). The only difference of apply() with the call() method is that the
second parameter of the apply() method accepts the arguments to the actual function as an array.

```javascript
var obj1 = {
  prof: "intern"
};

function def(firstName, middleName, lastName) {
  console.log(`${firstName} ${middleName} ${lastName} is an ${this.prof}`);
}

var empName = ["Shubham", "Manish", "Potdar"];

def.apply(obj1, empName);
// Shubham Manish Potdar is an intern
```

</br>

## bind()
The bind() method creates a new function that, when called, has its this keyword set to the provided value.
__.bind__ allows you to set the "this" value now while allowing you to execute the function in the future, because it returns a new function object.

```javascript

var obj3 = {
  name: "Kyle"
};

var obj4 = {
  name: "Suzy"
};

function ghi(question) {
  console.log(`${question} ${this.name}?`);
}

var jkl = ghi.bind(obj3);
jkl("How are you");
// How are you Kyle?

ghi.bind(obj4, "What's up")();
// What's up Suzy?
```


