# Callback

-   A callback function is a function passed into another function as an argument, which is then invoked inside the outer function.

    ```
    function print(callback) {
        callback();
    }
    ```

## Why Callback functions are required

-   JavaScript runs code sequentially in top-down order.

    Example:

    ```JavaScript
    function taskOne(){
        console.log("Task one is executed");
        taskTwo();
    }
    function taskTwo(){
        console.log("Task two is executed");
    }
    taskOne();
    taskTwo();
    ```
    Output:
    ```
    Task one is executed
    Task two is executed
    ```
    Here taskOne() is executed first, then later taskTwo() is executed.
-   However, there are some cases that code runs after something else happens and also not sequentially. This is called asynchronous programming.
-   Consider a following program

    Example:

    ```JavaScript
    function taskOne(){
        console.log("Task one is executed");
    }
    function taskTwo(){
        console.log("Task two is executed");
    }
    setTimeout(taskOne,2000);
    taskTwo();
    ```
    Output:
    ```
    Task two is executed
    Task one is executed
    ```
    Here even though the taskOne() is called, taskTwo() is executed first, and when the timer ends, taskOne() is executed.
    The function passed to setTimeout() is a callback function.
-   Callbacks make sure that a function is not going to run before a task is completed but will run right after the task has completed.

## Advantage of callbacks

1. Callbacks reduce useage of redundant codes

    - For example, to find area and circumference of circle for given array of radius:

        ```JavaScript
        const area = radius => Math.PI * radius * radius;
        const circumference = radius => 2 * Math.PI * radius;

        // Define the circle function which takes radius values and callbacks for area and circumference
        function circle(radii, areaCallback, circumferenceCallback) {
            const areas = radii.map(areaCallback);
            const circumferences = radii.map(circumferenceCallback);
            return { areas, circumferences };
        }
        ```

2. Callbacks does not pause the execution of main program.
3. Flexibility in Handling Results and Errors.
   Example:
    ```JavaScript
    function divide(a, b, callback) {
        if (b === 0) {
            callback('Cannot divide by zero', null);
        } else {
            callback(null, a / b);
        }
    }
    divide(10, 2, (error, result) => {
        if (error) {
            console.error(error);
        } else {
            console.log('Result:', result);  // Result: 5
        }
    });
    ```

## Nested callbacks or Callback Hell

-   Callback Hell refers to the situation where the code becomes deeply nested due to multiple levels of callbacks, making it difficult to read, understand, and maintain.
-   Example:

    ```JavaScript
    main(function(err, result) {
        if (err) {
            console.error(err);
        } else {
            callback1(result, function(err, newResult) {
                if (err) {
                    console.error(err);
                } else {
                    callback2(newResult, function(err, finalResult) {
                        if (err) {
                            console.error(err);
                        } else {
                            console.log(finalResult);
                        }
                    });
                }
            });
        }
    });
    ```

Callback Hell is also reffered to as 'Pyramid of Doom', since the code grows horizontally, it becomes difficult to read and maintain.
