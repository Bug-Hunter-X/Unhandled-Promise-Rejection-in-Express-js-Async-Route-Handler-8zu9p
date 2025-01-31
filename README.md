# Unhandled Promise Rejection in Express.js Async Route Handler

This repository demonstrates a common error in Express.js applications: unhandled promise rejections within asynchronous route handlers.  Failure to properly handle errors in asynchronous operations can lead to silent failures, making debugging difficult.

## The Problem

The `bug.js` file contains an Express.js server with an asynchronous route handler.  This handler uses `Promise.then()` and `Promise.catch()`, but the `catch` block only logs the error to the console. This does not prevent the promise rejection from bubbling up and potentially crashing the application (or at least making it unstable).  In a production environment, this could go unnoticed unless carefully monitored.

## The Solution

The `bugSolution.js` file demonstrates the correct way to handle this situation using either `try...catch` within an `async` function, or Express.js's built-in error handling middleware. This approach prevents the unhandled promise rejection.