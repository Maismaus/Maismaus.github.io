---
title: JavaScript Actions
description: JavaScript actions
url: "/docs/javascriptdoc/jsactions"

showtoc: true
disableShare: true
hidemeta: true
---

### Copy to clipboard

`navigator.clipboard.writeText(content);`

### Get current page name

```
var x = mx.ui.getContentForm().path;
var y = x.split('/');
var z = y[1].split('.');
var pageName =  z[0];
return pageName;
```

### Select all text on input focus

Set this JavaScript action on the OnChange nanoflow

```
const activeElement = document.activeElement;
if (activeElement.tagName === "INPUT") activeElement.select();
```