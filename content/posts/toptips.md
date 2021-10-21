---
author: "Marius"
title: "Here's 8 tips you wish you knew earlier to speed up your Mendix development"
url: "/posts/tips-to-speed-up-your-Mendix-development"
date: "2021-10-14"
description: "Pro tips"
tags: ["Mendix", "Development", "Tips", "Guide"]
cover:
  image: "/posts/images/toptipsheader.png"
  alt: "Hero image for top tips for speeding up your Mendix development"
---

As a Mendix developer, you are likely working with Studio Pro every day. However, there are many simple tricks that you can use in your day to day work that make your life a little bit easier. In this blog post, I will go over some of the pro tips that I have gathered during my time as a Mendix developer.

### 1. Use the JavaScript api

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

### 2. Use JavaScript bookmarklets

Since every action is available through the JavaScript API, we can take this one step further. Most modern browser offer the option to save JavaScript snippets in your bookmarks called [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet).
Bookmarking a JavaScript function allows you to call it with a single mouse press directly from your browser. The possibilities are endless: logging in, opening a page, executing a microflow...

##### Log out of any Mendix application instantly:

```
javascript:(function()%7Bmx.logout()%3B%7D)()%3B
```

##### Log in to your Mendix app with the provided username and password ("MxAdmin" with password "1" in this example):

```
javascript:(function()%7Bmx.login(%22MxAdmin%22%2C%20%221%22)%3B%7D)()%3B
```

> _I use this [bookmarklet maker](https://caiorss.github.io/bookmarklet-maker/) to generate bookmarklets from my JavaScript snippets._

### 3. Use dissolve container to quickly remove a container

Got a container you don't need anymore, but you need to save the content within it? Stop dragging all items out of the container before deleting it! Simply right click the container and select `dissolve container` to remove the container but keep the content contained within it.

![Remove a container quickly by selecting dissolve container](/posts/images/toptipsdissolvecontainer.png)

### 4. Use inline snippet to dissolve a snippet

Similar to `dissolve container`, you can right click a snippet and select `inline snippet` to quickly put all snippet contents back on a page directly.

![Remove a snippet quickly by selecting inline snippet](/posts/images/toptipsinlinesnippet.png)

### 5. Use Prettier for automatic file formatting

If you have experience writing custom styling, you are probably familiar with CSS indentation formatting. There are many ways you can automate this. I use the Visual Studio Code extension [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to automatically format my SCSS whenever I save a file.

                //From this
                .class{background:red}

                //To this!
                .class {
                    background: red;
                }

> _You can even customize the formatting rules on a per-project basis, using a Prettier [configuration file](https://prettier.io/docs/en/configuration.html)!_

### 6. Use FontAwesome to override glyphicons

### 7. Use set as return value to quickly configure the return value

You can select the entity to return from a microflow by double clicking the End event, selecting the return Entity type and then entering a variable to return. However you can also right click an activity that contains a variable and press `Set as return value` to do all those things at once!

![Use set as return value to set the return type and return the selected object](/posts/images/toptipsreturnvalue.png)

### 8. Drag and drop

Drag and drop (also jokingly referred to as _sleur en pleur_ in Dutch 😉) is a pattern which is used often throughout Studio Pro. Did you know you can use it in many more instances than simply dragging activities into microflows?

#### Drag flows from the Explorer into Microflows

You can either drag a microflow into a blank area of a microflow to create a new Call Microflow activity, or onto an existing Call Microflow activity to replace the subflow with another.

#### Drag items from the Explorer into pages

You can drag most items from the Project Explorer into a page to add a widget to your page. You can drag them onto existing widgets or onto blank targets to create a new widget.

- Drag a microflow onto a button to set that microflow as the action
- Drag a page into a page view to insert a button linking to that page
- Drag a microflow onto a dataview to set that microflow as the datasource

> Microflows must return a list before you can drag them onto a listview

#### Drag connector items into data views to insert input widgets

If you have your selection inside a dataview, the connector tab will show you the attributes for the entity in that dataview. You can use the connector to drag any of those attributes into the dataview to instantly create an input widget for that attribute. No more scrolling through the Toolbox to find the correct widget, it automatically select the right type of input widget for that attribute!

### 9. Keyboard shortcuts

Ctrl + Enter
F5 F9
Ctrl + Space

### 10. TortoiseSVN
