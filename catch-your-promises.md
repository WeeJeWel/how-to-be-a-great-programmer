# Catch Your Promises

> When I was younger, I was the worst at catching any ball. Therefore I decided to make up for it by always catching my promises.

The number one mistake I see that unexperienced JavaScript programmers make is not catching their promises.

## Bad Example

Consider the following:

```js
async function getSomething() {
  return fetch('https://something.com');
}

something.on('my_event', async () => {
  const something = await getSomething();
  console.log(something);
});
```

What happens when `getSomething()` rejects? In Node.js, it throws an `unhandledRejection` event and it kills your process! Because during testing `something.com` was online, you might've never encountered this and think your code is great. But it's not, it's actually really bad.

You cannot just make any method `async`! Every Promise _needs_ to be catched. It's like Yin & Yang, Salt & Pepper and Lily & Marshall. They belong together.

## A Somewhat Better Example

```js
something.on('my_event', async () => {
  try {
    const something = await getSomething();
    console.log(something);
  } catch( err ) {
    console.error('Error getting something:', err);
  }
});
```

See how we now catch the promise? But it's not great yet. What happens when someone adds code above `try {`? It still can reject unhandled! It's a small chance, but it is possible. So better be safe than sorry.

## The Best Example

Therefore, this is our final form of beauty:

```js
something.on('my_event', () => {
  // From a sync context, create a new async context
  Promise.resolve().then(async () => {
    const something = await getSomething();
    console.log(something);
  }).catch(err => {
    console.error('Error getting something:', err);
  });
});
```

The event handler of `my_event` is sync, as is expected, and _inside_ the sync method we create a new _async_ context by calling `Promise.resolve().then(async () => { ... })` and eventually catch it by appending `.catch(err => { ... })`.

This pattern forces you to think about _what should actually happen when this Promise rejects?_ instead of going on with your day and letting someone more experienced clean up your mess.

## Bonus: Two types of Promise chains

In almost all situations, there are two types of promise chains.

**The first is a Promise chain started from a Request/Response**. For example a web server handling a request, or a user pressing a button.

This is the easiest one to code for. Simply make the upper-most method async, attach a catch-handler (e.g. return HTTP 5XX and send the error as JSON) and `await` all your code while going down.

**The second is a Promise chain started externally.**  For example through an event emitter, or a parallel track in your code that's considered _nice to have_ (for example, send a message to Slack when running a cronjob).

In this case, think about what the Promise rejection should do (almost always: log to the console), and then code it _in a new Promise chain_ by using the `Promise.resolve().then(async () => { ... }).catch(err => { ... })` pattern.
