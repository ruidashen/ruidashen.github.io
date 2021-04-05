## JS Fundamentals

### Q：Some ES6 Features

### A:

- let
- const
- arrow function
- Promise
- spread operator
- default parameter
- import, export

### Q: How to use Promise, Promise.all and Promise.race

### A:

- Promise:

```JavaScript
function fn() {
    return new Promise((resolve,reject)=>{
        if (success) // success
            resolve();
        else { // fail
            reject();
        }
    })
}

fn
.then(handleSuccess)
.catch(handleError)
```

- Promise.all

```JavaScript
Promise.all([promise1,promise2])
.then(handleSuccess) // handleSuccess will only run if promise1 and promise2 both resolve
.catch(handleError) // handleError will run whenever promise1 or promise2 rejects
```

- Promise.race

```JavaScript
Promise.race([promise1,promise2])
.then(handleSuccess) // handleSuccess will run when promise1 or promise2 resolves
.catch(handleError) // handleError will run when either promise1 or promise2 rejects
```

### Q: Function debounce and function throttle

### A:

#### A simple throttle function can be written as:

```JavaScript
// Throttling
function throttle(fn,delay) {
  let canUse = true;

  return function() {
    if (canUse) {
      fn.apply(this,arguments);
      canUse = false;
      setTimeout(()=>{
          canUse = true;
      },delay)
    }
  }
}

const throttled = throttle(()=>console.log('hi'),1000)
window.onresize = throttled;
```

Try running the above code on your browser and resize the window to see what happens.

Note that some people think that throttled function should not be invoked immediately, it should invoke after the delay which is correct in my opinion.

#### A simple debounce function can be writeen as:

```JavaScript
// Debouncing
 function debounce(fn, delay){
   let timerId = null
   return function(){;
     const context = this;
     if(timerId) {
       window.clearTimeout(timerId)
     }
     timerId = setTimeout(()=>{
       fn.apply(context, arguments)
       timerId = null
     },delay)
   }
 }
let debounced = debounce(()=>console.log('hi'),1000);
window.onresize = debounced;
```

### AJAX

Using the XMLHttpRequest object:

```js
var request = new XMLHttpRequest();

request.open("GET", "/xxxx");
request.onreadystatechange = function () {
  if (request.readyState === 4) {
    console.log("request completed");
    if (request.status >= 200 && request.status < 300) {
      console.log("request succeed");
    } else {
      console.log("error");
    }
  }
};
request.send();
```

or simply

```js
var request = new XMLHttpRequest();

request.open("GET", "/xxxx");
request.onload = () => console.log("request succeed");
request.send();
```
