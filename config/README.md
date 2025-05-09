# 配置模块 API 文档
1. [获取系统配置](#1-获取系统配置)
2. [检查更新](#2-检查更新)
3. [获取第三方参数](#3-获取第三方参数)

## 1. 获取系统配置

### 接口说明
获取系统配置信息。

### 请求信息
- 请求路径：`/api/v1/config`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - platformId: 平台ID
  - channelId: 渠道ID
  - versionName: 版本名称
  - versionNumber: 版本号
  - device: 设备号
- 请求参数（表单数据）：
  - platform: 平台（1-安卓, 2-IOS）

### 响应信息
```json
{
    "requestId": "f39bb6ac-dbc7-478f-b1bc-48081a37a286",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "commentSwitch": 0,
        "cacheDomain": "https://ct-api.dashuyuanapp.com",
        "imageDomain": "https://cdn-image.tumanapp.com",
        "coverDomain": "https://cdn-image.tumanapp.com",
        "staticDomain": "https://cdn-statics.tumanapp.com",
        "shareDownUrl": "https://api.wudidewo.one/website/download.html",
        "promotionTitle": "成功邀请好友，送免广告特权",
        "thirdPartyConfig": {
            "baiduyyAppId": "",
            "baiduyyAppKey": "",
            "baiduyySecretKey": "",
            "androidOcpcId": "",
            "androidOcpcKey": "",
            "iosOcpcId": "",
            "iosOcpcKey": "",
            "ocpcStatus": 2,
            "watchwordSwitch": 2,
            "p2pswitch": "2",
            "p2pswitchios": "2"
        },
        "configAdvertise": {
            "ios": {},
            "android": {},
            "adSwitch": false,
            "readAdPage": 0,
            "watchVideoFreeTime": 0,
            "readUnlockChapter": 0,
            "readUnlockIntervalChapter": 0,
            "installAfterAd": 0,
            "installAfterAdOrigin": 0,
            "readFullAdInterval": 0,
            "readInterceptInterval": 0,
            "homePageInterstitialTime": 0
        },
        "promotionDesc": [
            {
                "title": "推广说明：",
                "content": "每成功推广1人，送1天免广告，可无限叠加。\n累计成功推广50人，送终身免广告。"
            },
            {
                "title": "怎样才算推广成功？",
                "content": "分享给未安装过的用户，被邀请者下载后启动应用成功即可，对方必须在不同的设备上进行登录。(如邀请不成功请被邀请者登录应用后再尝试)"
            },
            {
                "title": "为什么推广链接别人打不开？",
                "content": "因为微信或QQ等第三方内置浏览器会自动屏蔽，推荐使用自带浏览器等打开。"
            }
        ],
        "signalingUrl": "",
        "p2pSwitch": false,
        "p2pSwitchIos": false,
        "iosTrailer": false,
        "androidTrailer": false,
        "statusOver": 2
    }
}
```

## 2. 检查更新

### 接口说明
检查应用是否有新版本更新。

### 请求信息
- 请求路径：`/api/v1/checkupdate`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - platformId: 平台ID
  - channelId: 渠道ID
  - versionName: 版本名称
  - versionNumber: 版本号
  - device: 设备号
  - channelId: 渠道ID

### 请求参数
| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| platform | int | 是 | 平台类型：1-安卓，2-IOS |

### 响应信息
```json
{
    "code": 0,
    "message": "success",
    "data": {
        "has_update": true,          // 是否有更新
        "force_update": false,       // 是否强制更新
        "version": "1.0.0",          // 最新版本号
        "update_url": "string",      // 更新下载地址
        "update_content": "string"   // 更新内容说明
    }
}
```

## 3. 获取第三方参数

### 接口说明
获取第三方服务配置参数，如短信服务、对象存储等。

### 请求信息
- 请求路径：`/api/v1/thirdparameter`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID

### 响应信息
```json
{
    "requestId": "3935c7e2-c246-4bd6-815a-2a592a7db95f",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "aKeyLoginIosSecret": "3dxxjk1",
        "aKeyLoginAndroidSecret": "u83gwu1"
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

1. 所有配置接口都需要进行签名验证
2. 配置信息会根据不同的应用ID、平台ID和渠道ID返回不同的配置
3. 版本检查接口会根据当前版本号判断是否需要更新
4. 第三方参数接口返回的敏感信息（如密钥）需要进行加密处理
5. 配置信息会定期更新，客户端需要做好缓存处理
6. 强制更新时，用户必须更新到最新版本才能继续使用 