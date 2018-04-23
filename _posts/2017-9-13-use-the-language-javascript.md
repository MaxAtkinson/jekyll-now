---
layout: post
title: 'JavaScript: Use The Language!'
categories: [tech]
date: 2017-7-25
published: false
---

This post covers:
- [Map](#map)
- [Filter](#filter)
- [Reduce](#reduce)

In a language like JavaScript, there are endless ways to achieve solutions to problems. But there are elegant ways and there are not so elegant ways.

In JavaScript, there are a lot of built-in functions which can help in limiting the amount of boilerplate code being written and overall lead to a more succinct, pretty and readable solution.

Let's say we've a bunch of JSON data:
```javascript
const people = [
  {
    name: 'Meech',
    age: 27
  },
  {
    name: 'Juice',
    age: 14
  },
  {
    name: 'Erick',
    age: 18
  }
];
```

## Example 1: Map

Let's say we want to get a list of the names in our people dataset. Someone new to JavaScript might do something like the following:

```javascript
const names = [];

for (let i=0; i<people.length; i++) {
  names.push(people[i]);
}
```

... Or ...

```javascript
const names = [];

people.forEach((person) => names.push(person.name));
```

### The ideal solution

Ideally, we want to use `Array.prototype.map` in this scenario.

`Map` takes one argument, a function which is called on each item in the array and returns some new value: the value that the current item should be "mapped" on to.

In this scenario, we could use map as follows:

```javascript
const names = people.map((person) => person.name);

=> ['Meech', 'Juice', 'Erick']
```

This example shows how to extract a property from a list of objects using map, but it can also be used to attach properties to these items under some condition:

```javascript
const mappedPeople = people.map((person, index) => {
  person.isEven = (index % 2 === 0);
});

=> [
  {
    name: 'Meech',
    age: 27,
    isEven: true
  },
  {
    name: 'Juice',
    age: 14,
    isEven: false
  },
  {
    name: 'Erick',
    age: 18,
    isEven: true
  }
]
```

The current index is also passed to the callback by map as you can see.
