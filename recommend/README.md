# 主机模块 API 文档
- [推荐信息与话题列表](#推荐信息与话题列表)
  - [1. 漫画推荐列表](#1-漫画推荐列表)
  - [2. 获取话题列表](#2-获取话题列表)
- [推荐评论](#推荐评论)
- [处理推荐相关信息](#处理推荐相关信息)

## 推荐信息与话题列表

## 1. 漫画推荐列表

### 接口说明
获取漫画推荐。

### 请求信息
- 请求路径：`/api/v1/recommend`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - platformId: 推广平台ID
- 请求参数（表单数据）：
  - pageIndex: 页码
  - pageSize: 每页记录数
  - memberId: 用户ID（可选），用于查询会员用户增加的推荐列表
  - topicId: 主题ID（1-4）
    - 1: 热门推荐
    - 2: 快乐找番
    - 3: 神奇吐槽
    - 4: 聊天话题
  - type: 类型（1-推荐，2-热议）

### 响应信息
```json
{
    "requestId": "b22cbeba-cc5a-4bb6-b357-23cd51fc7d0b",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1459,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "Member": {
                    "memberId": 406670,
                    "nickname": "用户80941051",
                    "avatar": ""
                },
                "cartoon": {
                    "cartoonId": 4655,
                    "cartoonName": "传武",
                    "categoryName": "恐怖",
                    "cartoonPic": "/3/4655/cover/9f7oh7.webp",
                    "cartoonScore": 9.7,
                    "cartoonAuthor": "GK工坊",
                    "cartoonTotal": 467,
                    "cartoonIsEnd": 2,
                    "lastName": "第467话 第三卷 150 百川归海 "
                },
                "id": 4253,  // 推荐ID（recommendId）
                "type": 0,
                "content": "好看好看！",
                "commentCount": 0,
                "likeCount": 1,
                "isLike": 0,
                "createdAt": "2025-03-16T18:59:26+08:00",
                "status": 1
            },
            {
                "Member": {
                    "memberId": 189032,
                    "nickname": "用户11897528",
                    "avatar": ""
                },
                "cartoon": {
                    "cartoonId": 4805,
                    "cartoonName": "一人之下",
                    "categoryName": "冒险",
                    "cartoonPic": "/3/4805/cover/8ks55n.webp",
                    "cartoonScore": 9.6,
                    "cartoonAuthor": "米二",
                    "cartoonTotal": 750,
                    "cartoonIsEnd": 2,
                    "lastName": "708 去第二页吧 "
                },
                "id": 4250,
                "type": 0,
                "content": "非常好看",
                "commentCount": 0,
                "likeCount": 0,
                "isLike": 0,
                "createdAt": "2025-03-16T17:06:05+08:00",
                "status": 1
            }
        ]
    }
}
```

## 2. 获取话题列表

### 接口说明
获取话题列表。

### 请求信息
- 请求路径：`/api/v1/recommend/topic`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（表单数据）：
  - name: 名称（为空获取话题列表所有信息，填写后会进行定向搜索）
  - sortOrder: 排序方式（建议不填，或直接填写desc）

### 响应信息
```json
{
    "code": 200,
    "data": {
        "count": 4,
        "list": [
            {
                "id": 1,
                "name": "热门推荐",
                "sort": 99,
                "status": 1,
                "createdAt": "2024-09-23T15:53:35+08:00",
                "updatedAt": "2024-09-23T15:53:35+08:00",
                "createBy": 1,
                "updateBy": 0
            },
            {
                "id": 2,
                "name": "快乐找番",
                "sort": 98,
                "status": 1,
                "createdAt": "2024-09-23T15:53:43+08:00",
                "updatedAt": "2024-09-23T15:53:43+08:00",
                "createBy": 1,
                "updateBy": 0
            },
            {
                "id": 3,
                "name": "神奇吐槽",
                "sort": 97,
                "status": 1,
                "createdAt": "2024-09-23T15:53:51+08:00",
                "updatedAt": "2024-09-23T15:53:51+08:00",
                "createBy": 1,
                "updateBy": 0
            },
            {
                "id": 4,
                "name": "聊天话题",
                "sort": 96,
                "status": 1,
                "createdAt": "2024-09-23T15:55:27+08:00",
                "updatedAt": "2024-09-23T15:55:27+08:00",
                "createBy": 1,
                "updateBy": 0
            }
        ]
    },
    "msg": "查询成功",
    "requestId": "b4e93ae7-7355-4479-a145-8e618edc5109"
}
```

## 推荐评论

## 1. 获取漫画推荐评论详情

### 接口说明
获取漫画推荐评论详情。

### 请求信息
- 请求路径：`/api/v1/recommend/comment/:id`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路径参数）：
  - id: 推荐ID（recommendId）

### 响应信息
```json
{
    "requestId": "af82f72e-554e-4c61-a851-507e3881b655",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "id": 0,
        "content": "",
        "like": 0,
        "memberId": 0,
        "rank": 0,
        "avatar": "",
        "nickname": "",
        "level": 0,
        "replyTotal": 0,
        "isLike": 2,
        "medalId": 0,
        "medalLevel": 0,
        "medalPic": "",
        "ruleName": "",
        "replyList": null,
        "updatedAt": "0001-01-01T00:00:00Z",
        "createdAt": "0001-01-01T00:00:00Z",
        "cartoon": {
            "cartoonId": 0,
            "cartoonName": "",
            "categoryName": "",
            "cartoonPic": "",
            "cartoonScore": 0,
            "cartoonAuthor": "",
            "cartoonTotal": 0,
            "cartoonIsEnd": 0,
            "lastName": ""
        }
    }
}
```

## 2. 根据漫画推荐评论id获取评论列表

### 接口说明
根据漫画推荐评论id获取评论列表。

### 请求信息
- 请求路径：`/api/v1/recommend/commentList`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
- 请求参数（表单数据）：
  - pageSize: 每页记录数
  - pageIndex: 页数
  - recommentId: 推荐id，通过“漫画推荐列表”接口获取的List的单个元素中的id
  - sort: 排列方式(1.最新,2.最热,不传默认按照最新排序)

### 响应信息
```json
{
    "requestId": "64f519d2-6a59-4ba2-b9da-f8f7d2d018bb",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 0,
        "pageIndex": 1,
        "pageSize": 10,
        "list": null
    }
}
```

## 处理推荐相关信息