# Promise

A `Promise` is an object that represents the eventual completion (or failure) of an asynchronous operation.

### Basic Structure of a Promise

```JavaScript
const promise = new Promise((resolve, reject) => {
  // Asynchronous operation
  if (/* operation successful */) {
    resolve(result); // Operation was successful
  } else {
    reject(error);   // Operation failed
  }
});
```

### Promise states
- A Promise in JavaScript represents the eventual result of an asynchronous operation and can be in one of three distinct states:

1. **Pending:**
	- The 'pending' state is the initial state of a promise. When a promise is created, it starts in the 'pending' state.
	- The final result of the asynchronous operation is not yet known.
2. **Fulfilled**
	- A promise transitions to the 'fulfilled' state when the asynchronous operation completes successfully.
	- Resolved: The Promise has been resolved with a value.
	- The promise is now settled.

3. **Rejected**
	- A Promise transitions to the Rejected state when the asynchronous operation fails.
	- The promise is now settled.

### Key Methods of Promises

1. **then(onResolve, onReject)**

    - Adds fulfillment and rejection handlers to the promise.
    - Returns a new promise resolving to the return value of the called `onResolve` or `onReject` callback.
    - then() method makes sure to use callback function only when the promise is either resolved or rejected.

    **Syntax:**

    ```JavaScript
    promise.then(onResolve, onReject);
    ```

    **Example:**

    ```JavaScript
    const pr = new Promise((resolve, reject) => {
    	setTimeout(() => resolve("Success!"), 1000);
    });

    pr.then((result, error) => {
      	if (error) return console.log(error); // Handles error
      	else return console.log(result); // Handles result
    });
    ```

2. **catch(onReject)**

    - catch() handles promise rejection.
    - It immediately returns another promise object.
    - It is a shortcut for `Promise.prototype.then(undefined, onReject)`

    **Syntax:**

    ```javascript
    promise.catch(onReject);
    ```

    **Example:**

    ```javascript
    const pr = new Promise((resolve, reject) => {
        setTimeout(() => reject("Error!"), 1000);
    });

    pr.catch((error) => console.log(error)); // Error!
    ```

3. **finally(onFinally)**

    - Adds a handler to be called when the promise is settled (either fulfilled or rejected).
    - It immediately returns another Promise object.
    - finally() avoids duplicating code in both the promise's then() and catch() handlers.

    **Syntax:**

    ```javascript
    promise.finally(onFinally);
    ```

    **Example:**

    ```JavaScript
    const pr = new Promise((resolve, reject) => {
        setTimeout(() => resolve("Finished!"), 1000);
    });

    pr
	.then((result) => console.log(result)) // "Finished!"
	.finally(() => console.log("Cleanup")); // Cleanup
    ```

    ```JavaScript
    const pr = new Promise((resolve, reject) => {
        setTimeout(() => {
    		if (Math.random() > 0.5) {
      			resolve('Finished');
    		} else {
      			reject('Uh oh');
    		}
    	});
    });

    pr
    .then((result) => {
    	console.log(result);
    })
    .catch((err) => {
    	console.error(err);
    })
    .finally(() => {
    	console.log('End of Promise');
    });
    ```

4. **Promise.all(iterable)**

    - Promise.all() is a static method that takes an iterable of promises as input and returns a single Promise.
    - The returned promise fulfills when all of the input's promises fulfill (including when an empty iterable is passed).
    - The returned promise rejects when any of the iterable promises rejects, with this first rejection reason.

		**Syntax:**

		```JavaScript
		Promise.all([promise1, promise2, ...])
		```

		**Example:**

		```javascript
		const pr1 = new Promise((resolve, reject) => {
			return resolve("Promise 1 resolved");
		});
		const pr2 = new Promise((resolve, reject) => {
			return resolve("Promise 2 resolved");
		});
		const pr3 = new Promise((resolve, reject) => {
			return resolve("Promise 3 resolved");
		});
		const prAll = Promise.all([pr1, pr2, pr3]);
		prAll
			.then((result) => console.log(result)) // ['Promise 1 resolved', 'Promise 2 resolved', 'Promise 3 resolved']
			.catch((error) => console.error(error));
		```

    - When one or more promise is rejected:

		```JavaScript
		const pr1 = new Promise((resolve, reject) => {
		return reject("Uh oh! Promise 1 failed to resolve");
		});
		const pr2 = new Promise((resolve, reject) => {
			return resolve("Promise 2 resolved");
		});
		const pr3 = new Promise((resolve, reject) => {
			return resolve("Uh oh! Promise 3 failed to resolve");
		});
		const prAll = Promise.all([pr1, pr2, pr3]);
		prAll
			.then((result) => console.log(result))
			.catch((error) => console.error(error)); // "Uh oh! Promise 1 failed to resolve"
		```

5. **Promise.allSettled(iterable)**

    - Returns a promise that resolves after all of the given promises have either resolved or rejected.

		**Syntax:**

		```javascript
		Promise.allSettled([promise1, promise2, ...])
		```

		**Example:**

		```JavaScript
		const pr1 = new Promise((resolve, reject) => reject("Uh oh! Promise 1 did not resolve"));
		const pr2 = new Promise((resolve, reject) => resolve("Promise 2 resolved"));
		const pr3 = new Promise((resolve, reject) => resolve("Promise 3 resolved"));

		const prAll = Promise.allSettled([pr1, pr2, pr3]);
		prAll.then((results) => results.forEach(result=>console.log(result)));
		```

		Outputs:

		```
		{status: 'rejected', reason: 'Uh oh! Promise 1 did not resolve'}
		{status: 'fulfilled', value: 'Promise 2 resolved'}
		{status: 'fulfilled', value: 'Promise 3 resolved'}
		```

6. **Promise.any(iterable)**

    - Promise.any() is a static method that takes an iterable of promises as input and returns a single Promise.
    - The returned promise fulfills when any of the input's promises fulfills, with this first fulfillment value.
    - It rejects when all of the input's promises reject (including when an empty iterable is passed), with an AggregateError containing an array of rejection reasons.

		**Syntax:**

		```JavaScript
		Promise.any([promise1, promise2, ...])
		```

		**Example:**

		```javascript
		const pr1 = new Promise((resolve, reject) =>
			reject("Uh oh! Promise 1 failed to resolve")
		);
		const pr2 = new Promise((resolve, reject) => resolve("Promise 2 resolved"));
		const pr3 = new Promise((resolve, reject) =>
			resolve("Uh oh! Promise 3 failed to resolve")
		);
		const prAny = Promise.any([pr1, pr2, pr3]);
		prAnl
			.then((result) => console.log(result)) // Promise 2 resolved
			.catch((error) => console.error(error));
		```

		If all the promises are rejected:

		```JavaScript
		const pr1 = new Promise((resolve, reject) => reject("Uh oh! Promise 1 failed to resolve"));
		const pr2 = new Promise((resolve, reject) => resolve("Uh oh! Promise 1 failed to resolve"));
		const pr3 = new Promise((resolve, reject) => resolve("Uh oh! Promise 3 failed to resolve"));
		const prAny = Promise.any([pr1, pr2, pr3]);
		prAny
			.then((result) => console.log(result))
			.catch((error) => console.error(error)); // Uh oh! Promise 1 failed to resolve
		```

7. **Promise.race(iterable)**

    - Promise.any() is a static method that takes an iterable of promises as input and returns a single Promise.
    - The returned promise settles with the eventual state of the first promise that settles.

		**Syntax:**

		```JavaScript
		Promise.race([promise1, promise2, ...])
		```

		**Example:**

		```JavaScript
		const promise1 = new Promise((resolve) =>
			setTimeout(resolve, 100, "First")		// First promise to be settles
		);
		const promise2 = new Promise((resolve) =>
			setTimeout(resolve, 200, "Second")
		);

		Promise.race([promise1, promise2])		// returns promise as soon as promise 1 is settled
			.then((result) => console.log(result)) // "First"
			.catch((error) => console.log(error));
		```

		If the first that settles is rejected

		```JavaScript
		const promise1 = new Promise((resolve, reject) =>
			setTimeout(reject, 100, "First")		// First promise to be settles
		);
		const promise2 = new Promise((resolve) =>
			setTimeout(resolve, 200, "Second")
		);

		Promise.race([promise1, promise2])		// returns promise as soon as promise 1 is settled
			.then((result) => console.log(result))
			.catch((error) => console.log(error)); // "First"
		```

8. **Promise.resolve(value)**

    - Returns a Promise object that is resolved with the given value.

		**Syntax:**

		```javascript
		Promise.resolve(value);
		```

		**Example:**

		```javascript
		Promise.resolve("Resolved")
			.then((value) => console.log(value)) // "Resolved"
			.catch((error) => console.log(error));
		```

9. **Promise.reject(reason)**

    - Returns a Promise object that is rejected with the given reason.

		**Syntax:**

		```javascript
		Promise.reject(reason);
		```

		**Example:**

		```javascript
		Promise.reject("Rejected")
			.then((value) => console.log(value))
			.catch((reason) => console.log(reason)); // "Rejected"
		```

### Promise chaining

-   Promise chaining refers to the technique of linking multiple .then() and .catch() methods to a single Promise, where each .then() method returns a new Promise.
-   This allows you to handle asynchronous operations one after another, where the output of one operation becomes the input for the next.

-   **Syntax:**

    ```JavaScript
    asyncFunction()
    .then(result => {
    	// Handle the result of asyncFunction
    	return anotherAsyncFunction(result); // Return a new Promise
    })
    .then(newResult => {
    	// Handle the result of anotherAsyncFunction
    	return yetAnotherAsyncFunction(newResult); // Return a new Promise
    })
    .then(finalResult => {
    	// Handle the final result
    	console.log(finalResult);
    })
    .catch(error => {
    	// Handle any error that occurred in any of the previous Promises
    	console.error('Error:', error);
    });
    ```

    Example:

    ```JavaScript
    function getUser(id) {
    return new Promise((resolve, reject) => {
    	setTimeout(() => {
    	console.log('Fetching user data...');
    	if (id) {
    		resolve({ id, name: 'John Doe' });
    	} else {
    		reject('No user ID provided');
    	}
    	}, 1000);
    });
    }

    function getUserPosts(user) {
    return new Promise((resolve) => {
    	setTimeout(() => {
    	console.log(`Fetching posts for user ${user.name}...`);
    	resolve(['Post1', 'Post2', 'Post3']);
    	}, 1000);
    });
    }

    function getPostComments(post) {
    return new Promise((resolve) => {
    	setTimeout(() => {
    	console.log(`Fetching comments for post ${post}...`);
    	resolve(['Comment1', 'Comment2']);
    	}, 1000);
    });
    }

    // Promise chaining
    getUser(1)
	.then(user => getUserPosts(user))
	.then(posts => getPostComments(posts[0]))
	.then(comments => console.log('Comments:', comments))
	.catch(error => console.error('Error:', error));
    ```

    The above program will produce:

    ```
    Fetching user data...
    Fetching posts for user John Doe...
    Fetching comments for post Post1...
    Comments: (2) ['Comment1', 'Comment2']
    ```

#### Why promise chaining is necessary

1. **Managing Sequential Asynchronous Operations and**
2. **Error handling across multiple operations**

    - Promise chaining helps manage asynchronous operations that need to occur in sequence.
    - Chained .catch() handles errors from any part of the promise chain.
    - Example:

        ```JavaScript
        getUser(1)
		.then(user => getUserPosts(user)) // will be executed when promise returned by getUser is resolved.
		// getUserPosts(user) will return promise.
		.then(posts => getPostComments(posts[0])) // will be executed when promise returned by getUserPosts(user) is resolved.
		// getPostComments(posts[0]) will return promise.
		.then(comments => console.log('Comments:', comments)) // will be executed when promise returned by getPostComments(posts[0]) is resolved.
		.catch(error => console.error('Error:', error)); // will be executed if any of the above promise is rejected.
        ```

3. **Improving Readability and Maintainability**

    - Chained promises help avoid “callback hell” where nested callbacks can become hard to read and maintain. Promises and chaining provide a linear flow of operations that is easier to understand.
    - Above example with callbacks.

        ```JavaScript
        getUser(1, function (err, user) {
        	if (err) throw err;
        	getUserPosts(user, function (err, posts) {
        		if (err) throw err;
        		getPostComments(posts[0], function (err, comments) {
        			if (err) throw err;
        			console.log(comments);
        		});
        	});
        });
        ```

4. **Combining Multiple Promises**

    - Multiple promises returning from asynchronous operation can be handled using Promise.all() or Promise.race() and then chain additional operations.
    - Example:

        ```JavaScript
        Promise.all([getUser(1), getUser(2)])
		.then(([user1, user2]) => {
		// Both users' data are available
		})
		.catch(error => console.error('Error:', error));
        ```

5. **Chaining with async and await** 
	- Using `async/await` syntax for chaining can make your code look even cleaner:
		```JavaScript
		async function handleUser() {
			try {
				const user = await getUser(1);
				const posts = await getUserPosts(user);
				const comments = await getPostComments(posts[0]);
				console.log(comments);
			} catch (error) {
				console.error('Error:', error);
			}
		}

		handleUser();
		```
#### Error handling in promise
1. **Error thrown inside .then() when there is .catch()**
	- Any error occurerd inside .then() will be handled by .catch() placed at end of promise chain.
	- Any subsequent .then() function written between .catch and error thrown will not be executed.
	- Example:
		```JavaScript
		Promise.resolve("Hello")
		.then(data => {				// This function processes the data
			throw new Error("Something went wrong in then"); 	// An error is thrown
			return processData(data);  // This line is not reached
		})
		.then(result => {			// This function is skipped.
			console.log(result);
		})
		.catch(error => {			// This .catch() handles the error thrown 
			console.error("Caught an error:", error.message);
		});
		```

2. **Error thrown inside .then() when there is no .catch()**
	- The error causes the Promise to be rejected, but since there is no .catch() block, the rejection is unhandled.

		```JavaScript
		Promise.resolve("Hello")
		.then(data => {
			// This function processes the data
			throw new Error("Something went wrong in then"); // An error is thrown
			return processData(data);  // This line is not reached
		})
		.then(result => {
			// This function will not run
			console.log(result);
		});
		```
		Outputs:
		```
		Uncaught Error Error: Something went wrong in then
		```
## References
1. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
2. [JavaScript.info](https://javascript.info/promise-basics)
3. [How Promises Work in JavaScript – A Comprehensive Beginner's Guide By FreeCodeCamp.org](https://www.freecodecamp.org/news/guide-to-javascript-promises/)






