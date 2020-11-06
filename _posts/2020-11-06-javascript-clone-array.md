---
published: true
title: 'JavaScript - How to duplicate an array'
description: 'How to copy an array in JavaScript. How to clone an array in JavaScript. How to copy an array in TypeScript. Examples.'
date: 2020-11-06T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'javascript'
color: '#7AAB13'
permalink: /javascript-duplicate-array
categories:
  - JavaScript
tags:
  - JavaScript, Angular

introduction: 'How to copy or clone an array in JavaScript'
---

## Shallow and deep copy
<img src="/assets/img/uploads/2020/js_shallow_deep_copy.png" alt="shallow and deep copy"/>
Shallow copy: only the original array object is cloned, the original content is referenced by the new array.

Deep copy: the objects inside the original array are cloned. Useful when you want to work on a copy of the original data.


## Shallow copy
A shallow copy simply creates a new _array_ object with the same references to the objects of the original array.

<img src="/assets/img/uploads/2020/js_shallow_copy.png" alt="shallow copy"/>

If you update an object inside the cloned array, the original object will be updated.

### How to create a shallow copy

Here some examples, other methods are available (loop etc.):

```javascript
// spread operator
const newArraySpread = [... originalArray];

// slice
const newArraySlice = originalArray.slice();

// Array class
const newArrayFrom = Array.from(originalArray)
```

According to some benchmarks, `splice` should be the fastest method. You can test with your data in this online benchmark: [https://jsben.ch/lO6C5](https://jsben.ch/lO6C5)

## Deep copy
A deep copy clones the original array and his content to new objects.

There are no references with the original array. You can modify the content without an impact on the original data.


<img src="/assets/img/uploads/2020/js_deep_copy.png" alt="deep copy"/>

### How to create a deep copy

The 'easiest' method in JavaScript is to convert the array in JSON string and convert the JSON string in a new object.
```javascript
const newArray = JSON.parse(JSON.stringify(originalArray));
```

This method is the easiest because it avoids a custom implementation, but it can have issues with circular references and big arrays (performance).






