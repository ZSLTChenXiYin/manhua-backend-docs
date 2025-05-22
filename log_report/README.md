# 日志上报模块 API 文档

## 1. 设备信息上报

### 接口说明

### 请求信息
- 请求路径：`/api/v1/log-report`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - channelId: 渠道ID
  - platformId: 平台ID
  - device: 设备ID
  - versionNumber: 版本号
  - versionName: 版本
- 请求参数（json）：
```json
{
  "requestId": "<string>",  // 请求id,32位字符串，前端生成-保证每次请求的唯一性
  "type": "<string>",  // 上报类型,"add":首次安装后打开应用时上报,"active":每天首次打开应用时上报,"start":启动并距离上次关闭时间大于30s时上报,"time":如果时长差值大于30s，则上报时长。如果少于30s，则不上报，先记录时长留待下次上报。
  "akey": "<string>",  // "120-3"，120代表累计阅读秒数，3代表每个章节末尾的信息流广告累计成功加载次数，中间用-分割
  "network": "<string>",  // 网络类型-wifi-4g
  "phoneModel": "<string>",  // 手机型号
  "duration": "<integer>",  // app使用时长-单位为秒
  "startTime": "<string>",  // 开始时间格式 2020-10-10 10:03:12
  "endTime": "<string>",  // 结束时间格式 2020-10-10 10:03:12
  "sysVersion": "<string>"  // 系统版本
}
// 示例
{
  "requestId": "e66387dedd5d4e1e8712c61981b13918",
  "type": "active",
  "akey": "120-3",
  "network": "wifi-4g",
  "phoneModel": "huawei",
  "duration": 120,
  "startTime": "2025-5-22 10:01:12",
  "endTime": "2025-5-22 10:03:12",
  "sysVersion": "11"
}
```

### 响应信息
```json
{
    "requestId": "d761ce53-502b-47b7-ac6e-dcbb56ad017a",
    "code": 200,
    "msg": "上报成功",
    "data": {
        "sign_latest": true,
        "sign_present": true,
        "sign_valid": true
    }
}
```

## 2. 广告上报

### 接口说明

### 请求信息
- 请求路径：`/api/v1/ad-report`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - channelId: 渠道ID
  - platformId: 平台ID
  - device: 设备ID
  - versionNumber: 版本号
  - versionName: 版本

- 请求参数（json）：
```json
{
  "type": "adClick",  // 上报类型,"adClick":点击一次拦截广告时上报，"adPlayFinish":广告播完上报，"adFailure":"激励视频广告播放失败"
  "adErrMessage": "",  // 广告错误内容
  "adPosition": 1,  // 广告位置：1.阅读页广告拦截视频 2.书籍下载激励视频 3.阅读页拦截推广邀请
  "network": "wifi-4g",  // 网络类型-wifi-4g
  "phoneModel": "huawei"  // 手机型号
}
```

### 响应信息
```json
{
    "requestId": "84b23693-195e-4d0d-a563-837e439dd30b",
    "code": 200,
    "msg": "上报成功",
    "data": ""
}
```

## 错误码说明

| 错误码 | 说明 |
|--------|------|
| 200 | 成功 |
| 400 | 请求参数错误 |
| 401 | 未认证或认证失败 |
| 403 | 无权限访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |
