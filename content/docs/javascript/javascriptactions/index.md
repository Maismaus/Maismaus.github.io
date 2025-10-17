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

### Select all text on input focus

Set this JavaScript action on the OnChange nanoflow

```
const activeElement = document.activeElement;
if (activeElement.tagName === "INPUT") activeElement.select();
```