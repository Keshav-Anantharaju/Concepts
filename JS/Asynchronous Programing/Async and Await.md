# Asynchronous function

-   Asynchronous Programming allows to perform tasks that takes time to execute (such as fetching data from a server or reading files) without blocking the execution of other code. Instead of waiting for a task to complete, the code moves on to other tasks and handles the result later.

## Common methods to manage asynchronous code.

1. [Callbacks](https://github.com/Keshav-Anantharaju/Concepts/blob/main/JS/Functions/Callback%20functions.md)
2. [Promises](https://github.com/Keshav-Anantharaju/Concepts/blob/main/JS/Asynchronous%20Programing/Promise.md)
3. Async/Await: Async/Await is a syntactic sugar on top of Promises, making asynchronous code look synchronous.

### How Async/Await Works

-   Async functions always return a Promise.

    ```JavaScript
    async function getData() {
    return;
    }
    console.log(getData());
    ```

    Outputs:

    ```
    Promise {[[PromiseState]]: 'fulfilled', [[PromiseResult]]: undefined, Symbol(async_id_symbol): 83, Symbol(trigger_async_id_symbol): 48}
    ```

    If any other values is returned except 'Promise', async function will wrap the values in promise and return.

    ```JavaScript
    async function getData() {
        return "Hello";
    }
    console.log(getData());
    ```

    Outputs:

    ```
    Promise {[[PromiseState]]: 'fulfilled', [[PromiseResult]]: 'Hello', Symbol(async_id_symbol): 83, Symbol(trigger_async_id_symbol): 48}
    ```

-   Await is a keyword that can be only be used inside async function.
-   Await pauses execution until the Promise is resolved or rejected.
    ```JavaScript
      async function getData(){
          const p = await /* code */
          console.log(p);
    }
    ```

    Will display the value of p.

-   Try...catch handles errors.

### Chaining with Async/Await

-   Just like Promise.then(), Chaining can be done in Async/Await.

    ```JavaScript
    async function process() {
        try {
            const result = await fetchData();
            const processedResult = await processResult(result);
            await saveResult(processedResult);
            console.log("Data saved successfully!");
        } catch (error) {
            console.error(error);
        }
    }

    process();
    ```

## Inversion of control

1.  With Callbacks

    -   Callbacks are function that are passed as an argument to another function.
    -   When a developer defines a function, he passes his callback function to a 3rd party API to be executed.
    -   With the 3rd party API, the developer is unaware about following things
        1. A Callback may be called multiple times.
        2. A Callback would never get called.
        3. A Callback may be called synchronously.
    -   Consider an example below.
    
        ```JavaScript
        function fetchData(callback) {
          setTimeout(() => {
              // External source manages the timing
              callback("Data received");  // Control is inverted: the callback handles the result
          }, 1000);
        }
        ```
    -   Here the callback function is passesd as an argument to the fetchData and later called in setTimeout().

    -   The developer do not have control over the callback function, and relies about the functionality of setTimeout().

    -   To handle inversion of control, we use promises.

2.  With Promises

-   Promises allow us to not rely on callbacks passed into asynchronous functions to handle asynchronous results.
-   Instead, we can chain Promises for a sequence of asynchronous operations, escaping the Callback hell.

    Example:

    ```JavaScript
    const cart = ["TV", "Washing Machine", "Mini Fridge"];

    // With callback
    createOrder(cart, function(orderId){
        proceedWithPayement(orderId);
    });

    // with Promise
    const promise = createOrder(cart);
    promise.then((orderId) => {proceedWithPayment(orderId)});
    ```
    In the first part of the above example, we are inverting the control to the third-party library or API. We rely on the API to execute our callback

    In the second part, we are using a Promise object instead of a callback, so as soon as the Promise object gets filled, we can use the ‘then()’ method to call our proceedWithPayment() function. Here we are the ones in control this time and can easily make sure that our function gets called only once.

## Comparing with other asynchronous methods

|   **Aspect**      |           **Callbacks**           |          **Promises**             |              **Async/Await**              |
|-------------------|-----------------------------------|-----------------------------------|-------------------------------------------|
|**Readability**    |Can lead to deeply nested code.    |Better readability with chaining.  |Most readable and synchronous-like syntax. |
|**Error Handling** |Errors need explicit checks in each callback.|Centralized with .catch().         |Centralized with try/catch.      |
|**Control Flow**   |Complex for multiple asynchronous tasks.|Easier chaining of async operations. |Simplest for managing complex async |
|**Complexity**     |High complexity for nested callbacks. |Reduced complexity through chaining. |Simplest approach for async tasks.    |
