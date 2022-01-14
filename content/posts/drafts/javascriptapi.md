---
author: "Marius"
title: "Using the JavaScript API in Mendix"
url: "/posts/javascript-api-guide"
date: "2022-01-01"
description: "Must-have tools for Mendix developers"
tags: ["Mendix", "Development", "Tips", "Guide"]
credits: 
    author: "JSapi"
    url: "https://unsplash.com/@carlevarino?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
    text: "Hero image by"
cover:
  image: "/posts/images/usefultools/header.jpg"
  alt: "Hero image for top tips for speeding up your Mendix development"
draft: true
---

### 8. Use the JavaScript api

Mendix uses the JavaScript API to send actions to the server. Did you know you can use this API to perform any action you could normally perform through the web page?
This could help you out if you need to quickly retrieve some objects but you don't have pages set up for this.

```
mx.data.get({
    xpath: "//System.User",
    callback: function(objs) {
        console.log("Received " + objs.length + " MxObjects");
    }
});
```
> _Mendix also offers [documentation](https://apidocs.rnd.mendix.com/9/client/) for using the JavaScript API. I might write a full blogpost about the Mendix JavaScript API later, so keep a look out!_