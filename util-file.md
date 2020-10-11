# Create a Util-file

To avoid leftpad-type dependencies, I almost always create a Util.js class with various static methods that are useful. It prevents me from searching for a package for trivial one-function problems.

```javascript
module.exports = class Util {

  static async wait(delay) {
    return new Promise(resolve => setTimeout(resolve, delay));
  }

}
```
