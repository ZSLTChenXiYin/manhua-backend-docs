# 漫画历史记录模块 API 文档
1. [加入阅读历史](#1-加入阅读历史)
2. [获取阅读历史](#2-获取阅读历史)
3. [删除阅读历史记录](#3-删除阅读历史记录)

## 1. 加入阅读历史

### 接口说明
将漫画加入用户的阅读历史记录。

### 请求信息
- 请求路径：`/api/v1/cartoonhistory`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token} （可选，用于验证会员用户身份）
  - device: 设备号
  - appId: 应用ID
  - platformId: 平台ID
  - channelId: 渠道ID（已弃用）

- 请求参数（json）：
```json
{
  "cartoonId": 1139,
  "chapter": 1,
  "chapterId": 81980,
  "chapterName": "02 师姐难当"
}
```

### 响应信息
```json
{
    "requestId": "11de2cce-9c26-4c52-9c49-0764a9ffc300",
    "code": 200,
    "msg": "同步成功",
    "data": {
        "a": false,
        "b": "to",
        "c": "webp"
    }
}
```

## 2. 获取阅读历史

### 接口说明
获取当前用户的阅读历史记录。

### 请求信息
- 请求路径：`/api/v1/cartoonhistory`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号

- 请求参数（表单数据）：
  - pageSize: 每页记录数
  - pageIndex: 当前页码

### 响应信息
```json
{
    "requestId": "df4ae453-6e7d-45a7-bc99-c25ff636e7e5",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "name": "师姐，我不做门派第一了",
                "aliasName": "师姐，我不做门派第一了",
                "protagonist": "",
                "categoryId": 4,
                "categoryName": "玄幻",
                "author": "小铜钱",
                "aliasAuthor": "小铜钱",
                "isEnd": 2,
                "chapterNum": 111,
                "introduce": "雁山派掌门从山下捡来根骨绝佳的孩子，取名雁心，把她托给大师姐柳云，让她传授雁山派基础武功于她，这也太耽误练功了，柳云一边揣测是因为自己天资笨拙被师父放弃，一边却坚守大师姐的职责，用心带练雁心，使其成为了门派第一。师妹的反超似乎打破了二人原有的关系，此时门派也开始内外受难……",
                "picture": "/1/1139/cover/1a85bf.webp",
                "status": 1,
                "score": 9.1,
                "chapterName": "02 师姐难当",
                "chapterUpdateTime": "2024-11-22T10:02:58+08:00",
                "chapter": 1,
                "chapterId": 81980,
                "createBy": 1,
                "device": "1234567890",
                "id": 584878,
                "cartoonId": 1139,
                "lastReadtime": "2025-05-09T18:37:45+08:00"
            }
        ]
    }
}
```

## 3. 删除阅读历史记录

### 接口说明
删除指定的阅读历史记录。

### 请求信息
- 请求路径：`/api/v1/cartoonhistory/:ids`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - device: 设备号

- 请求参数（路径参数）：
  - ids: 要删除的阅读历史记录ID，多个ID用逗号分隔

### 响应信息
```json
{
    "requestId": "0a5a5267-a15f-40be-afde-b3117faf1feb",
    "code": 200,
    "msg": "删除成功",
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

## 注意事项

1. 无