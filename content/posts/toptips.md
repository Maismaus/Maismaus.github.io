---
author: "Marius"
title: "tips you wish you knew earlier to speed up your Mendix development"
url: "/posts/tips-to-speed-up-your-Mendix-development"
date: "2021-10-14"
description: "Pro tips"
tags: ["Mendix", "Development"]
---

As a Mendix developer, you are likely working with Studio Pro every day. However, there are many simple tricks that you can use in your day to day work that make your life a little bit easier. In this blog post, I will go over some of the pro tips that I have gathered during my time as a Mendix developer.

### 1. Use the JavaScript api 
Mendix uses the JavaScript API to send actions to the server. Did you know you can use this API to perform any action you could normally perform through the web page? 
This could help you out if you need to quickly retrieve some objects but you don't have pages set up for this.

                mx.data.get({
                    xpath: "//System.User",
                    callback: function(objs) {
                        console.log("Received " + objs.length + " MxObjects");
                    }
                });

> *Mendix also offers [documentation](https://apidocs.rnd.mendix.com/9/client/) for using the JavaScript API*

### 1. Use JavaScript bookmarklets
Mx.logout(), Mx.login(username,password), DevMenu
Since every action is available through the JavaScript API, we can take this one step further. Most modern browser offer the option to save JavaScript snippets in your bookmarks called [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet).
Bookmarking a JavaScript function allows you to call it with a single mouse press directly from your browser!

Use this bookmarklet to log out from any Mendix application:

                    javascript:(function()%7Bmx.logout()%3B%7D)()%3B

> *I use this [bookmarklet maker](https://caiorss.github.io/bookmarklet-maker/) to generate bookmarklets from my JavaScript snippets.*

### 2. Use dissolve container to quickly remove a container

### 3. Use inline snippet to dissolve a snippet

### 4. Imitate the Mendix DOM rendering for widget customizations

### 5. Use Prettier for automatic file formatting
If you have experience writing custom styling, you are probably familiar with CSS indentation formatting. There are many ways you can automate this. I use the Visual Studio Code extension [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to automatically format my SCSS whenever I save a file.
                
                //From this
                .class{background:red}

                //To this!
                .class {
                    background: red;
                }

> *You can even customize the formatting rules on a per-project basis, using a Prettier [configuration file](https://prettier.io/docs/en/configuration.html)!*

### 6. Use FontAwesome to override glyphicons

### 7. Use set as return value to quickly configure the return value

### 8. Drag and drop

#### 8.1  microflows into subflow calls to replace them
#### 8.2 Datasource flows into dataviews
#### 8.3 Microflows into action buttons
#### 8.4 Connector items into data views