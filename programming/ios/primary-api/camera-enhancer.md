---
layout: default-layout
title: Dynamsoft Camera Enhancer - iOS API references - CameraEnhancer Class
description: This is the documentation - iOS API references - CameraEnhancer Class page of Dynamsoft Camera Enhancer.
keywords:  Camera Enhancer, iOS API references, CameraEnhancer Class
needAutoGenerateSidebar: true
noTitleIndex: true
needGenerateH3Content: true
breadcrumbText: iOS CameraEnhancer Class
---

# CameraEnhancer Class

```objc
class com.dynamsoft.dce.CameraEnhancer
```

## Initialization

| Method | Description |
| ------ | ----------- |
| [`initWithView`](#initwithview) | Initialize the camera enhancer with the camera view |
| [`initLicense`](#initlicense) | Sets product key and activate the SDK. |
| [`getVersion`](#getversion) | Get the SDK version. |

&nbsp;

### initWithView

Initialize the camera enhancer with the `DCECameraView`.

```java
- (instancetype)initWithView:(DCECameraView *)view;
```

**Return Value**

The instance of DynamsoftCameraEnhancer.

**Code Snippet**

Objective-C:

```objc
_dce = [[DynamsoftCameraEnhancer alloc] initWithView:_dceView];
```

Swift:

```swift
let dce = DynamsoftCameraEnhancer.init(view: dceCameraView)
```

### initLicense

Sets product key and activate the SDK.

```objc
+(void)initLicense:(NSString*)license verificationListener:(id) verificationListener;
```

**Parameters**

`license`: The product key.  
`verificationListener`: The listener that handle callback when license server returns. See also [`DCELicenseVerificationListener`]({{ site.ios-api-auxiliary }}protocol-licenselistener.html).

**Code Snippet**

Objective-C:

```objc
[DynamsoftCameraEnhancer initLicense:@"Put your license here" verificationDelegate: self];
```

Swift:

```swift
DynamsoftCameraEnhancer.initLicense("Put your license here", verificationDelegate: self)
```

&nbsp;

### getVersion

Get the SDK version of Dynamsoft Camera Enhancer.

```objc
- (NSString*)getVersion;
```

**Return Value**

A string value that stands for the camera enhancer SDK version.

**Code Snippet**

Objective-C:

```objc
NSString* version = [_dce getVersion];
```

Swift:

```swift
let version = dce.getVersion()
```

&nbsp;

## Basic Camera Control Methods

| Method | Description |
| ------ | ----------- |
| [`getAllCameras`](#getallcameras) | Get all available cameras. This method returns a list of available camera IDs. |
| [`selectCamera`](#selectcamera) | Select a camera from the camera list with the camera ID. |
| [`getSelectedCamera`](#getselectedcamera) | Get the camera ID of the current selected camera. |
| [`getCameraState`](#getcamerastate) | Get the state of the current selected camera. |
| [`open`](#open) | Turn on the current selected camera. |
| [`close`](#close) | Turn off the current selected camera. |
| [`pause`](#pause) | Pause the current selected  camera. |
| [`resume`](#resume) | Resume the current selected camera. |
| [`turnOnTorch`](#turnontorch) | Turn on the torch. |
| [`turnOffTorch`](#turnofftorch) | Turn off the torch. |

&nbsp;

### getAllCameras

Get the IDs of all available cameras.

```objc
- (NSArray*)getAllCameras;
```

**Return Value**

An NSArray that includes all available cameras. Users can clearly read whether the camera is front-facing, back-facing or external from the cameraID.

**Code Snippet**

Objective-C:

```objc
NSArray<NSString*>* allCameras = [_dce getAllCameras];
```

Swift:

```swift
let allCameraList = dce.getAllCameras()
```

&nbsp;

### selectCamera

Select camera by `cameraID`. The camera will be selected and further camera control settings will be applied to this camera. When the selected camera is changed by selecting another camera via this method, the settings that applied to this camera will be inherited by the newly selected camera.

```objc
- (void)selectCamera:(NSString*)cameraId;
```

**Parameters**

`cameraID`: A `String` value that listed in the `cameraIDList` returned by `getAllCameras`. The method will have no effects if the input value does not exist in the `cameraIDList`.

**Code Snippet**

Objective-C:

```objc
[_dce selectCamera:@"BACK_FACING_CAMERA"];
```

Swift:

```swift
dce.selectCamera("BACK_FACING_CAMERA")
```

**Remarks**

- There is always a back-facing camera be defined as a default camera. If user don't select any camera via `selectCamera`, the default camera will be considered as the selected camera.
- If there is no opened camera, the method `selectCamera` will not open any camera.
- If there is an opened camera and the opened camera's ID is exactly equals the input ID, the method `selectCamera` will make no changes.
- If there is an opened camera and the opened camera's ID is different with the input ID, the method `selectCamera` will close the currently opened camera and then open a new camera by the input ID.

&nbsp;

### getSelectedCamera

Get the ID of the current selected camera.

```objc
- (NSString*)getSelectedCamera;
```

**Return Value**

The ID of the current selected camera.

**Code Snippet**

Objective-C:

```objc
NSString* cameraID = [_dce getSelectedCamera];
```

Swift:

```swift
let selectedCamera = dce.getSelectedCamera()
```

&nbsp;

### getCameraState

Get the state of the current selected camera.

```objc
- (EnumCameraState*)getCameraState;
```

**Return Value**

One of the preset camera state in Enumeration [`EnumCameraState`]({{site.enumerations}}enum-camera-state.html).

**Code Snippet**

Objective-C:

```objc
EnumCameraState state = [_dce getCameraState];
```

Swift:

```swift
let cameraState = dce.getCameraState()
```

&nbsp;

### open

- Turn on the selected camera if a camera has been selected via `selectCamera`.
- Turn on the default camera if no camera is selected via `selectCamera`.

```objc
- (void)open;
```

**Code Snippet**

Objective-C:

```objc
[_dce open];
```

Swift:

```swift
dce.open()
```

&nbsp;

### close

- Turn off the selected camera if a camera has been selected via `selectCamera`.
- Turn off the default camera if no camera is selected via `selectCamera`.

```objc
- (void)close;
```

**Code Snippet**

Objective-C:

```objc
[_dce close];
```

Swift:

```swift
dce.close()
```

&nbsp;

### pause

- Pause the selected camera if a camera has been selected via `selectCamera`.
- Pause the default camera if no camera is selected via `selectCamera`.

```objc
- (void)pause;
```

**Code Snippet**

Objective-C:

```objc
[_dce pause];
```

Swift:

```swift
dce.pause()
```

**Remarks**

If the `pause` method is triggered:

- The camera UI will be stopped on the last frame that captured before you `pause` the camera.
- The camera is still opened.
- The video streaming input is not stopped.
- DCE video buffer will continue appending frames.

&nbsp;

### resume

- Resume the selected camera if a camera has been selected via `selectCamera`.
- Resume the default camera if no camera is selected via `selectCamera`.

```objc
- (void)resume;
```

**Code Snippet**

Objective-C:

```objc
[_dce resume];
```

Swift:

```swift
dce.resume()
```

&nbsp;

### turnOnTorch

Turn on the torch (if the torch of the mobile device is available).

```objc
- (void)turnOnTorch;
```

**Code Snippet**

Objective-C:

```objc
[_dce turnOnTorch];
```

Swift:

```swift
dce.turnOnTorch()
```

&nbsp;

### turnOffTorch

Turn off the torch.

```objc
- (void)turnOffTorch;
```

**Code Snippet**

Objective-C:

```objc
[_dce turnOffTorch];
```

Swift:

```swift
dce.turnOffTorch()
```

&nbsp;

## Frame Acquiring Methods

| Method | Description |
| ------ | ----------- |
| [`getFrameFromBuffer`](#getframefrombuffer) | Get the latest frame from the buffer. The input boolean value determines whether the fetched frame will be removed from the buffer. |
| [`addListener`](#addlistener) | Add a listener to the camera enhancer instance. |
| [`removeListener`](#removelistener) | Remove a preciously added listener from the camera enhancer instance. |

&nbsp;

### getFrameFromBuffer

Get the latest frame from the buffer. The input boolean value determines whether the fetched frame will be removed from the buffer.

```objc
- (DCEFrame*)getFrameFromBuffer:(BOOL)keep;
```

**Parameters**

`Keep`: If set to `true`, the frame will be kept in the video buffer, otherwise it will be removed from the video buffer.

**Return Value**

The latest frame in the video buffer.

**Code Snippet**

Objective-C:

```objc
dceFrame = [_dce getFrameFromBuffer:true];
```

Swift:

```swift
let dceFrame = dce.getFrameFromBuffer()
```

&nbsp;

### addListener

Add a listener to the `CameraEnhancer` instance. This method will have no effect if the same listener is already added.

```objc
- (void)addListener:(nonnull id<DCEFrameListener>)listener;
```

**Parameters**

`listener`: An object of `DCEFrameListener`. Its callback method `frameOutputCallback` will be available for users to make further operations on the captured video frame.

**Code Snippet**

Objective-C:

```objc
[_dce addListener:self];
```

Swift:

```swift
dce.addListener(self)
```

&nbsp;

### removeListener

Remove a preciously added listener from the `CameraEnhancer` instance. This method will have no effect if there is no listener exists in `CameraEnhancer` instance.

```objc
- (void)removeListener:(nonnull id<DCEFrameListener>)listener;
```

**Parameters**

`listener`: The input listener will be removed from CameraEnhancer instance.

**Code Snippet**

Objective-C:

```objc
[_dce removeListener:self];
```

Swift:

```swift
dce.removeListener(self)
```

&nbsp;

## Enhanced Features

| Method | Description |
| ------ | ----------- |
| [`enableFeatures`](#enablefeature) | Enable camera enhancer features by inputting [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html) values. |
| [`disableFeatures`](#disablefeature) | Disable camera enhancer features by inputting [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html) values. |
| [`isFeatureEnabled`](#isfeatureenabled) | Check whether the input features are enabled. |

&nbsp;

### enableFeatures

Enable camera enhancer features by inputting [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html) value.

```objc
- (void)enableFeatures:(EnumEnhancerFeatures)features;
```

**Parameters**

`enhancerFeatures`: The combined value of [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html).  

**Code Snippet**

Objective-C:

```objc
[_dce enableFeatures:0x01];
```

Swift:

```swift
dce.enableFeatures(0x01)
```

**Remarks**

The `EnumEnhancerFeatures` members:

|  Members | Value |
| ------------------------------ | ----- |
| `FRAME_FILTER` | 0x01 |
| `SENSOR_CONTROL` | 0x02 |
| `ENHANCED_FOCUS` | 0x04 |
| `FAST_MODE` | 0x08 |
| `AUTO_ZOOM` | 0x10 |

The enable action will not be approved if the license is invalid. If your input values include the features that already enabled, these features will keep the enabled status.

&nbsp;

### disableFeatures

Disable camera enhancer features by inputting [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html) values.

```objc
- (void)disableFeatures:(EnumEnhancerFeatures)features;
```

**Parameters**

`enhancerFeatures`: The combined value of [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html).  

**Code Snippet**

Objective-C:

```objc
[_dce disableFeatures:0x02];
```

Swift:

```swift
dce.disableFeatures(0x02)
```

**Remarks**

You can still disable the features evenif the license is invalid. If your input values include the features that are not enabled, these features will keep the disabled status.

&nbsp;

### isFeatureEnabled

Check whether the input features are enabled.

```objc
- (BOOL)isFeatureEnabled:(EnumEnhancerFeatures)features;
```

**Parameters**

`enhancerFeatures`: The combined value of [`EnumEnhancerFeatures`]({{site.enumerations}}enum-enhancer-features.html).

**Return Value**

A BOOL value that refers to whether all the features you input are enabled.

- `True`: All the features you input are enabled.  
- `False`: There is at least one feature is not enabled among your input values.

**Code Snippet**

Objective-C:

```objc
BOOL featureEnabled = [_dce isFeatureEnabled:0x02];
```

Swift:

```swift
let featureEnabled = dce.isFeatureEnabled(0x02)
```

**Remarks**

If the features you input are all enabled but don't cover all the enabled features, this method will still return `true`.

&nbsp;

## Advanced Camera Control Methods

| Method | Description |
| ------ | ----------- |
| [`setFrameRate`](#setframerate) | Set the frame rate to the input value (if the input value is available for the device). |
| [`getFrameRate`](#getframerate) | Get the current frame rate. |
| [`setResolution`](#setresolution) | Set the resolution to the input value (if the input value is available for the device). |
| [`getResolution`](#getresolution) | Get the current resolution. |
| [`setZoom`](#setzoom) | Set the zoom factor. Once `setZoom` is triggered and approved, the zoom factor of the actived camera will immediately become the input value. |
| [`setFocus`](#setfocus) | Set the focus position (value range from 0.0f to 1.0f) and trigger a focus at the configured position. |
| [`updateAdvancedSettingsFromFile`](#updateadvancedsettingsfromfile) | Update the advanced camera controlling and video streaming processing parameters. This method enable you to update settings via a JSON file from the storage. |
| [`updateAdvancedSettingsFromString`](#updateadvancedsettingsfromstring) | Update the advanced camera controlling and video streaming processing parameters. This method enable you to update settings via a JSON string. |

### setFrameRate

Set the frame rate to the input value (if the input value is available for the device).

```objc
- (void)setFrameRate:(NSInteger)frameRate;
```

**Parameters**

`frameRate`: An int value that refers to the target frame rate.  

**Code Snippet**

Objective-C:

```objc
[_dce setFrameRate:15];
```

Swift:

```swift
dce.setFrameRate(15)
```

**Remarks**

The available frame rate setting threshold is alway intermittent, which means the input value might not match any available frame rate threshold. If the input value is below the lowest available threshold, the frame rate will be set to the lowest available threshold. If the input value is above the lowest available threshold but still not match any threshold, the frame rate will be set to the highest available threshold that belows the input value.

&nbsp;

### getFrameRate

Get the current frame rate.

```objc
- (NSInteger)getFrameRate;
```

**Return Value**

The current frame rate.

**Code Snippet**

Objective-C:

```objc
NSInteger frameRate = [_dce getFrameRate];
```

Swift:

```swift
let frameRate = dce.getFrameRate()
```

&nbsp;

### setResolution

Input a target resolution value that preset in Enumeration `Resolution`. The camera enhancer will try to set the resolution to the target value or the closest available value below the target value.

```objc
- (Void)setResolution:(Resolution)resolution;
```

**Parameters**

`resolution`: One of the int value that preset in Enumeration [`EnumResolution`]({{site.enumerations}}enum-resolution.html).

**Code Snippet**

Objective-C:

```objc
[_dce setResolution:EnumResolution1080P];
```

Swift:

```swift
dce.setResolution(Resolution.EnumResolution1080P)
```

&nbsp;

### getResolution

Get the current resolution.

```objc
- (NSString*)getResolution;
```

**Return Value**

The size of the current resolution.

**Code Snippet**

Objective-C:

```objc
NSInteger resolution = [_dce getResolution];
```

Swift:

```swift
let resolution = dce.getResolution()
```

&nbsp;

### setZoom

Set the zoom factor. Once `setZoom` is triggered and approved, the zoom factor of the actived camera will immediately become the input value.

```objc
- (Void)setZoom:(CGFloat)factor
```

**Parameters**

`factor`: The target zoom factor.

**Code Snippet**

Objective-C:

```objc
[_dce setZoom:3.0f];
```

Swift:

```swift
dce.setZoom(3.0)
```

&nbsp;

### setFocus

Set the focus position (value range from 0.0f to 1.0f) and trigger a focus at the configured position.

```objc
- (Void)setFocus:(CGPoint)focusPosition;
```

**Parameters**

`focusPosition`: A CGPoint that stores the x and y coordinate of the targeting focus position.

**Code Snippet**

Objective-C:

```objc
CGPoint focusPoint = {0.4, 0.5};
[_dce setFocus:focusPoint];
```

Swift:

```swift
let focusPoint = CGPoint(x:0.4, y:0.5)
dce.setFocus(focusPoint)
```

&nbsp;

### updateAdvancedSettingsFromFile

Update the advanced camera controlling and video streaming processing parameters. This method enable you to update settings via a JSON file from the storage.

```objc
- (void)updateAdvancedSettings:(NSString*)filePath;
```

**Parameters**

`filePath`: The file path of the JSON file.

**Code Snippet**

Objective-C:

```objc
[_dce updateAdvancedSettingsFromFile:@"Put your JSON file path here."];
```

Swift:

```swift
dce.updateAdvancedSettingsFromFile("Put your JSON file path here.")
```

**Remarks**

You might need permission authority to enable the Camera Enhancer to read the file in your mobile storage.

&nbsp;

### updateAdvancedSettingsFromString

Update the advanced camera controlling and video streaming processing parameters. This method enable you to update settings via a JSON string.

```objc
- (void)updateAdvancedSettings:(NSString*)JSONString;
```

**Parameters**

`jsonString`: A stringified JSON data.

**Code Snippet**

Objective-C:

```objc
[_dce updateAdvancedSettingsFromString:@"Put your stringified JSON data here."];
```

Swift:

```swift
dce.updateAdvancedSettingsFromString("Put your stringified JSON data here.")
```