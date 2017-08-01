---
layout: post
title: 'IndexedDB made easy with Dexie.js'
categories: [tech]
date: 2017-7-25
published: false
---

With the rise of single-page applications on the web, specifically using [React.js]() and the requirement for more application state than ever, a new challenge has arisen: how do we persist state once it becomes too big for the browser's simplistic [localStorage]()?

## The Problem
Any React app that's worth its salt will make use of a state manager such as [Redux]() or less commonly, [MobX](). The problem comes when we have large amounts of structured data which we require to allow our application to work as well offline as it does online.

If this were a small amount of JSON data, the first solution is of course the aforementioned localStorage, but when we look at the limitations of local/sessionStorage, there's a cap, set by the browser, of 10MB.

## The Solution
Luckily, the browser provides a database which allows us to store over 50MB of data, called IndexedDB.
> "IndexedDB is a low-level API for client-side storage of significant amounts of structured data, including files/blobs. This API uses indexes to enable high-performance searches of this data. While Web Storage is useful for storing smaller amounts of data, it is less useful for storing larger amounts of structured data. IndexedDB provides a solution." **- MDN**

...Sounds great, we'll use that.

## The IndexedDB API
Great, we've found a solution that'll store more than 10MB of application state!

Don't celebrate too much just yet. Let's take a look at the IDB API for fetching a todo:

- Show how to set up IDB? Long... Could just say after setting up an object store.

```javascript
function someApiExample() {
  return new Promise(function(resolve, reject) {
    resolve({ some: 'data' });
  });
}
```

The way IndexedDB works is it allows querying by the primary key or using an index which can be defined on a table, or "store" in IDB.

...Mozilla weren't kidding when they said 'low-level'!

For developers who are used to working with the JavaScript [Promise]() API and/or [async/await]() ...or really any other form of modern JavaScript, this just looks like more trouble than it's worth.

Luckily, IDB allows for query languages to be layered on top of its API, and that's where [Dexie]() comes in. Dexie works as an [Object Relational Mapper (ORM)](), hiding the nitty gritty of IndexedDB from us.

## Dexie.js
- Far less code complexity
- Maintainers won't cry
- Multi index support is poor
- Can't query very well on multiple indexes, .filter can be used - unsure of performance hit here.
