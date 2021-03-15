---
title:  Recursively-Cleaning Parameters
permalink: self-cleaning-parameters
subtitle: Kind of like overloading functions
---

One of the best ways I know to learn idiomatic patterns for programming is to read the source of libraries written by people who know what they're doing. I do this every now and again and go spelunking for tips. I spotted this in [page.js](https://github.com/visionmedia/page.js):

```javascript
function page(path, fn) {
  // <callback>
  if ('function' === typeof path) {
    return page('*', path);
  }
```

As in, if instead of a path and a callback the function is passed a callback and nothing else, we assume they meant to use the * path with the callback they passed. The function arranges the arguments into the right order, and calls itself. I call this pattern recursively-cleaning parameters.

_Sitenote: this is friendly API design. It's effectively overloading a function, which isn't supported natively in JavaScript._

That example could have just as easily looked like this:

```javascript
function page(path, fn) {
  // <callback>
  if ('function' === typeof path) {
    fn = path;
    path = '*';
  }
```

which is a lot less tidy. Plus, if the function accepted more parameters, it would just get dirtier and dirtier from there. Cool!
