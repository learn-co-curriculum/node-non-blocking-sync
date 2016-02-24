# Sync Code

## Overview

So non-blocking input/output is great for performance. But how do you actually code in it? To understand non-blocking I/O and asynchronous code better, we shall start with synchronous code first.

Synchronous code might be useful. Imagine a situation where you read configurations from a file to boot up your system. Without the configurations, the system won't work. In this case, you don't want the asynchronous method. The synchronous method would be a better idea, because the system won't start without the configurations.

This lesson will cover the synchronous code on the example of the `fs` module.

## Objectives

1. Illustrate sync code with `fs` file read method
1. Illustrate sync code with `fs` file write method

## `fs.readFileSync()`

The method for reading file content has this usage:

```js
var content = fs.readFileSync(filename, options)
```

If you have console logs, then you can see that the process is blocked until the data `content` becomes available:

```js
console.log('Start reading file')
var content = fs.readFileSync(filename, options)
console.log('Finish reading file')
console.log(content)
```

The output will have "Start reading file" and "Finish reading file" in that order. The `content` variable will be defined for the `console.log(content)`.


## fs.writeFileSync()

The synchronous method for writing to a file has this usage:

```js
fs.writeFileSync(filename, content, options)
```

If we add console logs, the output will also has "Start reading file" and " Finish reading file"

```js
console.log('Start reading file')
fs.writeFileSync(filename, content, options)
console.log('Finish reading file')
```

---

<a href='https://learn.co/lessons/node-non-blocking-sync' data-visibility='hidden'>View this lesson on Learn.co</a>
