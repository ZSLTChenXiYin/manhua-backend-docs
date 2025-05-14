# 同步模块 API 文档
1. [同步标签数据](#1-同步标签数据)
2. [同步分类数据](#2-同步分类数据)


## 1. 同步标签数据

### 接口说明
同步标签数据。

### 请求信息
- 请求路径：`/api/v1/sync/tag`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2
  - status: 状态(1.启用,2.禁用)
    - 测试数据: 1

### 响应信息
```json
{
    "requestId": "dc87789d-029e-44b4-8672-2dbd02925c00",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 98,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 27,
                "name": "穿越",
                "sort": 27,
                "status": 1,
                "gender": 1,
                "titlePicture": "",
                "coverPicture": "",
                "syncState": 2,
                "createdAt": "2022-12-25T12:52:26+08:00",
                "updatedAt": "2022-12-25T12:53:16+08:00",
                "createBy": 1,
                "updateBy": 0
            },
            {
                "id": 28,
                "name": "重生",
                "sort": 28,
                "status": 1,
                "gender": 1,
                "titlePicture": "",
                "coverPicture": "",
                "syncState": 2,
                "createdAt": "2022-12-25T12:52:26+08:00",
                "updatedAt": "2022-12-25T12:53:16+08:00",
                "createBy": 1,
                "updateBy": 0
            }
        ]
    }
}
```

## 2. 同步分类数据

### 接口说明
同步分类数据。

### 请求信息
- 请求路径：`/api/v1/sync/category`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2
  - status: 状态(1.启用,2.禁用)
    - 测试数据: 1

### 响应信息
```json
{
    "requestId": "a7c538ab-ad3f-49b4-a8eb-3fe6a0585b4a",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 34,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 25,
                "gender": 2,
                "pid": 0,
                "name": "恋爱",
                "pinyin": "lianai",
                "picture": "static/cate/5c7ce3.png",
                "keywords": "",
                "description": "",
                "weight": 5,
                "status": 1,
                "syncState": 1,
                "cartoonCategorys": null,
                "createdAt": "2022-12-27T11:23:47+08:00",
                "updatedAt": "2024-09-14T08:30:48+08:00",
                "createBy": 1,
                "updateBy": 1
            },
            {
                "id": 4,
                "gender": 1,
                "pid": 0,
                "name": "玄幻",
                "pinyin": "xuanhuan",
                "picture": "static/cate/7f08b0.png",
                "keywords": "",
                "description": "",
                "weight": 7,
                "status": 1,
                "syncState": 1,
                "cartoonCategorys": null,
                "createdAt": "2022-12-27T11:20:21+08:00",
                "updatedAt": "2024-09-14T08:32:53+08:00",
                "createBy": 1,
                "updateBy": 1
            }
        ]
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

1. 无