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
