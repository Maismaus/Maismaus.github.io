---
title: JavaScript Bookmarks
description: Mendix JavaScript Bookmarks
url: "/docs/jsdoc/javascriptbookmarks"

showtoc: true
disableShare: true
hidemeta: true
---

This section describes various bookmarklets that you can use in the bookmarks toolbar. They contain various JavaScript functions for easy access.


### Login

Login as a user. Currently set up with user MxAdmin and password 1.

```
javascript:(function()%7Bvar xhr %3D new XMLHttpRequest()%3B%0Axhr.open("POST"%2C location.origin %2B "%2Fxas%2F"%2C true)%3B%0Axhr.setRequestHeader("Content-Type"%2C "application%2Fjson")%3B%0Axhr.send(%0AJSON.stringify(%7B%0A        action%3A "login"%2C%0A        params%3A %7B%0A            username%3A "MxAdmin"%2C%0A            password%3A "1"%2C%0A        %7D%2C%0A    %7D)%0A)%3B%0Axhr.onreadystatechange %3D function () %7B%0A    window.location %3D "index.html"%3B%0A%7D%3B%7D)()%3B
```

### Logout

Logout as current user.

```
javascript:mx.logout();
```


#### Session bookmarklet

Remove all sessions (if you have access rights to it).

```
javascript:(function()%7Bmx.data.get(%7Bxpath%3A%20%22%2F%2FSystem.Session%22%2Ccallback%3A%20function%20(session)%20%7Bvar%20sessionArray%20%3D%20%5B%5D%3Bfor%20(var%20i%20%3D%200%3B%20i%20%3C%20session.length%3B%20i%2B%2B)%20%7BsessionArray.push(session%5Bi%5D._guid)%3B%7Dmx.data.remove(%7Bguids%3A%20sessionArray%2Ccallback%3A%20function%20()%20%7Bconsole.log(toString(session.length)%20%2B%20%22sessions%20removed%22)%3B%7D%2Cerror%3A%20function%20(e)%20%7Bconsole.log(%22Could%20not%20remove%20objects%3A%22%2C%20e)%3B%7D%7D)%3B%7D%7D)%7D)()

```

###

Go to index.html

```
javascript:void(window.location.href = '/index.html');
```

### Show current page details

Shows the currently module and pagename in a JavaScript alert.

```
javascript:(function()%7Bjavascript%3A(function()%7Bvar pageTitle%3Dmx.ui.getContentForm().path.replace(".page.xml"%2C"")%3Bvar pageTitleArr%3DpageTitle.split("%2F")%3Bvar moduleName%3DpageTitleArr%5B0%5D%3Bvar pageName%3DpageTitleArr%5B1%5D%3Bprompt("Module%3A"%2BmoduleName%2CpageName)%3B%7D)()%3B%7D)()%3B
```