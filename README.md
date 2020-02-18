# Unit 6 Lesson 1 Practice: Promises

## Directions
Fork and clone this lab. Respond to questions in clear, concise sentences directly within this markdown file.

**1. What will the following code snippet log? Why?**
  ```javascript
  console.log('Line 1')
  setTimeout(() => console.log('Line 2'), 1000)
  console.log('Line 3')
  ```
  
  The code above will print the following to the console:
  The console will log "Line 1", then "Line 3", and finally "Line 2". This is because setTimeout() will execute it's 
  function after 1000 milliseconds. Meaning that function will log "Line 2" after 1 second, and in the meantime it continues down
  the source code. By that time, "Line 3" will have been logged.

**2. What does the following code snippet log? Why?**
  ```javascript
  function createPromise(seconds) {
    return new Promise((resolve) => {
      setTimeout(function() {
        resolve(`After ${seconds} second(s), this promise is resolved.`)
      }, seconds * 1000)
    })
  }

  console.log(createPromise(1000))
  ```

  The promise is return with a status of pending and value of undefined. When the promise is resolved, then this function will have a value of
  `After ${seconds} second(s), this promise is resolved.` Aproximately 1 second after the promise has been resolved.
  
**3. How do we use our `createPromise` function to log `"After 1 second(s), this promise is resolved."`**

  We use .then() to go into our Promise once it is resolved, so we can log the value.

**4. What does the following code snippet return? What does it log?**
  ```javascript
  const ourPromise = new Promise((resolve) => {
    resolve(12);
  })

  ourPromise.then(value => value * 2);
  ```
  
  This snippet returns a resolved promise, with an updated value.

**5. What does the following code snippet return? What does it log?** <br> _
**Note:** Instead of using the `Promise` constructor to create a Promise that immediately resolves to 12, we can just use the [`Promise.resolve`]
(https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/resolve) method._

  ```javascript
  const ourPromise = Promise.resolve(12);
  ourPromise.then(value => value * 2).then(value => value + 10);
  ```

  This returns the promise with a updated properties like promiseValue: 34.
  
**6. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.resolve(12).then(value => value * 2).then(value => console.log(value + 10))
  ```

**7. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.resolve(12).then(value => value * 2).then(value => {
    console.log(value + 10);
    return value + 10;
    });
  ```

**8. What does the following code snippet return? What does it log? How does this differ from the question above?**
  ```javascript
  Promise.reject(12).then(value => value * 2).then(value => {
    console.log(value + 10);
    return value + 10;
    }).catch(reason => {
      const message = `${reason} is a bad number.`;
      console.error(message);
      return reason;
    });
  ```