# 设备模块 API 文档
1. [设备注册](#1-设备注册)
2. [获取邀请码和邀请数量](#2-获取邀请码和邀请数量)
3. [获取免广告时间](#3-获取免广告时间)
4. [获取邀请用户列表](#4-获取邀请用户列表)
5. [获取邀请分享信息](#5-获取邀请分享信息)
6. [查询设备更新状态](#6-查询设备更新状态)
## 1. 设备注册

### 接口说明
注册新设备，获取设备ID和邀请码。

### 请求信息
- 请求路径：`/api/v1/device/register`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json
  - versionName: 版本名称（可使用1.0.0或1.0.1）
  - versionNumber: 版本号（版本名称1.0.0对应1，1.0.1对应101）
  - appId: 应用ID（102-107，建议测试使用107）
    - 102: 美漫园
    - 103: 大树园
    - 104: 梦漫彩
    - 105: 漫千绘
    - 106: 罗漫园
    - 107: 漫云彩
  - platformId: 平台ID（测试使用1）
  - channelId: 渠道ID（已弃用，填1即可）

- 请求参数（json）：
```json
{
    "device": "string",      // 设备号（可使用安卓id）
    "inviteCode": "string",  // 邀请码（可选）
    "sign": "string",        // RSA加密签名（先用RSA加密，后用base64编码填入）
    "osVersion": "string",   // 操作系统版本
    "deviceModel": "string"  // 设备型号
}
```

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": "ok"
}
```

## 2. 获取邀请码和邀请数量

### 接口说明
获取设备的邀请码和已邀请用户数量。

### 请求信息
- 请求路径：`/api/v1/device/invitenumandcode`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
  - appId: 应用ID
  - platformId: 平台ID

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "inviteCode": "string",    // 邀请码
        "inviteCount": 0,           // 邀请数量
        "shortUrl": "string"       // 邀请码短链接
    }
}
```

## 3. 获取免广告时间

### 接口说明
获取设备的免广告时间信息。

### 请求信息
- 请求路径：`/api/v1/device/invitetime`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
  - appId: 应用ID

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "inviteTime": "2024-03-21T10:00:00Z",  // 免广告时间
        "signPresent": true,                    // 签名是否存在
        "signValid": true,                      // 签名是否有效
        "signLatest": true                      // 签名是否最新
    }
}
```

## 4. 获取邀请用户列表

### 接口说明
获取通过该设备邀请码注册的用户列表。

### 请求信息
- 请求路径：`/api/v1/device/myinviteuserlist`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
  - appId: 应用ID

- 请求参数（表单数据）：
  - pageIndex: 页码（int）
  - pageSize: 每页记录数（int）

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "total": 100,                // 总记录数
        "pageIndex": 1,              // 当前页码
        "pageSize": 10,              // 每页记录数
        "list": [                    // 用户列表
            {
                "userId": 1,         // 用户ID
                "nickname": "string", // 昵称
                "avatar": "string",   // 头像URL
                "inviteTime": "2024-03-21T10:00:00Z" // 邀请时间
            }
        ]
    }
}
```

## 5. 获取邀请分享信息

### 接口说明
获取设备邀请分享的相关信息。

### 请求信息
- 请求路径：`/api/v1/device/inviteshare`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
  - appId: 应用ID
  - platformId: 平台ID

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": "ok"
}
```

## 6. 查询设备更新状态
### 接口说明
查询设备号是否更新完成。该路由目前必定返回成功。

### 请求信息
- 请求路径：`/api/v1/device/queryUpdateState`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json
  - X-Package: 应用包名
  - sign: 请求签名

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "state": 2  // 更新状态：1-更新中，2-更新完成
    }
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

## 注意事项

1. 设备注册时需要提供有效的设备号和签名
2. 邀请码系统用于用户推广和获取免广告时间
3. 设备更新状态查询用于同步设备信息
4. 设备黑名单功能用于管理违规设备
5. 所有请求都需要进行签名验证
6. 设备注册可能会受到每日限制和特定应用的限制 