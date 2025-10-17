---
title: "The Mendix React Client Is Coming: Here’s What You Need to Know"
description: "Stay up to date on React to build future-proof applications"
author: "Marius"
url: "/blog/the-mendix-react-client-is-coming"
date: "2025-07-10"
tags: ["Mendix", "Development", "Tips", "Guide"]
cover:
   image: "/blog/images/reactclient/header.webp"
   alt: "Hero image for the Mendix React client"

ShowReadingTime: true
hidemeta: false
showtoc: false
---

The Dojo era
------------

For over a decade, Mendix used Dojo as a front-end client framework. Frameworks like Dojo save developers a lot of time by providing useful libraries out of the box.

Dojo was among the most popular JavaScript frameworks for many years. However, the JavaScript landscape evolves rapidly, and other libraries have surpassed Dojo by being faster, more comprehensive, and easier to use. One of these libraries is React, which quickly became one of the most popular JavaScript frameworks.

Mendix transitioned to using React and the Pluggable Widgets API as a preferred method for building custom widgets and steadily phased out Dojo widgets.

The main web client, however, is still based on Dojo. This eventually has to be replaced to move to a full React client.

The Mendix React Client
-----------------------

The React client is available from Mendix 10.7 and above. The React client offers several benefits:

*   It is faster
*   It allows incremental loading
*   It is future-proof

Before you can migrate to the React client, you cannot have any Dojo widgets in your project.

While migrating to React is not a necessity yet and won’t be for a while, knowing about its existence helps you build future-proof applications. Avoiding Dojo widgets now saves you from having to migrate them a year or two from now.

### **_So, what can you do?_**

There are some default Mendix widgets based on Dojo. These should be avoided, and their modern counterparts should be used instead.

*   Data Grid 1 ➡ DataGrid2
*   Reference Selectors & Drop-down ➡ Combo box
*   Dynamic & Static Image ➡ Image
*   Template Grid ➡ Gallery

> If your first thought is “…but Data Grid 2”, give the latest version another try. Mendix worked hard on these widgets and I can confidently say that they are now much better than their legacy counterparts.

Furthermore, make sure to follow these guidelines:

*   Whenever you add a new custom widget, make sure it is based on React.
*   Enable Migration mode to check existing widget compatibility.
*   For more information, read up on the [Mendix React Client](https://docs.mendix.com/refguide/mendix-client/react/) documentation.

### Final thoughts

While you don’t have to migrate all your existing widgets just yet, you shouldn’t introduce deprecated widgets to your projects anymore. This ensures that you build future-proof applications and prevents you from a lot of work in the future. Your future self will thank you!