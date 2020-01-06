# Implementing memoization via closures

```javascript
const memoizedAdd = function() {
  let cache = [];
  return function(n) {
    if (cache[n]) {
      console.log("Fetching from cache");
      return cache[n];
    } 
    else {
      console.log("Calculating result");
      let result = n + 10;
      cache[n] = result;
      return result;
    }
  };
};


const newAdd = memoizedAdd();
console.log(newAdd(9)); 
console.log(newAdd(9)); 

const neweradd = memoizedAdd();
console.log(neweradd(9)); 

/* console output:
Calculating result
19
Fetching from cache
19
Calculating result
19
*/
```
