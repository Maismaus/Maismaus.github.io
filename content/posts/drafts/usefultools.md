---
author: "Marius"
title: "Essential tools for Mendix app development"
url: "/posts/Mendix-tools-for-development"
date: "2022-01-01"
description: "Tools for Mendix developers you can't do without"
tags: ["Mendix", "Development", "Tips", "Guide"]
credits: 
 author: "Cesar Carlevarino Aragon"
 url: "https://unsplash.com/@carlevarino?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
 text: "Hero image by"
cover:
  image: "/posts/images/usefultools/header.jpg"
  alt: "Hero image for must-have tools for Mendix app development"
draft: true
---

If you're working on Mendix apps on a daily basis, you better make sure you have the right tools to work with. Mendix Studio Pro is a great platform to build apps with, but there are many external tools that will help you build apps quicker than ever before. In this article, I will go over my recommendations for must-have tools for everyday use. 

### 1. Use Prettier for automatic file formatting
If you have experience writing custom styling, you are probably familiar with CSS indentation formatting. Did you know there are easy ways to automate this? I use the Visual Studio Code extension [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to automatically format my SCSS whenever I save a file.

```
//From this...
.class{background:red}

//To this! 👇
.class {
    background: red;
}
```

> _You can even customize the formatting rules on a per-project basis, using a Prettier [configuration file](https://prettier.io/docs/en/configuration.html)! This way, you can ensure that everyone on your team uses the same formatting._

### 2. Extend Mendix Version Control by installing TortoiseSVN

Mendix uses Subversion (SVN) for version management. Most of the things you need for this are included under the Version Control menu item in Studio Pro, but you can download [TortoiseSVN](https://tortoisesvn.net/) to get some additional functionalities. 

With TortoiseSVN, you can:

- Update to a specific revision, for instance to compare changes between commits.
- Rename and archive branches.
- Resolve merge issues that occurred outside of Studio Pro.
- Update and commit without having to open Studio Pro.
- Add items to the ignore list, preventing merge conflicts for compiled files.

> _Make sure you check which TortoiseSVN version you need for your Studio Pro version_

![Revert back to a specific revision using TortoiseSVN](/posts/images/usefultools/tortoisesvn-sm.png)
*Revert back to a specific revision using TortoiseSVN*

### 3. Enhance your browser with bookmarklets

Mendix offers a JavaScript API that you can use to your advantage. Most modern browser offer the option to save JavaScript snippets in your bookmarks called [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet).
Bookmarking a JavaScript function allows you to call it with a single mouse click directly from your browser. The possibilities are endless: logging in, opening a page, executing a microflow... You can bookmark any function that you use regularly during app development. 

##### Log out of any Mendix application instantly by clicking a bookmark on your toolbar:

```
javascript:(function()%7Bmx.logout()%3B%7D)()%3B
```

##### Log in to your Mendix app with the provided username and password ("MxAdmin" with password "1" in this example):

```
javascript:(function()%7Bmx.login(%22MxAdmin%22%2C%20%221%22)%3B%7D)()%3B
```
> _I use this [bookmarklet maker](https://caiorss.github.io/bookmarklet-maker/) to generate bookmarklets from my JavaScript snippets._

![Bookmarklet example](/posts/images/usefultools/bookmarklet.png)
*Bookmark JavaScript snippets to quickly use JavaScript functions in your Mendix app*

### 4. Squeeze more efficiency out of Windows using PowerToys

If you've ever used a MacBook before, I'm sure you miss the Spotlight feature after switching to Windows. Did you know Microsoft offers this —and more— with PowerToys? For instance, it adds functionality in File Explorer to preview .svg and .md files, a right-click image resizer, and a nifty color picker. A must-have for anyone using Windows 10 on a daily basis!

![PowerToys logo](/posts/images/usefultools/powertoys-sm.png)
*The PowerToys Run window, one of the many useful features included in the package*

### 5. Automate your installation process with Chocolatey

Again, if you used a MacBook in the past, you've probably heard of Homebrew. There is a Windows equivalent called Chocolatey. Chocolatey is a package manager for Windows that allows you to search for and install software right from the command prompt. 

To illustrate, let me give you an example. I'm sure you are familiar with the traditional method of installing new software. It goes something like this:

* Open browser
* Search for software
* Load the website
* Navigate to the download page
* Find the correct version
* Download installer
* Open the installer
* Go through the installation wizard
* Done

With Chocolatey, you can:

* Open command prompt
* Enter `choco install PowerToys -y`
* Done

> _Sounds good? That's because it is! Now let's get Mendix Studio Pro available in Chocolatey by upvoting my [idea](https://forum.mendix.com/link/ideas/2645) on the forum._

![What installing software looks like using Chocolatey](/posts/images/usefultools/chocolatey.png)
*What installing software looks like using Chocolatey*

### 6. Use the Windows 10 built-in Snipping Tool to capture parts of your screen

Got a problem that you want to visualize? Use the Snipping Tool to capture parts of your screen in a screenshot. That way, you can keep your screenshots focused on the exact item that you want to share instead of sharing your entire screen. Simply press `⊞ Win + Shift + S` and drag to select the part of the screen you want to capture.

![Quick and easy partial screen capture using the Snipping Tool](/posts/images/usefultools/snippingtool-sm.png)
*Quick and easy partial screen capture using the Snipping Tool*

### 7. Improve your integration testing with Postman

One of Mendix's strengths is its ability to integrate with many other systems. Integrations are a key part of many Mendix applications. However, troubleshooting a connection from within Mendix is often a hassle, because of the configuration required to set it up. You can use Postman instead to perform webservice calls to and from Mendix. 

Postman also offers a collection runner, where you can configure a number of webservice requests in a specific order. You can use this on top of unit tests for test automation.

![Postman logo](/posts/images/usefultools/postman-sm.png)
*Run requests in sequence from Postman to test your entire app's integration suite*

### 8. Run a local mail server using FakeSMTP

Configuring an external e-mail server to work locally can be a nuisance. You might not have an internet connection, configuration settings could change or you don't want to have to reconfigure the e-mail server every time you switch databases locally. For these scenarios, [FakeSMTP](http://nilhcem.com/FakeSMTP/) is a perfect solution. This lightwight Java package will run a local e-mail server that you can connect to in seconds. Because it is written in Java, you can use it on any operating system too!

![FakeSMTP logo](/posts/images/usefultools/fakesmtp-sm.png)
*Run a local mail server with FakeSMTP*

### 9. Use Fiddler to analyze incoming & outgoing traffic

If you want to have more insight into what data is coming in and going out, Fiddler is a must-have tool. You can route all internet traffic through Fiddler to analyze in detail what requests are being made between your computer and external servers. Make sure to configure the Fiddler port as a proxy in your Mendix project settings so all traffic is properly routed through it!

![Fiddler logo](/posts/images/usefultools/fiddler.png)
*Investigate incoming and outgoing traffic with Fiddler*

### 10. Slack

Did you know there is an entire Mendix community available on Slack? This active community can help you out with problems. Find the Mendix Slack community [here](https://mendixcommunity.slack.com/)!

[![Slack logo](/posts/images/usefultools/slack.png)](https://mendixcommunity.slack.com/)

---

Which software do you use on top of Mendix Studio Pro? Let me know in the comments!
