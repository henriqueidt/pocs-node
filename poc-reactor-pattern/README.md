# POC REACTOR PATTERN

The reactor pattern is used to avoid blocking `Input/Output(I/O)` operations

I/O Operations can perform in two ways:
1. `Blocking I/O`: A function call is made and the execution is paused until data is returned `(Synchronous)`
2. `Non-blocking I/O`: A funcion call is made and the execution continues whithout waiting for the results `(Asynchronous)`

Javascript by default is `synchronous`, single threaded, blocking language.
The `reactor pattern` is what makes Node.js Asynchronous

JS runs synchronously with a single `Call Stack` that executes all code that comes in immediately.

Whenever executing a JS code, a `Global Execution Context (GEC)` is created and added to the `Call Stack`, and then JS is executed line by line.

## Delayed Functions

For delayed executions, like for example `setTimeout`, after the time is expired, the callback it returns is put inside the `Callback Queue`.
The `Event Loop` then acts as the gatekeper, checking for entries in the `Callback Queue` and moving them into the `Call Stack` ONLY IF IT IS EMPTY.

````JAVASCRIPT
setTimeout(function cb() {
  console.log('Hello world')
}, 500)
````

## Promises

Promises callbacks are also waited for the resolution of the promise. The difference is that the callback is now moved into the `Microtask Queue`, which is very similar to the `Callback Queue`, but has higher priority

````JAVASCRIPT
fetch("example.com")
.then(function cb() {
  console.log("fetched")
})

new MutationObserver(function cb(list, observer) {
  console.log("mutations happened: " + list)
})
````

Interesting to notice that `async await` is just a wrap around a Promise that puts all of the code following the `await` call into the callback of the Promise:

````JAVASCRIPT
async function example() {
  const result = await fetch("example.com")
  console.log(result)
}
````

is the same as:

````JAVASCRIPT
function example() {
  return fetch("example.com").then(result => {
    console.log(result)
  })
}
````
