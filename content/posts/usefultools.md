---
author: "Marius"
title: "External tools to help you during development"
url: "/posts/tips-to-speed-up-your-Mendix-development"
date: "2021-10-14"
description: "Pro tips for leveling up your development game"
tags: ["Mendix", "Development", "Tips", "Guide"]
credits: 
    author: 
    url: ""
    text: 
cover:
  image: "/posts/images/toptipsheader.jpg"
  alt: "Hero image for top tips for speeding up your Mendix development"
draft: true
---

### 7. Use Prettier for automatic file formatting

If you have experience writing custom styling, you are probably familiar with CSS indentation formatting. There are many ways you can automate this. I use the Visual Studio Code extension [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to automatically format my SCSS whenever I save a file.

                //From this
                .class{background:red}

                //To this!
                .class {
                    background: red;
                }

> _You can even customize the formatting rules on a per-project basis, using a Prettier [configuration file](https://prettier.io/docs/en/configuration.html)!_

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

### 9. Use JavaScript bookmarklets

Since every action is available through the JavaScript API, we can take this one step further. Most modern browser offer the option to save JavaScript snippets in your bookmarks called [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet).
Bookmarking a JavaScript function allows you to call it with a single mouse press directly from your browser. The possibilities are endless: logging in, opening a page, executing a microflow...

##### Log out of any Mendix application instantly by clicking a bookmark on your toolbar:

```
javascript:(function()%7Bmx.logout()%3B%7D)()%3B
```

##### Log in to your Mendix app with the provided username and password ("MxAdmin" with password "1" in this example):

```
javascript:(function()%7Bmx.login(%22MxAdmin%22%2C%20%221%22)%3B%7D)()%3B
```

> _I use this [bookmarklet maker](https://caiorss.github.io/bookmarklet-maker/) to generate bookmarklets from my JavaScript snippets._

### 10. TortoiseSVN

Mendix uses Subversion (SVN) for version management. Most of the things you need for this are included in Studio Pro, but you can download [TortoiseSVN](https://tortoisesvn.net/) to get some additional functionalities. 

With TortoiseSVN, you can:

- Update to a specific revision, for instance to compare changes between commits
- Rename and archive branches
- Resolve merge issues that occurred outside of Studio Pro
- Update and commit without having to open Studio Pro
- Add items to the ignore list

> _Make sure you check which TortoiseSVN version you need for your Studio Pro version_


---

Are you missing some Pro Tips that you use in this blog post? Let me know!

### PowerToys

### Chocolatey