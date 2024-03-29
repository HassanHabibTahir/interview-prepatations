# interview-prepatations

### Using var

Variables declared with var have function scope, not block scope. That means, the variable i declared using var inside the loop will be hoisted to the top of the function containing the loop.
In this case, by the time the setTimeout functions execute, the loop has already completed its iterations, and the value of i will be equal to 15 for all the setTimeout callbacks. This happens because var doesn't create a new i variable for each iteration of the loop; instead, it reuses the same i variable throughout the loop.

```javascript
for(var i = 0; i < 15; i++) {
  setTimeout(function() {
    console.log(i);
  }, 1000);
}
```

### Using Let

Variables declared with let have block scope. Each iteration of the loop will have its own lexical environment, creating a new i variable with each iteration.
When using let, each setTimeout callback will capture the value of i at the time it was created, which means each callback will log the value of i corresponding to its respective iteration of the loop. So, you'll see values from 0 to 14 logged with a delay of 1 second between each log.


```javascript
for(let i =0;i<15;i++){
  setTimeout(function(){
    console.log(i);
  },1000)
}

```