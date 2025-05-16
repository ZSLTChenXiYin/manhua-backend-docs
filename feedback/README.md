# 反馈模块 API 文档
1. [用户反馈标签列表](#1-用户反馈标签列表)
2. [用户反馈列表](#2-用户反馈列表)
3. [提交用户反馈](#3-提交用户反馈)
4. [提交章节纠错](#4-提交章节纠错)

## 1. 用户反馈标签列表

### 接口说明

### 请求信息
- 请求路径：`/api/v1/typelist`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（表单数据）：
  - class: 类型(1.意见反馈,2.章节纠错)
  - 示例：
    - class: 1

### 响应信息
```json
{
    "requestId": "f9f3dc2a-a11a-4f0d-a1da-9e94a57d0c48",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 8,
        "pageIndex": 1,
        "pageSize": 8,
        "list": [
            {
                "content": "不流畅",
                "type": 1
            },
            {
                "content": "更新慢",
                "type": 2
            },
            {
                "content": "书籍少",
                "type": 3
            },
            {
                "content": "操作难",
                "type": 4
            },
            {
                "content": "提示少",
                "type": 5
            },
            {
                "content": "不到账",
                "type": 6
            },
            {
                "content": "活动少",
                "type": 7
            },
            {
                "content": "其他",
                "type": 8
            }
        ]
    }
}
```

## 2. 用户反馈列表

### 接口说明

### 请求信息
- 请求路径：`/api/v1/feedback/list`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名

### 响应信息
```json
{
    "requestId": "732c4a29-cb17-4985-8a83-0690fcf4676d",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 3,
        "pageIndex": 1,
        "pageSize": 3,
        "list": [
            {
                "tag": "新手问题",
                "list": [
                    {
                        "title": "这里的漫画真的全部免费吗？",
                        "content": "本应用致力于为读者提供高质量的漫画，这里所有的漫画都是由版权方提供并授权发行的正版漫画，所有费用由我们承担，用户完全免费阅读。",
                        "picture": ""
                    }
                ]
            },
            {
                "tag": "阅读问题",
                "list": [
                    {
                        "title": "如何对阅读界面进行调整？",
                        "content": "在阅读器界面，单击屏幕中央区域，即可唤出阅读菜单。点击菜单上的“阅读设置”，字号、字体、背景色，翻页方式等一系列选项进行自定义操作。",
                        "picture": "/data/website/img/adjust.png"
                    },
                    {
                        "title": "为什么连载漫画还没有更新？",
                        "content": "连载漫画的更新时间取决于作者，一般会在2-4天内更新。如果遇到作者一星期以上没有更新，请点击下方“意见反馈”按钮对问题进行反馈，感谢您的关注与支持。",
                        "picture": ""
                    }
                ]
            },
            {
                "tag": "其他问题",
                "list": [
                    {
                        "title": "其他内容问题",
                        "content": "若有其他问题内容问题，如章节缺失，顺序错乱等，请点击下方的“意见反馈”，将你遇到的问题描述详细，并提供完整的漫画名、具体章节、系统提示文案和对应截图给我们，我们将为您跟进处理。",
                        "picture": ""
                    }
                ]
            }
        ]
    }
}
```

## 3. 提交用户反馈

### 接口说明

### 请求信息
- 请求路径：`/api/v1/addfeedback`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - versionNumber: 版本号
  - channelId: 渠道ID
  - 示例：
    - appId: 108
    - versionNumber: 1
    - channelId: 1

- 请求参数（json）：
```json
{
  "appVersion": "1.0.0",
  "content": "国外漫画太少了",
  "device": "1234567890",
  "deviceModel": "huawei",
  "mobile": "15523266543",
  "network": "wifi",  // 当前用户网络状态，如：4g、wifi、断网等
  "sysVersion": "11",
  "type": 3
}
```

### 响应信息
```json
{
    "requestId": "fa13cfee-b572-416a-ae7c-cbdafc1ae98d",
    "code": 200,
    "msg": "感谢您的反馈,我们会尽快核实",
    "data": null
}
```

## 4. 提交章节纠错

### 接口说明

### 请求信息
- 请求路径：`/api/v1/addchaptercorrect`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - appId: 应用ID
  - versionNumber: 版本号
  - channelId: 渠道ID
  - 示例：
    - appId: 108
    - versionNumber: 1
    - channelId: 1
- 请求参数（json）：
```json
{
  "appVersion": "1.0.0",
  "cartoonId": 10110,
  "cartoonName": "魔皇大管家",
  "chapterId": 133912,
  "chapterName": "第187话 登场",
  "content": "章节加载失败",
  "device": "1234567890",
  "deviceModel": "huawei",
  "mobile": "15523266543",
  "network": "wifi",
  "sysVersion": "11",
  "type": 4
}
```

### 响应信息
```json
{
    "requestId": "b9f4bdad-640f-43f4-b247-eca9998c822b",
    "code": 200,
    "msg": "感谢您的反馈,我们会尽快核实",
    "data": null
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
