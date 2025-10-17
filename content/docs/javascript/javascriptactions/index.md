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

### Open url with target

`window.open(url, target);`

### Print current page

`window.print();`

### Toggle class on element

```
const element = document.querySelector(querySelector);
if (element) {
    if (element.classList.contains(className)) {
        element.classList.remove(className);
    }
    else {
        element.classList.add(className);
    }
    return true;
}
else return false;
```

[JS_ToggleClassOnElement.mpk](/mpk/JS_ToggleClassOnElement.mpk)

### Select all text on input focus

Set this JavaScript action on the OnChange nanoflow

```
const activeElement = document.activeElement;
if (activeElement.tagName === "INPUT") activeElement.select();
```

### Scroll to error

```
const validationMessage = document.querySelector(".mx-validation-message");
if(validationMessage) {
    scrollIntoView(validationMessage);
    return;
}
const alert = document.querySelector(".alert.alert-danger");
if(alert) {
    scrollIntoView(alert);
    return;
}
console.warn("No validation message found.");
```