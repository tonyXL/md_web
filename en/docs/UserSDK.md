# UserSDK Interface Documentation

This document provides core interface descriptions for UserSDK, used for controlling camera devices, acquiring image streams, and setting parameters.

## 1. Initialize
Initializes the SDK environment. Must be called before any other interfaces.
- **Prototype**: `int Initialize(const char* configPath)`
- **Parameters**:
  - `configPath`: Path to the configuration file
- **Return**: 0 on success, other values on failure

## 2. OpenCamera
Connects to and opens the specified camera device.
- **Prototype**: `int OpenCamera(int cameraIndex)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device (starting from 0)
- **Return**: 0 on success, other values on failure

## 3. CloseCamera
Disconnects from the camera and releases resources.
- **Prototype**: `int CloseCamera(int cameraIndex)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
- **Return**: 0 on success, other values on failure

## 4. StartStream
Starts acquiring video stream data from the camera.
- **Prototype**: `int StartStream(int cameraIndex)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
- **Return**: 0 on success, other values on failure

## 5. StopStream
Stops acquiring video stream data.
- **Prototype**: `int StopStream(int cameraIndex)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
- **Return**: 0 on success, other values on failure

## 6. CaptureImage
Captures a single frame from the current video stream.
- **Prototype**: `int CaptureImage(int cameraIndex, void* buffer, int bufferSize)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
  - `buffer`: Buffer to store image data
  - `bufferSize`: Size of the buffer
- **Return**: 0 on success, other values on failure

## 7. SetParameter
Sets camera operating parameters (e.g., exposure, gain).
- **Prototype**: `int SetParameter(int cameraIndex, const char* paramName, float value)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
  - `paramName`: Parameter name (e.g., "Exposure", "Gain")
  - `value`: Parameter value
- **Return**: 0 on success, other values on failure

## 8. GetParameter
Gets current camera operating parameters.
- **Prototype**: `int GetParameter(int cameraIndex, const char* paramName, float* value)`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
  - `paramName`: Parameter name
  - `value`: Pointer to receive the parameter value
- **Return**: 0 on success, other values on failure

## 9. RegisterCallback
Registers an image data callback function for asynchronous data reception.
- **Prototype**: `int RegisterCallback(int cameraIndex, void (*callback)(void* data, int size))`
- **Parameters**:
  - `cameraIndex`: Index of the camera device
  - `callback`: Function pointer to the callback
- **Return**: 0 on success, other values on failure

## 10. GetVersion
Gets the SDK version information.
- **Prototype**: `const char* GetVersion()`
- **Parameters**: None
- **Return**: Version string (e.g., "1.0.0")
