---
title: Async .forEach()
---

# How to make a truly Async .forEach()

First of all, we need to understand what makes JS code asynchronous. You can check my [JS Promises](/blogs/javascript/async-await/promises) post for a more in depth explanation, but the TLDR is: When a WebAPI call returns a `Promise`, the current function/loop will always run to completion before the promise's `resolve` is executed.

Now, lets take a look at `forEach`. All it does is call the specified function with each value.

```JS
function forEach(callback) {
  for (const element of array) {
    callback(element);
  }
}
```

As we can see, the next `callback` is executed as soon as the previous one has returned. Since a returned `Promise` will not be awaited, it will execute the next one immediately.

## Applications

### Parallel

So, lets say we want to perform 5 asynchronous api calls. How can we do this?

If we use `forEach`, we will run into some issues:

```JS
urls.forEach(url => axios.delete(url));

console.log('Done?'); // This will run before the API calls have been responded


urls.forEach(async (url) => axios.delete(url));

console.log('Done?'); // Even passing an async function won't do it
```

This is because each callback will return a `Promise` as soon as the API call is fired. What we want is to pause our function until **all** requests have finished.

The proper way of doing this is:

```JS
const promises = urls.map(url => axios.delete(url))

try {
  const results = await Promise.all(promises)

  console.log('All requests executed successfully!!')
} catch(error) {
  console.error('Some request failed:', error)
}
```

### Sequential

Now, if you need your calls to happen sequentially, instead of in parallel, the best option is a for loop.

```JS
for(const url of urls) {
  await axios.delete(url)
}

console.log('All calls done!')
```
