---
title: JavaScript API
description: Mendix JavaScript API
url: "/docs/jsdoc/javascriptapi"

showtoc: true
disableShare: true
hidemeta: true
---

This section describes various JavaScript code snippets using the Mendix JavaScript client-side API.
For the complete documentation, refer to the [Mendix docs](https://apidocs.rnd.mendix.com/10/client/index.html)

## Session management

### Remove sessions

This can be useful if you've exceeded the user limit in your local environment

```
mx.data.get({
  xpath: "//System.Session",
  callback: function (session) {
    var sessionArray = [];
    var sessionLength = session.length;
    for (var i = 0; i < session.length; i++) {
      sessionArray.push(session[i]._guid);
    }
    mx.data.remove({
      guids: sessionArray,
      callback: function () {
        console.log(sessionLength + " sessions removed");
      },
      error: function (e) {
        console.log("Could not remove objects:", e);
      },
    });
  },
});
```

#### Session bookmarklet

```
javascript:(function()%7Bmx.data.get(%7Bxpath%3A%20%22%2F%2FSystem.Session%22%2Ccallback%3A%20function%20(session)%20%7Bvar%20sessionArray%20%3D%20%5B%5D%3Bfor%20(var%20i%20%3D%200%3B%20i%20%3C%20session.length%3B%20i%2B%2B)%20%7BsessionArray.push(session%5Bi%5D._guid)%3B%7Dmx.data.remove(%7Bguids%3A%20sessionArray%2Ccallback%3A%20function%20()%20%7Bconsole.log(toString(session.length)%20%2B%20%22sessions%20removed%22)%3B%7D%2Cerror%3A%20function%20(e)%20%7Bconsole.log(%22Could%20not%20remove%20objects%3A%22%2C%20e)%3B%7D%7D)%3B%7D%7D)%7D)()

```

### Logging in

```
var xhr = new XMLHttpRequest();
xhr.open("POST", location.origin + "/xas/", true);
xhr.setRequestHeader("Content-Type", "application/json");
xhr.send(
  JSON.stringify({
    action: "login",
    params: {
      username: "MxAdmin",
      password: "1",
    },
  })
);
xhr.onreadystatechange = function () {
  window.location = "index.html";
};
```

#### Login bookmarklet

Bookmark this and press the bookmark to login. Replace username and password with your own (currently: MxAdmin, 1).

```
javascript:(function()%7Bvar%20xhr%3Dnew%20XMLHttpRequest()%3Bxhr.open(%22POST%22%2Clocation.origin%2B%22%2Fxas%2F%22%2Ctrue)%3Bxhr.setRequestHeader(%22Content-Type%22%2C%22application%2Fjson%22)%3Bxhr.send(JSON.stringify(%7Baction%3A%22login%22%2Cparams%3A%7Busername%3A%22MxAdmin%22%2Cpassword%3A%221%22%2C%7D%2C%7D))%3Bxhr.onreadystatechange%3Dfunction()%7Bwindow.location%3D%22index.html%22%3B%7D%7D)()%3B
```

## Object handling

### Log GUID of object retrieved through association

```
mx.data.get({
  xpath: "//Onboarding.Application[RegisterID=257]/Onboarding.Applicant_Application/Onboarding.Applicant",
  callback: function (obj) {
    console.log(obj[0]._guid);
  },
});
```

### Retrieve objects with guid

```
mx.data.get({
  guids: ["123456", "456789"],
  callback: function (objs) {
    console.log("Received " + objs.length + " MxObjects");
  },
});
```

### Execute microflow with guid as parameter

```
mx.data.action({
  params: {
    applyto: "selection",
    actionname: "Onboarding.ACT_NewApplication", //Execute microflow
    guids: ["20829148276589155"], //Guid as parameter
  },
  origin: this.mxform,
  callback: function (obj) {
    // expect single MxObject
    alert(obj.get("manufacturer"));
  },
  error: function (error) {
    alert(error);
  },
});
```

### Get, edit and commit

```
mx.data.get({
  xpath: "//Onboarding.Applicant[RegisterID=1374]", //Get applicant with ID 1374
  callback: function (obj) {
    obj[0].set("RegisterID", "1375"); //Set marital status to '02'
    mx.data.commit({
      mxobj: obj[0], //Commit applicant
      callback: function () {
        console.log("Object committed");
      },
      error: function (e) {
        console.error("Could not commit object:", e);
      },
    });
  },
});
```

### Advanced object editing

-  Get an object,
-  Get another object,
-  Set association of first object to second object,
-  Commit second object

```
mx.data.get({
  xpath: '//Onboarding.Applicant[RegisterID=1374]',
  callback: function (applicant) {
    console.log(applicant[0]);
    mx.data.get({
      xpath: '//Onboarding.Country[Name="Germany"]',
      callback: function (obj) {
        obj[0].addReference("Onboarding.Application_Country", country[0]._guid);
        console.log(obj[0]);
        mx.data.commit({
          mxobj: obj[0], //Commit applicant
          callback: function () {
            console.log("Object committed");
          },
          error: function (e) {
            console.error("Could not commit object:", e);
          },
        });
      },
    });
  },
});
```

### Remove object

```
mx.data.get({
  xpath: "//Onboarding.Applicant[RegisterID=84427]",
  callback: function (applicant) {
    //Return list of tasks
    mx.data.remove({
      //Remove first item in the list
      guid: applicant[0]._guid,
      callback: function () {
        console.log(applicant[0]);
      },
      error: function (e) {
        console.log("Could not remove objects:", e);
      },
    });
  },
});
```

## Open pages

### Open page in content

```
mx.ui.openForm("Login/Login.page.xml", {
  location: "content",
  callback: function (form) {
    console.log(form.id);
  },
});
```

### Open page in popup

```
mx.ui.openForm("Onboarding/Application.page.xml", {
  location: "modal",
  callback: function () {},
});
```

### Get page title

```
javascript: (function () {
  var pageTitle = mx.ui.getContentForm().path.replace(".page.xml", "");
  var pageTitleArr = pageTitle.split("/");
  var moduleName = pageTitleArr[0];
  var pageName = pageTitleArr[1];
  prompt("Module: " + moduleName, pageName);
})();
```
