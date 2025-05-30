# 漫评模块 API 文档
1. [根据漫画id获取评论列表](#1-根据漫画id获取评论列表)
2. [评论详情](#2-评论详情)
3. [ta的影评/我的影评](#3-ta的影评我的影评)
4. [发表评论](#4-发表评论)
5. [点赞](#5-点赞)
6. [删除评论](#6-删除评论)

## 1. 根据漫画id获取评论列表

### 接口说明
根据漫画id获取评论列表

### 请求信息
- 请求路径：`/api/v1/comment/list`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
- 请求参数（表单数据）：
	- pageIndex: 页面数
	- pageSize: 页面显示数量
	- cartoonId: 漫画id
	- sort: 排序,1.最新,2.最热
  - 示例：
    - pageIndex: 1
    - pageSize: 10
    - cartoonId: 3687
    - sort: 1

### 响应信息
```json
{
    "requestId": "5fbb5273-8afa-45d3-bf96-88cb849aabdc",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 5,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "id": 7332,
                "content": "居然还没更完？",
                "like": 5,
                "memberId": 130716,
                "rank": 5,
                "avatar": "/static/avatar/131/130716/amyl9d.png",
                "nickname": "ddd",
                "level": 0,
                "replyTotal": 0,
                "updatedAt": "2025-01-26T15:15:31+08:00",
                "createdAt": "2025-01-26T15:15:32+08:00",
                "status": 1,
                "isLike": 2,
                "replyList": []
            },
            {
                "id": 2321,
                "content": "不是，我小学的时候这部漫画还在我都上高中快毕业，这部漫画还没更完吗？",
                "like": 13,
                "memberId": 116210,
                "rank": 5,
                "avatar": "",
                "nickname": "用户70909167",
                "level": 0,
                "replyTotal": 4,
                "updatedAt": "2024-12-30T01:33:31+08:00",
                "createdAt": "2024-12-30T01:33:31+08:00",
                "status": 1,
                "isLike": 2,
                "replyList": [
                    {
                        "commentId": 2321,
                        "replyId": 8114,
                        "memberId": 411936,
                        "nickname": "速冻心脏冻干",
                        "level": 0,
                        "status": 1,
                        "content": "我也想说，我从小学二三年级开始看，现在高二了还没更完",
                        "avatar": "/static/avatar/412/411936/5aksm0.png",
                        "like": 0,
                        "isLike": 2,
                        "createdAt": "2025-03-07T08:57:05+08:00",
                        "parentId": 0,
                        "parent": {
                            "replyId": 0,
                            "memberId": 0,
                            "nickname": "",
                            "level": 0,
                            "status": 0,
                            "content": ""
                        }
                    },
                    {
                        "commentId": 2321,
                        "replyId": 7991,
                        "memberId": 351488,
                        "nickname": "用户32495997",
                        "level": 0,
                        "status": 1,
                        "content": "我都大二了",
                        "avatar": "",
                        "like": 0,
                        "isLike": 2,
                        "createdAt": "2025-03-02T19:13:01+08:00",
                        "parentId": 0,
                        "parent": {
                            "replyId": 0,
                            "memberId": 0,
                            "nickname": "",
                            "level": 0,
                            "status": 0,
                            "content": ""
                        }
                    },
                    {
                        "commentId": 2321,
                        "replyId": 4550,
                        "memberId": 279381,
                        "nickname": "用户93342013",
                        "level": 0,
                        "status": 1,
                        "content": "我都毕业工作了，都还没更完",
                        "avatar": "",
                        "like": 0,
                        "isLike": 2,
                        "createdAt": "2025-02-07T04:16:47+08:00",
                        "parentId": 0,
                        "parent": {
                            "replyId": 0,
                            "memberId": 0,
                            "nickname": "",
                            "level": 0,
                            "status": 0,
                            "content": ""
                        }
                    }
                ]
            }
        ]
    }
}
```

## 2. 评论详情

### 接口说明
根据评论id获取评论详情

### 请求信息
- 请求路径：`/api/v1/comment/info/:id`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
  - appId: 应用id
  - channelId: 渠道
  - platformId: 平台
- 请求参数（路径参数）：
  - id: 评论id
  - 示例：
    - id: 2321

### 响应信息
```json
{
    "requestId": "ae5077c7-db91-40c9-bdef-b0b56c8276b2",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "id": 2321,
        "content": "不是，我小学的时候这部漫画还在我都上高中快毕业，这部漫画还没更完吗？",
        "like": 13,
        "rank": 5,
        "avatar": "",
        "nickname": "用户70909167",
        "level": 0,
        "replyTotal": 4,
        "updatedAt": "2024-12-30T01:33:31+08:00",
        "createdAt": "2024-12-30T01:33:31+08:00",
        "memberId": 116210,
        "status": 1,
        "isLike": 2
    }
}
```

## 3. ta的影评/我的影评

### 接口说明
根据用户id获取ta的影评/我的影评

### 请求信息
- 请求路径：`/api/v1/comment/otherlist`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
- 请求参数（路由参数）：
  - pageIndex: 页面数
  - pageSize: 页面显示数量
  - memberId: 用户id(id填自己就是自己的漫评，填谁的id就是谁的漫评)
  - 示例：
    - pageIndex: 1
    - pageSize: 10
    - memberId: 116210

### 响应信息
```json
{
    "requestId": "d4d08677-30d1-4c46-a510-3f049d81f4ae",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "commentId": 2321,
                "content": "不是，我小学的时候这部漫画还在我都上高中快毕业，这部漫画还没更完吗？",
                "commentStatus": 1,
                "like": 13,
                "isLike": 2,
                "replyTotal": 4,
                "cartoonId": 3687,
                "cartoonName": "风起苍岚",
                "cartoonStatus": 1,
                "cartoonDeletedAt": "",
                "picture": "/2/3687/cover/qpa5n2.webp",
                "createdAt": "2024-12-30T01:33:31+08:00"
            }
        ]
    }
}
```

## 4. 发表评论

### 接口说明
发表评论
### 请求信息
- 请求路径：`/api/v1/comment`
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
  "cartoonId": 1139,
  "content": "画得好棒！",
  "rank": 5  // 1-5分
}
```

### 响应信息
```json
{
    "requestId": "deebcec9-d3ad-4f44-8dfa-5b89b24cea0a",
    "code": 200,
    "msg": "评论成功",
    "data": null
}
```

## 5. 点赞

### 接口说明
点赞

### 请求信息
- 请求路径：`/api/v1/comment/like`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用id
  - channelId: 渠道
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
    "requestId": "9ffc740a-3258-48d7-b18f-1a1ad5ddc29d",
    "code": 200,
    "msg": "操作成功",
    "data": {
        "before": false
    }
}
```

## 6. 删除评论

### 接口说明
删除评论

### 请求信息
- 请求路径：`/api/v1/comment/:id`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
- 请求参数（路径参数）：
  - id: 评论id
  - 示例：
    - id: 20367

### 响应信息
```json
{
    "requestId": "97793258-2e00-42ba-8882-cd87f09a0a6c",
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
