# Consistency

Be obsessed about consistency. It helps you:

* Reduce bugs
* Create easy to understand code
* Get respect among peers

## Variable names

Never do this:

```javascript
const result = this.getDevices();
result.forEach(device => {
  // Just stop.
});
```

Always do this:

```javascript
const devices = this.getDevices();
devices.forEach(device => {
  // Just stop.
});
```

Always use plural and singular, as close to what it is as you can. If you have a method `getThings()`, then call the variable you store them in `things`. When you loop over them, call the current iteration `thing`.

## Capitalization

Certain names, such as brands, should **always** be written correctly. **Especially in comments.**

Never do this:

```javascript
// Fixes an ios bug that apple introduced two years ago
```

Always do this:

```javascript
// Fixes an iOS bug that Apple introduced two years ago
```

It's your way of respecting the work of other great people. And it's a way to show you care about details. _I trust people who care about details._

Imagine you have published a library called `RotateDatabaseDaemon` and people start calling it `rotatedatabasedaemon` or `RotateDatabasedaemon` or `rotdd` or whatever.
