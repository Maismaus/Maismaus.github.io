---
title: Java actions
description: Miscellaneous Java action helpers
url: "/docs/javadoc/"
showtoc: true
disableShare: true
hidemeta: true
---

A collection of various helper functions in Java.

## Get object by guid

`return Core.retrieveId(getContext(), Core.createMendixIdentifier(objectGuid));`

[JAVA_GetObjectByGuid.mpk](/mpk/JAVA_GetObjectByGuid.mpk)

## Get ModelReflection MxObjectMembers

```
XPath<IMendixObject> xpath = XPath.create(getContext(), MxObjectMember.entityName)
    .eq(
        MxObjectMember.MemberNames.MxObjectMember_MxObjectType,
        MxObjectType.entityName,
        MxObjectType.MemberNames.CompleteName,
        targetObject);
List<IMendixObject> mxObjectMemberList = xpath.all();
return mxObjectMemberList;
```

[JAVA_GetMxObjectMembers.mpk](/mpk/JAVA_GetMxObjectMembers.mpk)

## Escape JSON object

`return JSONObject.escape(inputString);`

[JAVA_EscapeJSON.mpk](/mpk/JAVA_EscapeJSON.mpk)