# 首页模块 API 文档

## 1. 获取首页公告信息

### 接口说明
获取首页公告信息，包括公告ID、标题和内容。

### 请求信息
- 请求路径：`/api/v1/home`
- 请求方法：GET
- 请求头：
  - device: 设备号

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": {
        "id": 1, // 公告ID
        "title": "公告标题",
        "content": "公告内容"
    }
}
```

## 2. 设置首页公告已读

### 接口说明
标记首页公告为已读状态。

### 请求信息
- 请求路径：`/api/v1/homeRead`
- 请求方法：POST
- 请求头：
  - device: 设备号
- 请求参数：
```json
{
    "id": 1  // 公告ID
}
```

### 响应信息
```json
{
    "code": 200,
    "message": "success",
    "data": null
}
```

## 3. 获取首页推荐内容

### 接口说明
获取首页推荐内容，包括漫画推荐、话题推荐等。

### 请求信息
- 请求路径：`/api/v1/recommend`
- 请求方法：GET
- 请求头：
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
    "code": 200,
    "message": "success",
    "data": {
        "count": 1459,
        "pageIndex": 1,
        "pageSize": 10,
        "list": [
            {
                "Member": {
                    "memberId": 406670,
                    "nickname": "用户80941051",
                    "avatar": "" // 头像URL，为空时使用默认头像
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
                "id": 4253,
                "type": 0,
                "content": "好看好看！",
                "commentCount": 0,
                "likeCount": 1,
                "isLike": 0,
                "createdAt": "2025-03-16T18:59:26+08:00",
                "status": 1
            },
            // ...
            // List数据长度和pageSize相关
        ]
    }
}
```

## 错误码说明

| 错误码 | 说明 |
|--------|------|
| 0 | 成功 |
| 400 | 请求参数错误 |
| 401 | 未认证或认证失败 |
| 403 | 无权限访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

## 注意事项

1. 首页公告信息会根据设备首次使用时间进行过滤
2. 公告已读状态会记录在数据库中
3. 推荐内容支持分页加载
4. 广告配置支持多平台、多渠道配置
5. 广告展示时间间隔可配置
6. 推荐内容支持多种类型（推荐、热议等）
7. 推荐内容支持按用户ID筛选
8. 推荐内容支持按主题ID筛选
9. 广告配置支持JSON格式的灵活配置
10. 所有接口都需要进行签名验证 