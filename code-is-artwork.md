# Code is an artwork

Great code should be easy to read. Bugs should be obvious to spot. For example:

```javascript
async function sendMessageToUser(userId, message) {
  const userId = 'abcd';
  const user = this.getUser(userId);
  await user.sendMessage(message);
}
```

Do you see how `userId` and `user` aligns? Now let's see this with a typo:

```javascript
async function sendMessageToUser(userId, message) {
  const userId = 'abcd';
  const user = this.getUser(userId);
  await usar.sendMessage(message);
}
```

Very obvious. Let's try this again when our names don't visually align.

```javascript
async function sendMessageToUser(userId, message) {
  let user = this.getUser('abcd');
  const result = usar.sendMessage(message);
  await result;
}
```

Quite hard to spot.

Now, don't go change your `const` to `let` if it doesn't make sense. But when you get the chance, align variables to make your code simpler to read.

```javascript
async function sendMessageToUser(userId, message) {
  const userId = 'abcd';
  const user = this.getUser(userId);
  if ( !user ) throw new Error('Unknown User');
  await user.sendMessage(message);
```
