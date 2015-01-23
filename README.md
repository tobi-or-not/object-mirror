# Mirroring Javascript Objects
I attempted to sort values that can be `null` or `undefined` mixed with other JS data types. Unfortunately using `<` or `>` always returns false, which makes it impossible to get a stable search result. 

```
'test' > undefined --> false
'test' < undefined --> false
```
Thus, the idea was to compare the a `String`, for example, to a fresh instance of the same type. Creating this fresh instance is exactly what the mirror function does.

```
var objectOfSameType = function(blueprint) {
  var type = Object.prototype.toString.call(blueprint).split(' ')[1];
  return  this[type.slice(0, type.length - 1)]();
};
```

This html file is a test setup to check the behavior across browsers and platforms.
