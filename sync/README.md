# 同步模块 API 文档

## 1. 漫画站群同步漫画数据

### 接口说明
同步漫画数据。

### 请求信息
- 请求路径：`/api/v1/sync/cartoon`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - status: 状态(1.启用,2.禁用)
    - 测试数据: 1
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2

### 响应信息
```json
{
    "requestId": "cf17d48c-44b9-4608-a5a8-b6670b365877",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 4906,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 3860,
                "categoryId": 25,
                "category": "校园",
                "name": "学霸哥哥别碰我",
                "aliasName": "学霸哥哥别碰我",
                "pinyin": "xuebagegebiepengwo",
                "author": "蜜夏动漫",
                "aliasAuthor": "蜜夏动漫",
                "protagonist": "",
                "status": 1,
                "recommend": 2,
                "sStatus": 1,
                "syncState": 1,
                "isEnd": 1,
                "heat": 0,
                "chapterNum": 107,
                "picture": "2/3860/cover/6k4s61.webp",
                "posterPic": "",
                "introduce": "什么？转学的第一天，竟然...",
                "areaId": 1,
                "collectionNum": 0,
                "chapterId": 197885,
                "chapterName": "第107回",
                "chapterUpdateTime": "2024-10-10T17:17:37+08:00",
                "chapterCountErr": 0,
                "sourceCartoonId": "2406",
                "lastSourceCartoonId": "2406",
                "ruleId": 14,
                "lastRuleId": 14,
                "score": 9,
                "view": 471,
                "pv": 283,
                "cartoonshelf": 79,
                "yesterday": 0,
                "lastWeek": 1,
                "lastMonth": 4,
                "commentNum": 0,
                "chapterInfo": [
                    {
                        "name": "默认章节",
                        "sort": 0
                    }
                ],
                "sourceCategories": "爱情,校园,大陆",
                "updateCycle": "",
                "areaName": "",
                "categoryName": "",
                "tagIds": null,
                "createdAt": "2024-10-10T17:16:31+08:00",
                "updatedAt": "2025-03-16T13:10:50+08:00",
                "createBy": 1,
                "updateBy": 0
            },
            {
                "id": 10420,
                "categoryId": 1,
                "category": "",
                "name": "蝴蝶，俘获老虎",
                "aliasName": "蝴蝶，俘获老虎",
                "pinyin": "hudiefuhuolaohu",
                "author": "Mindal Park",
                "aliasAuthor": "Mindal Park",
                "protagonist": "",
                "status": 1,
                "recommend": 2,
                "sStatus": 1,
                "syncState": 1,
                "isEnd": 2,
                "heat": 0,
                "chapterNum": 74,
                "picture": "6/10420/cover/6xilyb.webp",
                "posterPic": "",
                "introduce": "外表叛逆内里二缺的乐队主唱许延浩，在被好友居然是同志的这个事实，打击到失神狂奔的时候。撞上了引渡灵魂的阴差韩律，向来厌恶人类的韩律第一次产生了想要了解一个人的冲动。这份冲动的背后是好奇还是有别的心思？",
                "areaId": 1,
                "collectionNum": 0,
                "chapterId": 38974,
                "chapterName": "75.外传终",
                "chapterUpdateTime": "2024-10-15T21:31:46+08:00",
                "chapterCountErr": 0,
                "sourceCartoonId": "21400",
                "lastSourceCartoonId": "21400",
                "ruleId": 14,
                "lastRuleId": 14,
                "score": 9.1,
                "view": 683,
                "pv": 1092,
                "cartoonshelf": 370,
                "yesterday": 0,
                "lastWeek": 1,
                "lastMonth": 1,
                "commentNum": 2,
                "chapterInfo": [
                    {
                        "name": "默认章节",
                        "sort": 0
                    }
                ],
                "sourceCategories": "其它",
                "updateCycle": "",
                "areaName": "",
                "categoryName": "",
                "tagIds": null,
                "createdAt": "2024-10-15T21:29:49+08:00",
                "updatedAt": "2025-03-16T13:14:10+08:00",
                "createBy": 1,
                "updateBy": 0
            }
        ]
    }
}
```

## 2. 同步漫画标签数据

### 接口说明
同步漫画章节数据。

### 请求信息
- 请求路径：`/api/v1/sync/cartoonTag`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2

### 响应信息
```json
{
    "requestId": "a8229114-324a-40df-947a-4cde4fb4ddec",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 33264,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "cartoonId": 2,
                "tagId": 41,
                "syncState": 2,
                "updatedAt": "2024-09-19T15:49:53+08:00"
            },
            {
                "cartoonId": 3,
                "tagId": 41,
                "syncState": 2,
                "updatedAt": "2024-09-19T15:52:46+08:00"
            }
        ]
    }
}
```

## 3. 同步标签数据

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

## 4. 同步分类数据

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

## 5. 同步漫画分类数据

### 接口说明
同步漫画分类数据。

### 请求信息
- 请求路径：`/api/v1/sync/cartoonCategory`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2

### 响应信息
```json
{
    "requestId": "cdb1ece6-9090-499f-b08b-c12516a3cf1f",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 62,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 1,
                "categoryId": 2,
                "name": "热血",
                "syncState": 2,
                "updatedAt": "2022-05-11T09:42:51+08:00"
            },
            {
                "id": 3,
                "categoryId": 4,
                "name": "玄幻",
                "syncState": 2,
                "updatedAt": "2022-05-11T09:42:51+08:00"
            }
        ]
    }
}
```

## 6. 同步漫画章节数据

### 接口说明
同步漫画章节数据。

### 请求信息
- 请求路径：`/api/v1/sync/cartoonChapter`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（路由参数）：
  - record: 时间戳（从时间戳的时间开始同步数据）
  - pageIndex: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2
  - tableName: 表名
    - 测试数据: cartoon_chapter2

### 响应信息
```json
{
    "requestId": "7bb5004c-6ac6-4a6a-83f8-20950b2d7439",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "count": 238810,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 16,
                "cartoonId": 2001,
                "pictures": "2/2001/cpt/16/y8wuss.webp|2/2001/cpt/16/6lphcj.webp|2/2001/cpt/16/0ykdeh.webp|2/2001/cpt/16/sz57ox.webp|2/2001/cpt/16/oogog1.webp|2/2001/cpt/16/pdv0a0.webp|2/2001/cpt/16/k4vjpm.webp|2/2001/cpt/16/zh3xvg.webp|2/2001/cpt/16/mcp9qx.webp|2/2001/cpt/16/vcajzh.webp|2/2001/cpt/16/u8xt3l.webp|2/2001/cpt/16/3dhlmr.webp|2/2001/cpt/16/yioc2j.webp|2/2001/cpt/16/1ytq2u.webp|2/2001/cpt/16/p4zpw2.webp|2/2001/cpt/16/2s6okm.webp|2/2001/cpt/16/djebzs.webp|2/2001/cpt/16/bvpxnb.webp|2/2001/cpt/16/eds43j.webp|2/2001/cpt/16/ibc0a1.webp|2/2001/cpt/16/noqa31.webp",
                "picsizes": "491,857|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,800|491,874",
                "pictureNum": 21,
                "ruleId": 6,
                "sourceChapterId": "73",
                "sourceCartoonId": "manga-yt69577",
                "name": "第208回 走向光明 ",
                "coverPicture": "2/2001/cpt/16/y8wuss.webp",
                "status": 1,
                "uploadStatus": 0,
                "sort": 73,
                "chapterSort": 0,
                "isFree": 1,
                "createdAt": "2024-10-01T10:25:26+08:00",
                "updatedAt": "2024-10-01T10:26:16+08:00",
                "cartoonName": "",
                "createBy": 1,
                "updateBy": 0,
                "myContentUrl": "",
                "syncState": 1
            },
            {
                "id": 11,
                "cartoonId": 2001,
                "pictures": "2/2001/cpt/11/zk1nfo.webp|2/2001/cpt/11/k8eohg.webp|2/2001/cpt/11/tn94yy.webp|2/2001/cpt/11/dfoeoc.webp|2/2001/cpt/11/ivulfb.webp|2/2001/cpt/11/nns55w.webp|2/2001/cpt/11/ifecmn.webp|2/2001/cpt/11/078i3s.webp|2/2001/cpt/11/stvdzb.webp|2/2001/cpt/11/rjph7c.webp|2/2001/cpt/11/86zrq4.webp|2/2001/cpt/11/j4yozv.webp|2/2001/cpt/11/58k2ue.webp|2/2001/cpt/11/0o205b.webp|2/2001/cpt/11/14syoo.webp|2/2001/cpt/11/bt8tri.webp|2/2001/cpt/11/85pqf1.webp|2/2001/cpt/11/qwvqbt.webp|2/2001/cpt/11/k4zpnd.webp|2/2001/cpt/11/vy9i6z.webp|2/2001/cpt/11/t0o21p.webp",
                "picsizes": "540,887|32,808|808,1208|540,808|540,808|540,808|540,808|540,807|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,808|540,888",
                "pictureNum": 21,
                "ruleId": 6,
                "sourceChapterId": "61",
                "sourceCartoonId": "manga-yt69577",
                "name": "第1话 突入 ",
                "coverPicture": "2/2001/cpt/11/zk1nfo.webp",
                "status": 1,
                "uploadStatus": 0,
                "sort": 61,
                "chapterSort": 0,
                "isFree": 1,
                "createdAt": "2024-10-01T10:25:26+08:00",
                "updatedAt": "2024-10-01T10:26:17+08:00",
                "cartoonName": "",
                "createBy": 1,
                "updateBy": 0,
                "myContentUrl": "",
                "syncState": 1
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