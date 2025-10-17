---
title: "Mastering Mendix Maps: Unlocking Lightning-Fast Performance"
description: "You probably know what a list is. But do you?"
author: "Marius"
url: "/blog/mastering-mendix-maps"
date: "2023-10-19"
tags: ["Mendix", "Development", "Tips", "Guide", "Java"]
cover:
   image: "header.webp"
   alt: "Hero image for the Mastering Mendix Maps guide"

ShowReadingTime: true
hidemeta: false
showtoc: false
---

Creating lists in Mendix is one of its core features. You can use lists for looping over objects. Lists can improve performance by batch-committing objects. Aggregation functions can perform calculations and summations on your list, making them an integral part of any Mendix applications. However, as lists grow larger, they start to become **_SLOW_**_._

You might wonder why.

**Mendix is based on Java**. This means that most of what you create in Mendix is translated into Java code. **When you create a Mendix list, you’re essentially creating an ArrayList**. ArrayLists are convenient because they’re flexible. They allow you to add objects to it on the fly without requiring you to pre-allocate memory. ArrayLists support a wide range of operations, including insertion, removal, and retrieval of elements, making them versatile data structures for managing collections of objects. Of course, Mendix handles all of this in the background.

An ArrayList is constructed by indexing objects in the list, and they are indexed in chronological order. Retrieving objects through the index (“get the 10th object in the list”) is fast. However, searching for an entry with a specific value is slow because it has no index on list values. This means that for `find` operations, Mendix has to loop over each list item, and search time grows linearly with list size.

How a Single Trick Can Improve Performance
------------------------------------------

Java offers numerous interfaces for creating collections of objects, and **one of them is the Map**. A Map differs from Lists in several aspects. Most importantly, a Map is a collection of `Key-Value` pairs. The `Key` serves as a unique identifier associated with a `Value`. Maps are indexed on `Key` values, making retrieval using `Key` lightning fast.

### What Does This Mean in Practice?

Let’s say you’re doing a migration for a large financial institution. They have a CSV sheet containing transactions with an attribute CustomerID. You have a Mendix app with their Customers already, and you want to import the transactions and link them to a customer based on the CustomerID.

![Example domain model setup](/1.webp)

In traditional Mendix, this might look something like this:

![Mapping Transactions to Customers using database retrieval](/2.webp)

In this example, the client has 10,000 customers and 100,000 transactions that need to be linked to a customer. Mapping using a database retrieval took **213 seconds**. Alternatively, we can try retrieving the list of customers and use a `find` operation:

![Mapping Transactions to Customers using a find operation](/3.webp)

With the list `find` method, this took **75 seconds**.

With a Map, this was done in **3.5 seconds**. A **20x increase in performance**! So what kind of magic is going on behind the scenes here?

**Let’s Dive into Some Code!**

We begin by building a Map of `Key-Value` pairs and store it in the Context so that we have access to it during the current microflow, but gets garbage collected when the microflow is finished. The `Key` contains our CustomerID so we can find the Customer. The `Value` contains our Mendix Customer object. The Java action retrieves all Customer objects from the database and turns them into a Map.

```
IContext context = getContext();
context.getData().remove(ObjectMapType);
Map<Object, IMendixObject> objectMap = new HashMap<>();
List<IMendixObject> objectList = XPath.create(context, ObjectMapType).all();
for (IMendixObject mxObject : objectList) {
   objectMap.put(mxObject.getValue(context, ObjectKey), mxObject);
}
context.getData().put(ObjectMapType, objectMap);
```

When we want to find a Customer, we can retrieve it from the Map using its `Key` value:

```
@SuppressWarnings("unchecked")
Map<Object, IMendixObject> objectMap = (Map<Object, IMendixObject>) getContext().getData().get(ObjectMapType);
if (objectMap.isEmpty()) {
   Core.getLogger("ObjectMap").info("No object map found for map type " + ObjectMapType);
   return null;   
}
IMendixObject resultObject = objectMap.get(KeyValue);
if(resultObject != null) {
   return resultObject;
}
Core.getLogger("ObjectMap").debug("No object found for key " + KeyValue);
return null;
```

Our resulting microflow in Mendix is very similar to the `find` operation, with some actions replaced by our custom Java actions:

![Object mapping using custom Java actions](/4.webp)

You can find the ready-to-use Java actions [here](https://github.com/Maismaus/Maismaus.github.io/tree/main/content/blog/public).

When (Not) to Use This
----------------------

**Don’t use Maps when you have a list of just a few hundred objects**. The performance gains only start to become noticeable when dealing with tens of thousands of objects. **The larger the number of objects in your list, the greater the performance gains**. This means a theoretically infinite performance enhancement! _(as long as your server memory allows for storing the Maps, of course)._

### Pros

*   Lightning-fast retrieval of objects.
*   Easy to set up.

### Cons

*   Additional startup time is required for setting up the Map.
*   Less flexible than normal Lists.
*   Java knowledge is required for extending functionality.

Final Thoughts
--------------

While Mendix is a low-code platform, it’s crucial to understand that ultimately, everything is still code. Realizing and embracing this fact is essential for developing advanced modeling techniques.

There are many further optimizations possible in the solution described here. My code stores the entire Mendix objects as values in the created map. This is useful because we can return the objects directly from the Java action but has a negative impact on performance and memory usage. In my tests, storing GUIDs instead of Mendix objects doubled the performance of the Map. However, as modeling with GUIDs is more complex, I chose to explain only the basic solution.