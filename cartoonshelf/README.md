# 书架模块 API 文档

## 1. 加入书架

### 接口说明
加入书架。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/add`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json
  - appId: 应用ID
  - channelId: 渠道ID
- 请求体（json）：
```json
{
  "cartoonIds": "1139",  // 漫画ID，多个漫画ID用逗号分隔
  "chapterIds": "81980"  // 章节ID，多个章节ID用逗号分隔
}
```

### 响应信息
```json
{
    "requestId": "c0263051-1dc4-46c9-9bdc-20da7cccfd55",
    "code": 200,
    "msg": "同步成功",
    "data": [
        6533122  // cartoonshelfId
    ]
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