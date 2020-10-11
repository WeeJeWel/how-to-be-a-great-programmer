# The Abstraction Prison

It's tempting to create beautiful code with a lot of generic abstractions. Because in the future this will make you develop new features much faster, right?

You're usually wrong. Why? Because you don't know what the future brings.

Great code does its job in a way that's simple to read, and can be easily changed. Your code is never the end-goal (TODO: snippet) but a tool for another goal.

If your boss comes by your desk and tells you _"When we ship a box to Australia we need to charge one dollar extra."_ and your answer is _"Oof, well, that doesn't really fit in my abstraction."_ you are probably a terrible programmer. Your job was to create code that executes business logic, and business logic changes more often than Google kills any of their products.

Why didn't you create code where you can simply write:

```javascript
// Add one dollar because my boss told me to
if( country === 'AU' )
  price = price + 1;
```

Because these things _will_ happen so you'd better be prepared.

Don't lock yourself up in a prison of abstraction. Just [keep it simple](keep-it-simple.md).
