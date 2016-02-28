# Sync Code

## Overview

We've spent a lot of time in the beginning of Unit 1 talking about non-blocking input/output. It is great for performance, but sometimes you will need to write synchronous code in Node.

Yes, synchronous code might be useful. Imagine a situation where you read configurations from a file to boot up your system. Without the configurations, the system won't work. In this case, you don't want the asynchronous method. The synchronous method would be a better idea, because the system won't start without the configurations.

So although this unit is called non-blocking (and we'll cover asynchronous non-blocking code later), this this lesson will cover the synchronous code on the example of the `fs` module.

## Objectives

1. Illustrate sync code with `fs` file read method
1. Illustrate sync code with `fs` file write method

## Sync Expression

Consider an example in which we have a function and it return a sum of the values:

```js
function sum (a, b) {
  return a+b
}
```

This is a synchronous expression, because the function will return the value and the process will be blocked. By process being blocked, we mean that the control won't be delegated and other tasks cannot be performed. 

If the code is simple and fast as in the case of `a+b`, it's totally fine. Another example would be getting data from cache. This is fast compare to retrieving the data from a database.

In the synchronous code, we can assign the result of the expression to the variable:

```
function sum (a, b) {
  return a+b
}
var s = sum(1, 2)
console.log(s) // 3
```

So the advantages of synchronous code in Node are:

* It's easy to write and read because that's how most programming languages work and that's what taught in universities and schools
* It's ensures the correct sequence, e.g., `console.log(s)` will alway have the data because it's the last statement and `sum(1, 2) precedes it.

Typically, core Node modules will provide both synchronous and asynchronous methods when applicable so developers can pick the best tool. Let's zoom in on two such methods from `fs`.

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
