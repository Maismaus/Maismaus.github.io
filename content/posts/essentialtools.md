---
title: 10 Essential Tools for Mendix App Development
description: Tools for Mendix developers you won’t be able to do without
author: "Marius"
url: "/blog/10-essential-tools-for-Mendix-development"
date: "2022-05-25T09:54:40.816Z"
tags: ["Tips & tricks", "Recommended software"]
cover:
   image: "/posts/images/essentialtools/header.webp"
   alt: "10 Essential Tools for Mendix App Development"

ShowReadingTime: true
hidemeta: false
showtoc: false
---

No matter what you do for a living, making sure you have the right tools for the job is essential for any working professional. Mendix Studio Pro is a great piece of software to build apps with, but there are a plethora of other tools that can help you build apps more efficiently than ever before. In this article, I go over my recommendations for must-have tools for everyday use in Mendix development.

### 1\. Use Prettier for automatic file formatting

If you have experience writing custom styling, you are probably familiar with CSS indentation formatting. Did you know there are easy ways to automate this? I use the Visual Studio Code extension [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) to automatically format my SCSS whenever I save a file.

![Instant automatic indentation using Prettier.](/posts/images/essentialtools/prettier.webp)

> You can even customize the formatting rules on a per-project basis, using a Prettier [configuration file](https://prettier.io/docs/en/configuration.html)! This way, you can ensure that everyone on your team uses the same formatting.

### 2\. Extend Mendix Version Control by installing TortoiseSVN

Mendix uses Subversion (SVN) for version management. Most of the things you need for this are included under the Version Control menu item in Studio Pro, but you can download [TortoiseSVN](https://tortoisesvn.net/) to get some additional functionalities.

With TortoiseSVN, you can:

-  Update to a specific revision, for instance, to compare changes between commits.
-  Rename and archive branches.
-  Resolve merge issues that occurred outside of Studio Pro.
-  Update and commit without having to open Studio Pro.
-  Add items to the ignore list, preventing merge conflicts for compiled files.

> Make sure you check which TortoiseSVN version you need for your Studio Pro version.

![Revert back to a specific revision using TortoiseSVN.](/posts/images/essentialtools/tortoisesvn.webp)

### 3\. Enhance your browser with bookmarklets

Mendix offers a JavaScript API that you can use to your advantage. Most modern browsers offer the option to save JavaScript snippets in your bookmarks called [bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet).

Bookmarking a JavaScript function allows you to call it with a single mouse click directly from your browser. The possibilities are endless: logging in, opening a page, executing a microflow… You can bookmark any function that you use regularly during app development.

#### _Log out of any Mendix application instantly by clicking a bookmark on your toolbar_

`javascript:(function()%7Bmx.logout()%3B%7D)()%3B`

> I use this [bookmarklet maker](https://caiorss.github.io/bookmarklet-maker/) to generate bookmarklets from my JavaScript snippets.

![Bookmark JavaScript snippets to quickly use JavaScript functions in your Mendix app.](/posts/images/essentialtools/bookmarklet.webp)

### 4\. Squeeze more efficiency out of Windows using PowerToys

If you’ve ever used a MacBook before, I’m sure you miss the Spotlight feature after switching to Windows. Did you know Microsoft offers this — and more — with PowerToys? For instance, it adds functionality in File Explorer to preview `.svg` and `.md` files, a right-click image resizer, and a nifty color picker. A must-have for anyone using Windows on a daily basis!

![The PowerToys Run window, one of the many useful features included in the package.](/posts/images/essentialtools/powertoys.webp)

### 5\. Automate your installation process with Chocolatey

Again, if you used a MacBook in the past, you’ve probably heard of Homebrew. There is a Windows equivalent called Chocolatey. Chocolatey is a package manager for Windows that allows you to search for and install software right from the command prompt.

To illustrate, let me give you an example. I’m sure you are familiar with the traditional method of installing new software. It goes something like this:

-  Open browser
-  Search for software
-  Load the website
-  Navigate to the download page
-  Find the correct version
-  Download installer
-  Open the installer
-  Go through the installation wizard
-  Done

With Chocolatey, you can:

-  Open command prompt
-  Enter `choco install PowerToys -y`
-  Done

> Sounds good? That’s because it is! Now let’s get Mendix Studio Pro available in Chocolatey by **upvoting my** [**idea**](https://forum.mendix.com/link/ideas/2645) on the forum.

![What installing software looks like using Chocolatey.](/posts/images/essentialtools/chocolatey.webp)

### 6\. Use the built-in Windows Snipping Tool to capture parts of your screen

Got a problem that you want to visualize? Use the Snipping Tool to capture parts of your screen in a screenshot. That way, you can keep your screenshots focused on the exact item that you want to share instead of sharing your entire screen. Simply press `⊞ Win + Shift + S` and drag to select the part of the screen you want to capture.

![Quick and easy partial screen capture using the Snipping Tool.](/posts/images/essentialtools/snippingtool.webp)

### 7\. Improve your integration testing with Postman

One of Mendix’s strengths is its ability to integrate with many other systems. Integrations are a key part of many Mendix applications. However, troubleshooting a connection from within Mendix is often a hassle because of the configuration required to set it up. You can use Postman instead to perform web service calls to and from Mendix.

Postman also offers a collection runner, where you can configure a number of web service requests in a specific order. You can use this on top of unit tests for test automation:

![Run requests in sequence from Postman to test your entire app’s integration suite.](/posts/images/essentialtools/postman.webp)

> I’m working on a blogpost about **automated Mendixcloud deployments from Postman**. Follow me on [LinkedIn](https://www.linkedin.com/in/mariusvanderknaap/) to be the first to hear about it!

### 8\. Run a local mail server using FakeSMTP

Configuring an external e-mail server to work locally can be a nuisance. You might not have an internet connection, configuration settings change or you don’t want to have to reconfigure the e-mail server every time you switch databases locally. For these scenarios, [FakeSMTP](http://nilhcem.com/FakeSMTP/) is a perfect solution. This lightweight Java package will run a local e-mail server that you can connect to in seconds. Because it is written in Java, you can use it on any operating system too!

![Run a local mail server with FakeSMTP.](/posts/images/essentialtools/fakesmtp.webp)

### 9\. Use Fiddler to analyze incoming and outgoing traffic

If you want to have more insight into what data is coming in and going out, Fiddler is a must-have tool. You can route all internet traffic through Fiddler to analyze in detail what requests are being made between your computer and external servers. Make sure to configure the Fiddler port as a proxy in your Mendix project settings so all traffic is properly routed through it!

![Investigate incoming and outgoing traffic with Fiddler.](/posts/images/essentialtools/fiddler.webp)

### 10\. Slack

Did you know there is an entire Mendix community available on Slack? This active community can help you out with problems. **Find the Mendix Slack community** [**here**](https://mendixcommunity.slack.com/)**!**

![Slack logo.](/posts/images/essentialtools/slack.webp)
