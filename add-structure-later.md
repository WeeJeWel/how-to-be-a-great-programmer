# Add structure later

When you're starting on a new project you never fully understand the problem until you've solved it once.

So it's generally a bad idea to put much time into structuring until your solution has been proven to work. If you have a great structure but your solution didn't work, you can throw away both the structure and solution. That's double wasted time.

I usually create a single `poc.js` file that does _everything_ I need to do to prove that something can work. For example, when I'm writing a C-header-to-JavaScript parser, everything goes into that single file, ideally from top to bottom.

Then it works! That's amazing, solution verified. Only now may I create some abstractions because _only now_ I know which parts occur more than once (ideally more than twice) and abstract them.

It's very hard to see the bigger picture when you haven't zoomed in on all parts yet.
