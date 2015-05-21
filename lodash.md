#Using lodash

##Introduction

This document is more on how to properly use lodash. We'll take advantage of lodash's [lazy evaluation](http://filimanjaro.com/blog/2014/introducing-lazy-evaluation/).

```javascript
// We'll use this variable on all examples below
var my_array = [
	{name: 'Raven', age: 21},
	{name: 'John', age: 20},
	{name: 'rvnjl', age: 22}
];
```

##Pattern
```javascript
// NOT like this:
_.forEach(my_array, function () {
  ...
});

// but like this:
_(my_array) // create a lodash wrapper instance from an array, string or object
  .forEach() or map, filter, etc. // do what you want to do
  ...
  .commit() or .value(); // execute the things you want to do
  
// *chainable
// *easier to read
// *easier to transition
```
.commit() and .value() will optimize the things you want to do then execute it.

##When to use `.value()` over `.commit()` and vice-versa.
###.value()
```javascript
my_array = _(my_array)
  .pluck('name')
  .value();
// ['Raven', 'John', 'rvnjl']
```
Use `.value()` when you need the last state of your variable like `.map`, `.filter`, `.reduce`, etc.

###.commit()
executes the things you want to do and then returns the lodash wrapper instance
```javascript
_(my_array)
  .forEach(function (item) {
    console.log(item);
  })
  .commit();
```
Use commit when the last state of your variable is not necessary like `.forEach`

##Read the documentation to know all the awesome functions lodash offers [here](https://lodash.com/docs)
