# POC REACTOR PATTERN

The reactor pattern is used to avoid blocking `Input/Output(I/O)` operations

I/O Operations can perform in two ways:
1. `Blocking I/O`: A function call is made and the execution is paused until data is returned `(Synchronous)`
2. `Non-blocking I/O`: A funcion call is made and the execution continues whithout waiting for the results `(Asynchronous)`

Javascript by default is `synchronous`, single threaded, blocking language.
The `reactor pattern` is what makes Node.js Asynchronous

JS runs synchronously with a single `Call Stack` that executes all code that comes in immediately.

Whenever executing a JS code, a `Global Execution Context (GEC)` is created and added to the `Call Stack`, and then JS is executed line by line.

For delayed executions, like for example `setTimeout`, after the time is expired, the callback it returns is put inside the `Callback Queue`.
The `Event Loop` then acts as the gatekeper, checking for entries in the `Callback Queue` and moving them into the `Call Stack`

````JAVASCRIPT
setTimeout(function cb() {
  console.log('Hello world')
}, 500)
````