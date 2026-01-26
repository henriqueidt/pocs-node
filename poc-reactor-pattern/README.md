# POC REACTOR PATTERN

The reactor pattern is used to avoid blocking Input/Output(I/O) operations

I/O Operations can perform in two ways:
1. Blocking I/O: A function call is made and the execution is paused until data is returned (Synchronous)
2. Non-blocking I/O: A funcion call is made and the execution continues whithout waiting for the results (Asynchronous)

Javascript by default is synchronous, single threaded, blocking language.
The reactor pattern is what makes Node.js Asynchronous

JS runs synchronously with a single Call Stack that executes all code that comes in immediately.