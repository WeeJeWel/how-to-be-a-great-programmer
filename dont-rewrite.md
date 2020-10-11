# Do not rewrite code if you do not understand the code.

I've seen many programmers rewrite a piece of code because they didn't understand the code. Code that isn't yours often feels old, dirty or whatever. So their first urge is to rewrite it "up to their standards". The end result is often not better, and usually worse. Why it this?

Writing code is easier than reading code, because when you write code, you _must_ have this abstract model in your mind where you can debug the code in your head. When you're reading code, however, it takes a long time to get to that same mental model. It's therefore easier to 'learn by doing' than 'learn by reading'.

So they start to rewrite the code to understand it, but they tell themselves they're making it better. But as is often with programming, the first 90% is easy and then your abstraction becomes your own prison (TODO: snippet).

But you don't know yet where your new abstraction will bite you. And the previous programmer does, becuse he's been there. So now you've _changed_ code but didn't make it _better_. Now, _you_ think it's better, but that's because only _now_ you understand the problem, and it took you writing code to get there!

The problem is, your code is not better, it's _different_. However, the previous programmer now must _read_ your code to understand it again. So you've just wasted someone's time because you were too lazy to sit down, hand behind your head and just fucking _read_ the code with an open mind.

_N.B. If you think rewriting code is a great way to understand architecture, that's fine. Just throw your new code away when you're done and resist the urge to make a PR._
