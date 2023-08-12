---
title: Java actions
description: Miscellaneous Java action helpers
url: "/docs/javadoc/misc"
showtoc: true
disableShare: true
hidemeta: true
---

A collection of various helper functions in Java.

### Get object by guid

`return Core.retrieveId(getContext(), Core.createMendixIdentifier(objectGuid));`

### Get ModelReflection MxObjectMembers

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
