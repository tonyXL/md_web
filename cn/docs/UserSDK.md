# UserSDK 接口文档

本文档提供了 UserSDK 的核心接口说明，用于控制相机设备、获取图像流及设置参数。

## 1. 初始化 (Initialize)
初始化 SDK 环境，必须在调用其他接口前执行。
- **函数原型**: `int Initialize(const char* configPath)`
- **参数**:
  - `configPath`: 配置文件路径
- **返回值**: 0 成功，其他失败

## 2. 打开相机 (OpenCamera)
连接并打开指定索引的相机设备。
- **函数原型**: `int OpenCamera(int cameraIndex)`
- **参数**:
  - `cameraIndex`: 相机设备索引（从 0 开始）
- **返回值**: 0 成功，其他失败

## 3. 关闭相机 (CloseCamera)
断开与相机的连接并释放资源。
- **函数原型**: `int CloseCamera(int cameraIndex)`
- **参数**:
  - `cameraIndex`: 相机设备索引
- **返回值**: 0 成功，其他失败

## 4. 开始采集 (StartStream)
开始从相机获取视频流数据。
- **函数原型**: `int StartStream(int cameraIndex)`
- **参数**:
  - `cameraIndex`: 相机设备索引
- **返回值**: 0 成功，其他失败

## 5. 停止采集 (StopStream)
停止获取视频流数据。
- **函数原型**: `int StopStream(int cameraIndex)`
- **参数**:
  - `cameraIndex`: 相机设备索引
- **返回值**: 0 成功，其他失败

## 6. 单帧抓拍 (CaptureImage)
从当前视频流中捕获一帧图像。
- **函数原型**: `int CaptureImage(int cameraIndex, void* buffer, int bufferSize)`
- **参数**:
  - `cameraIndex`: 相机设备索引
  - `buffer`: 用于存储图像数据的缓冲区
  - `bufferSize`: 缓冲区大小
- **返回值**: 0 成功，其他失败

## 7. 设置参数 (SetParameter)
设置相机的运行参数（如曝光、增益等）。
- **函数原型**: `int SetParameter(int cameraIndex, const char* paramName, float value)`
- **参数**:
  - `cameraIndex`: 相机设备索引
  - `paramName`: 参数名称（如 "Exposure", "Gain"）
  - `value`: 参数值
- **返回值**: 0 成功，其他失败

## 8. 获取参数 (GetParameter)
获取相机当前的运行参数。
- **函数原型**: `int GetParameter(int cameraIndex, const char* paramName, float* value)`
- **参数**:
  - `cameraIndex`: 相机设备索引
  - `paramName`: 参数名称
  - `value`: 用于接收参数值的指针
- **返回值**: 0 成功，其他失败

## 9. 注册回调 (RegisterCallback)
注册图像数据回调函数，用于异步接收图像数据。
- **函数原型**: `int RegisterCallback(int cameraIndex, void (*callback)(void* data, int size))`
- **参数**:
  - `cameraIndex`: 相机设备索引
  - `callback`: 回调函数指针
- **返回值**: 0 成功，其他失败

## 10. 获取版本号 (GetVersion)
获取 SDK 的版本信息。
- **函数原型**: `const char* GetVersion()`
- **参数**: 无
- **返回值**: 版本号字符串 (如 "1.0.0")
