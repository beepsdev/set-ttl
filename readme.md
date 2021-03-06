# set-ttl
[![Run tests](https://github.com/beepsdev/set-ttl/actions/workflows/tests.yml/badge.svg)](https://github.com/beepsdev/set-ttl/actions/workflows/tests.yml)

A Simple module for allowing set entries to expire.

## Install
```
npm install --save set-ttl
```

## Run tests
Tests are made with Jest. You'll need to install dev-dependencies.
```
npm test
```

## Example Usage
```js
const SetTTL = require('set-ttl');

// Create cache with a TTL of 500ms
let cache = new SetTTL(500);

// Add a value to the set, TTL is not specified so the default is used.
cache.add('example');

// Check the contents of "example" after 250ms
setTimeout( ()=> {
    console.log('Should be true: ', cache.has('example'));
    cache.extend('example', 300); //Extends cached value TTL by 300ms
}, 250)

// After 1 second, the TTL should have expired and the item doesn't exist anymore
setTimeout( ()=> {
    console.log('Should be false: ', cache.has('example'));
}, 1000)
```

## Why?
I Wanted a simple way to keep track of keys and check when they have expired. I'm sure there are better solutions out there but I wanted to keep things simple.
Also, Some of the solutions I found used SetTimeout() or repeated a lot of unneeded checks which I wanted to avoid.

### Implemented for
`Set.prototype.size`
`Set.prototype.add(value)`
`Set.prototype.clear()`
`Set.prototype.delete(value)`
`Set.prototype.has(value)`
`Set.prototype.forEach(callbackFn, thisArg)`
