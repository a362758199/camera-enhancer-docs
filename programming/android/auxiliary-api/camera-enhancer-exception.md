---
layout: default-layout
title: Android CameraEnhancerException Class - Dynamsoft Camera Enhancer
description: Doucmentation of Dynamsoft Camera Enhancer Android CameraEnhancerException class.
keywords:  Camera Enhancer, Android, CameraEnhancerException
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: Android CameraEnhancerException Class
---

# CameraEnhancerException

Exception for signaling camera enhancer errors.

```java
class com.dynamsoft.dce.CameraEnhancerException extends Exception
```

| Method Name | Type |
|------|------|
| [`getErrorCode`](#geterrorcode) | int |

&nbsp;

## getErrorCode

Gets the error code.

```java
int getErrorCode()
```

**Return Value**

The error code. See also [`Error Code List`]({{ site.mobile-enum }}errorcode-android.html?lang=android).

**Code Snippet**

```java
try {
    mCameraEnhancer.setResolution(EnumResolution.RESOLUTION_1080P);
} catch (CameraEnhancerException e) {
    Log.e("DCE", "onCreate: Resolution setting error is:"+e.getErrorCode());
}
```
