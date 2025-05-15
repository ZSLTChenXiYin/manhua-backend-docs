# 主机模块 API 文档
- [推荐信息与话题列表](#推荐信息与话题列表)
  1. [漫画推荐列表](#1-漫画推荐列表)
  2. [获取话题列表](#2-获取话题列表)
- [推荐评论](#推荐评论)
  1. [获取漫画推荐评论详情](#1-获取漫画推荐评论详情)
  2. [根据漫画推荐评论id获取评论列表](#2-根据漫画推荐评论id获取评论列表)
  3. [漫画推荐评论回复列表](#3-漫画推荐评论回复列表)
  4. [漫画推荐动态列表](#4-漫画推荐动态列表)
- [处理推荐相关信息](#处理推荐相关信息)
  - [推荐相关](#推荐相关)
    1. [点赞/取消点赞（漫画推荐）](#1-点赞取消点赞漫画推荐)
    2. [推荐举报](#2-推荐举报)
    3. [增加漫画推荐](#3-增加漫画推荐)
    4. [删除漫画推荐](#4-删除漫画推荐)
    5. [更新漫画推荐](#5-更新漫画推荐)
  - [推荐评论相关](#推荐评论相关)
    1. [发表推荐评论](#1-发表推荐评论)
    2. [漫画推荐评论点赞](#2-漫画推荐评论点赞)
    3. [删除自己写的推荐评论](#3-删除自己写的推荐评论)
    4. [根据recommend_id获取我的评论](#4-根据recommend_id获取我的评论)
  - [推荐评论回复相关](#推荐评论回复相关)
    1. [漫画推荐评论发表回复](#1-漫画推荐评论发表回复)
    2. [漫画推荐评论回复删除](#2-漫画推荐评论回复删除)
    3. [漫画推荐评论回复点赞](#3-漫画推荐评论回复点赞)
  - [推荐评论与推荐评论回复相关](#推荐评论与推荐评论回复相关)
    1. [举报评论&举报回复](#1-举报评论举报回复)

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
    - 测试数据: 1
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
  - 示例：
    - pageIndex: 1
    - pageSize: 2
    - topicId: 1
    - type: 1

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
  - 示例：
    - name: 
    - sortOrder: 

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
  - id: 推荐回复ID（recommendcommentId）
  示例：
    - id: 4655

### 响应信息
```json
{
    "requestId": "2ce825fe-3bf7-41b1-a838-e0a75656b44f",
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
// 完整json
{
    "id": 1,
    "content": "这是一条评论内容",
    "like": 10,
    "memberId": 1001,
    "rank": 5,
    "avatar": "https://example.com/avatar.jpg",
    "nickname": "张三",
    "level": 3,
    "replyTotal": 2,
    "isLike": 1,
    "medalId": 5,
    "medalLevel": 2,
    "medalPic": "https://example.com/medal.jpg",
    "ruleName": "荣誉勋章",
    "replyList": [
        {
            "commentId": 101,
            "replyId": 201,
            "memberId": 1002,
            "avatar": "https://example.com/avatar2.jpg",
            "nickname": "李四",
            "level": 2,
            "status": 1,
            "content": "这是一条回复",
            "like": 3,
            "isLike": 0,
            "createdAt": "2024-01-01T00:00:00Z",
            "parent": {
                "replyId": 101,
                "memberId": 1001,
                "nickname": "张三",
                "level": 3,
                "status": 1,
                "content": "这是一条评论内容"
            }
        }
    ],
    "updatedAt": "2024-01-02T00:00:00Z",
    "createdAt": "2024-01-01T00:00:00Z",
    "cartoon": {
        "cartoonId": 2001,
        "cartoonName": "漫画名称",
        "categoryName": "漫画分类",
        "cartoonPic": "https://example.com/cartoon.jpg",
        "cartoonScore": 8.5,
        "cartoonAuthor": "作者姓名",
        "cartoonTotal": 50,
        "cartoonIsEnd": 1,
        "lastName": "最新章节名称"
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
  - 示例：
    - pageSize: 10
    - pageIndex: 1
    - recommentId: 7
    - sort: 1

### 响应信息
```json
{
    "requestId": "45574670-481f-4454-a50c-25829e5e8d1a",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 29,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "id": 3846,
                "content": "才买了他的实体书",
                "like": 0,
                "memberId": 354219,
                "rank": 0,
                "avatar": "/static/avatar/355/354219/sch760.png",
                "nickname": "兑狱",
                "level": 0,
                "replyTotal": 0,
                "isLike": 2,
                "medalId": 0,
                "medalLevel": 0,
                "medalPic": "",
                "ruleName": "",
                "replyList": [],  // 参考上文中的该字段
                "updatedAt": "2025-02-18T16:50:23+08:00",
                "createdAt": "2025-02-18T16:50:22+08:00",
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
            },
            {
                "id": 3686,
                "content": "搞钱的看这里ywa76.cc",
                "like": 0,
                "memberId": 343302,
                "rank": 0,
                "avatar": "/static/avatar/344/343302/hlsekb.png",
                "nickname": "用户11318363",
                "level": 0,
                "replyTotal": 0,
                "isLike": 2,
                "medalId": 0,
                "medalLevel": 0,
                "medalPic": "",
                "ruleName": "",
                "replyList": [],
                "updatedAt": "2025-02-16T06:29:30+08:00",
                "createdAt": "2025-02-16T06:29:29+08:00",
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
            },
            // ... 其他评论
        ]
    }
}
```

## 3. 漫画推荐评论回复列表

### 接口说明
获取漫画推荐评论回复列表。

### 请求信息
- 请求路径：`/api/v1/recommend/commentreplyList`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
    - 测试数据: 1234567890
- 请求参数（表单数据）：
  - pageIndex: 页数
  - commentId: 评论id
  - 示例：
    - pageIndex: 1
    - commentId: 3846

### 响应信息
```json
{
    "requestId": "63b938b0-bf70-4ea3-901a-bc57256c88cd",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 0,
        "pageIndex": 1,
        "pageSize": 10,
        "list": null
    }
}
// 完整结构
{
    "requestId": "63b938b0-bf70-4ea3-901a-bc57256c88cd",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "replyId": 1,
                "memberId": 1001,
                "avatar": "https://example.com/avatar.jpg",
                "nickname": "JohnDoe",
                "level": 5,
                "status": 2,
                "content": "这是一条回复内容",
                "like": 10,
                "isLike": 1,
                "createdAt": "2024-01-01T12:00:00Z",
                "parentId": 2,
                "parent": {
                    "replyId": 2,
                    "memberId": 1002,
                    "nickname": "JaneDoe",
                    "level": 3,
                    "status": 2,
                    "content": "这是父级回复内容"
                }
            },
            // ... 其他回复
        ]
    }
}
```

## 4. 漫画推荐动态列表

### 接口说明
获取漫画推荐动态列表。

### 请求信息
- 请求路径：`/api/v1/recommend/dynamic`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}  // 可选
- 请求参数（表单数据）：
  - pageIndex: 页数
  - pageSize: 每页记录数
  - memberId: 用户ID（可选），用于查询会员用户增加的推荐列表
  - 示例：
    - pageIndex: 1
    - pageSize: 10
    - memberId: 354219

### 响应信息
```json
{
    "requestId": "0c983244-c7aa-47c4-a6c4-29d4f83eaa37",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 0,  // list大小
        "pageIndex": 1,
        "pageSize": 10,
        "list": []
    }
}
// 完整结构
{
    "requestId": "0c983244-c7aa-47c4-a6c4-29d4f83eaa37",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "Member": {
                    "memberId": 1,
                    "nickname": "示例用户",
                    "avatar": "https://example.com/avatar.jpg"
                },
                "cartoon": {
                    "cartoonId": 100,
                    "cartoonName": "示例漫画",
                    "categoryName": "漫画分类",
                    "cartoonPic": "https://example.com/cartoon.jpg",
                    "cartoonScore": 8.5,
                    "cartoonAuthor": "示例作者",
                    "cartoonTotal": 50,
                    "cartoonIsEnd": 1,
                    "lastName": "最新章节名称"
                },
                "id": 123,
                "type": 1,
                "content": "这是一条漫画推荐内容",
                "commentCount": 20,
                "likeCount": 50,
                "isLike": 1,
                "createdAt": "2024-01-01T12:00:00Z",
                "status": 1
            },
            // ... 其他动态
        ]
    }
}
```

## 处理推荐相关信息

## 推荐相关

## 1. 点赞/取消点赞（漫画推荐）

### 接口说明
用户对漫画推荐进行点赞或取消点赞操作。

### 请求信息
- 请求路径：`/api/v1/recommend/like`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
- 请求参数（json）：
```json
{
  "recommendId": 7,
  "type": 1  // 1: 点赞, 2: 取消点赞
}
```

### 响应信息
```json
{
    "requestId": "4176ff51-bad4-4655-8235-12eeed618d7f",
    "code": 200,
    "msg": "点赞成功",
    "data": null
}
```

## 2. 推荐举报

### 接口说明
用户对漫画推荐进行举报操作。

### 请求信息
- 请求路径：`/api/v1/recommend/report`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
- 请求参数（json）：
```json
{
  "recommendId": 7,
  "type": 1  // 相似内容太多:1, 内容质量太差:2
}
```

### 响应信息
```json
{
    "requestId": "8a82a2e5-0be7-4281-9c4f-ca35f040f04b",
    "code": 200,
    "msg": "举报成功",
    "data": null
}
```

## 3. 增加漫画推荐

### 接口说明
用户增加漫画推荐。

### 请求信息
- 请求路径：`/api/v1/recommend/add`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID
    - 测试数据: 107
  - platformId: 平台ID
    - 测试数据: 1
- 请求参数（json）：
```json
{
  "cartoonId": 3687,
  "content": "风起苍岚很棒哦。",
  "topicIds": "1"
}
```

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "新增成功",
    "data": null
}
```

## 4. 删除漫画推荐

### 接口说明
用户删除漫画推荐。

### 请求信息
- 请求路径：`/api/v1/recommend/del`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
- 请求参数（json）：
```json
{
  "recommendId": 1
}
```

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "删除成功",
    "data": null
}
```

## 5. 更新漫画推荐

### 接口说明
用户更新漫画推荐。

### 请求信息
- 请求路径：`/api/v1/recommend/update`
- 请求方法：PUT
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID
    - 测试数据: 107
  - platformId: 平台ID
    - 测试数据: 1
- 请求参数（json）：
```json
{
  "recommendId": 1,
  "cartoonId": 3687,
  "content": "风起苍岚真的很棒哦。"
}
```

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "新增成功",
    "data": null
}
```

## 推荐评论相关

## 1. 发表推荐评论

### 接口说明
用户发表漫画推荐评论。

### 请求信息
- 请求路径：`/api/v1/recommend/comment`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
    - 测试数据: 1234567890
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（json）：
```json
{
  "content": "是的",
  "recommendId": 1,
  "cartoonId": 3687
}
```

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "评论成功",
    "data": null
}
```

## 2. 漫画推荐评论点赞

### 接口说明
用户对漫画推荐评论进行点赞或取消点赞操作。

### 请求信息
- 请求路径：`/api/v1/recommend/comment/like`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（json）：
```json
{
  "id": 1,  // 评论id
  "type": 1  // 1.点赞, 2.取消点赞
}
```

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "操作成功",
    "data": null
}
```

## 3. 删除自己写的推荐评论

### 接口说明
用户删除自己写的漫画推荐评论。

### 请求信息
- 请求路径：`/api/v1/recommend/comment/:id`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
    - 测试数据: 1234567890

### 响应信息
```json
{
    "requestId": "28bba5b9-e186-4f23-bd1b-56b62c9acf09",
    "code": 200,
    "msg": "删除成功",
    "data": null
}
```

## 4. 根据recommend_id获取我的评论

### 接口说明
根据recommend_id获取我的评论。

### 请求信息
- 请求路径：`/api/v1/recommend/commentDetail`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
- 请求参数（表单数据）：
  - recommendId: 推荐id
  - 示例：
    - recommendId: 1

### 响应信息
```json
{
    "requestId": "09c1cf81-808a-459e-bbb4-e0900064fad3",
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
        "updatedAt": "2024-01-01T00:00:00Z",
        "createdAt": "2024-01-01T00:00:00Z",
        "status": 0,
        "isLike": 0,
        "replyList": [
            {
                "commentId": 0,
                "replyId": 0,
                "memberId": 0,
                "nickname": "",
                "status": 0,
                "content": "",
                "level": 0,
                "avatar": "",
                "like": 0,
                "isLike": 0,
                "createdAt": "2024-01-01T00:00:00Z",
                "parentId": 0,
                "parent": {
                    "replyId": 0,
                    "memberId": 0,
                    "nickname": "",
                    "status": 0,
                    "content": "",
                    "level": 0
                }
            }
        ]
    }
}
```

## 推荐评论回复相关

## 1. 漫画推荐评论发表回复

### 接口说明
用户对漫画推荐评论进行回复。

### 请求信息
- 请求路径：`/api/v1/recommend/commentReply`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - device: 设备号
    - 测试数据: 1234567890
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（json）：
```json
{
  "commentId": 7,
  "content": "OvO",
  "id": 1,
  "replyId": 1
}
```

### 响应信息
```json
{
    "requestId": "a3fe9263-98b9-4c60-a825-601a26972faf",
    "code": 200,
    "msg": "发表成功",
    "data": ""
}
```

## 2. 漫画推荐评论回复删除

### 接口说明
用户删除漫画推荐评论回复。

### 请求信息
- 请求路径：`/api/v1/recommend/commentReply/:id`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}

### 响应信息
```json
{
    "requestId": "a3fe9263-98b9-4c60-a825-601a26972faf",
    "code": 200,
    "msg": "删除成功",
    "data": ""
}
```

## 3. 漫画推荐评论回复点赞

### 接口说明
用户对漫画推荐评论回复进行点赞或取消点赞操作。

### 请求信息
- 请求路径：`/api/v1/recommend/commentReply/like`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（json）：
```json
{
  "replyId": 1,
  "type": 1,  // 1.点赞, 2.取消点赞
  "appId": 107
}
```

### 响应信息
```json
{
    "requestId": "1a2bf290-75fe-4c4c-8d51-783a82468ff5",
    "code": 200,
    "msg": "已点赞成功",
    "data": {
        "before": false
    }
}
```

## 推荐评论与推荐评论回复相关

## 1. 举报评论&举报回复

### 接口说明
用户对漫画推荐评论或回复进行举报操作。

### 请求信息
- 请求路径：`/api/v1/recommend/commentreport`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID
    - 测试数据: 107
  - device: 设备号
    - 测试数据: 1234567890
- 请求参数（json）：
```json
{
  "id": 7,
  "type": 1,  // 1.评论, 2.回复
  "typeCode": 4 // 举报类型,1.广告诈骗,2.政治敏感,3.色情暴力,4.其他
}
```

### 响应信息
```json
{
    "requestId": "19615ffb-b527-4d5a-a254-227cf335d4eb",
    "code": 200,
    "msg": "举报成功",
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
