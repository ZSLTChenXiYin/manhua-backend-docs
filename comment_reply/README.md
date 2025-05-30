# 漫评回复模块 API 文档
1. [评论回复列表](#1-评论回复列表)
2. [发表回复](#2-发表回复)
3. [点赞回复](#3-点赞回复)
4. [删除回复](#4-删除回复)

## 1. 评论回复列表

### 接口说明
根据评论id获取评论回复列表

### 请求信息
- 请求路径：`/api/v1/comment-reply/list`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
- 请求参数（路由参数）：
  - commentId: 漫评id
  - pageIndex: 页码
  - pageSize: 每页大小
  - 示例：
    - commentId: 2321
    - page: 1
    - size: 10

### 响应信息
```json
{
    "requestId": "99bb05ae-ab22-4c18-a8a4-08b3e08f2fad",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 4,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "replyId": 8114,
                "memberId": 411936,
                "nickname": "速冻心脏冻干",
                "status": 1,
                "content": "我也想说，我从小学二三年级开始看，现在高二了还没更完",
                "level": 0,
                "avatar": "/static/avatar/412/411936/5aksm0.png",
                "like": 0,
                "isLike": 2,
                "createdAt": "2025-03-07T08:57:05+08:00",
                "parentId": 0,
                "parent": {
                    "replyId": 0,
                    "memberId": 0,
                    "nickname": "",
                    "status": 0,
                    "content": "",
                    "level": 0
                }
            },
            {
                "replyId": 7991,
                "memberId": 351488,
                "nickname": "用户32495997",
                "status": 1,
                "content": "我都大二了",
                "level": 0,
                "avatar": "",
                "like": 0,
                "isLike": 2,
                "createdAt": "2025-03-02T19:13:01+08:00",
                "parentId": 0,
                "parent": {
                    "replyId": 0,
                    "memberId": 0,
                    "nickname": "",
                    "status": 0,
                    "content": "",
                    "level": 0
                }
            },
            // ... 其他回复
        ]
    }
}
```

## 2. 发表回复

### 接口说明
发表漫画推荐评论回复
### 请求信息
- 请求路径：`/api/v1/comment-reply`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
  - appId: 应用id
  - channelId: 渠道
- 请求参数（json）：
```json
{
  "commentId": 2321,
  "replyId": ,  // 父级回复id（就是@某个人的漫评回复），可选（有就写，没有就删除该字段）
  "content": "我也很早就开始看了，现在也没更完。"
}
```

### 响应信息
```json
{
    "requestId": "7ba0b6b0-d1fe-431d-a7ac-36bfb2cede98",
    "code": 200,
    "msg": "发表成功",
    "data": null
}
```

## 3. 点赞回复

### 接口说明
漫画推荐评论回复点赞
### 请求信息
- 请求路径：`/api/v1/comment-reply/like`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
  - channelId: 渠道
  - appId: 应用id
- 请求参数（json）：
```json
{
  "id": 20367,
  "type": 1 // 1.点赞,2.取消点赞
}
```

### 响应信息
```json
{
    "requestId": "8058a1c7-3f29-47d5-87fe-53cd5a18f453",
    "code": 200,
    "msg": "操作成功",
    "data": {
        "before": false
    }
}
```

## 4. 删除回复

### 接口说明
漫画推荐评论回复删除

### 请求信息
- 请求路径：`/api/v1/comment-reply/:id`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
- 请求参数（路由参数）：
  - id: 回复id
  - 示例：
    - id: 8689

### 响应信息
```json
{
    "requestId": "336b8e52-17c5-4dc6-8a4b-bc3d9639a732",
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
