# 首页模块 API 文档

## 1. 检查漫画更新信息

### 接口说明
检查漫画更新信息。

### 请求信息
- 请求路径：`/api/v1/cartoon/checkupdate`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（表单数据）：
  - cartoonIds: 漫画id（一组id使用`,`隔开）
    - 测试数据: 1139

### 响应信息
```json
{
    "requestId": "5d82cd5d-f5ee-4714-83c5-397ec5a66ec7",
    "code": 200,
    "msg": "获取成功",
    "data": [
        {
            "cartoonId": 1139,
            "name": "师姐，我不做门派第一了",
            "aliasName": "师姐，我不做门派第一了",
            "protagonist": "",
            "categoryId": 4,
            "categoryName": "玄幻",
            "author": "小铜钱",
            "aliasAuthor": "小铜钱",
            "isEnd": 2,
            "chapterNum": 111,
            "intro": "雁山派掌门从山下捡来根骨绝佳的孩子，取名雁心，把她托给大师姐柳云，让她传授雁山派基础武功于她，这也太耽误练功了，柳云一边揣测是因为自己天资笨拙被师父放弃，一边却坚守大师姐的职责，用心带练雁心，使其成为了门派第一。师妹的反超似乎打破了二人原有的关系，此时门派也开始内外受难……",
            "picture": "/1/1139/cover/1a85bf.webp",
            "status": 1,
            "score": 9.1,
            "chapterName": "贺图 祝贺《虎x鹤 妖师录》动画开播！ ",
            "chapterUpdateTime": "2024-11-22T10:02:58+08:00"
        }
    ]
}
```

## 2. 首页猜你喜欢

### 接口说明
获取首页猜你喜欢信息。

### 请求信息
- 请求路径：`/api/v1/cartoon/guesslike`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - device: 设备号
    - 测试数据: 1234567890
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（表单数据）：
  - gender: 性别（0：男，1：女，2：未知）
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2
  - pageIndex: 页码
    - 测试数据: 1


### 响应信息
```json
{
    "requestId": "4ec2ae3a-2682-4d0e-afad-7ed34c6a344d",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 2,
        "pageIndex": 1,
        "pageSize": 2,
        "list": [
            {
                "id": 10583,
                "name": "无敌神拳",
                "picture": "/6/10583/cover/azpo7q.webp",
                "posterPic": "",
                "score": 9,
                "introduce": "赤手空拳入武林，只用两拳就能平定武林的拳王！真正的男人就连谈恋爱也很豪爽！说话慢，出拳快，世间没有人能挡下他九拳，从此武林的一代拳王开始了他的传奇人生…",
                "isEnd": 2,
                "author": "SMC",
                "aliasAuthor": "SMC",
                "protagonist": "",
                "categoryId": 30,
                "chapterName": "82.遇到猛骨军",
                "chapterNum": 83,
                "categoryName": "武侠",
                "zipurl": "",
                "createdAt": "2024-10-16 00:09:56"
            },
            {
                "id": 10717,
                "name": "末世歼灭者",
                "picture": "/6/10717/cover/4t0alo.webp",
                "posterPic": "",
                "score": 9.4,
                "introduce": "末日降临丧尸袭城！ 唯有杀戮方能存活！ 这是一个很常见的设定，丧尸危机爆发了。人们在某地区建立了安全地带，但有限的空间和过剩的人口导致房价暴涨。在这个时代，拥有一套属于自己的房子可以说（仍然）是天方夜谭。这个故事的主角也没有房子，和看这段文字的你一样。他为了购置一套属于自己的房子，决定冲到最前线，成为一名丧尸歼灭者，靠剿灭丧尸赚取金钱。",
                "isEnd": 2,
                "author": "奈落",
                "aliasAuthor": "奈落",
                "protagonist": "",
                "categoryId": 7,
                "chapterName": "第92话 最终话",
                "chapterNum": 92,
                "categoryName": "动作",
                "zipurl": "",
                "createdAt": "2024-10-16 02:07:55"
            }
        ]
    }
}
```

## 3. 搜索漫画信息

### 接口说明
搜索漫画信息。

### 请求信息
- 请求路径：`/api/v1/cartoon/search`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
- 请求参数（表单数据）：
  - type: 搜索类型（1.模糊搜索去重,2.搜索列表）
    - 测试数据: 1
  - content: 搜索内容
    - 测试数据: 师姐
  - page: 页码
    - 测试数据: 1
  - pageSize: 每页数量
    - 测试数据: 2

### 响应信息
```json
{
    "requestId": "0bd388c7-7997-4491-a71c-d0d898b089bc",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "list": [
            {
                "id": 6302,
                "name": "我的师姐稳得一批",
                "aliasName": "我的师姐稳得一批",
                "protagonist": "",
                "categoryId": 2,
                "categoryName": "热血",
                "author": "比格熊",
                "aliasAuthor": "比格熊",
                "isEnd": 2,
                "chapterNum": 244,
                "intro": "为了能在残酷的洪荒安身立命，必须不沾因果，杀人扬灰，谋而后动，深藏底牌，决不能越级挑战，建立后宫团，呈口舌之快。 师姐！对方不过是个筑基修士，你有必要用禁咒轰他三次吗！ 师姐！我就擦破点皮，别喂我吃九转金丹来回血啊！ 师姐，请不要装萌新，恶意卖萌。",
                "picture": "/4/6302/cover/bq3bh1.webp",
                "status": 1,
                "score": 9,
                "chapterName": "242热爱工作水",
                "chapterUpdateTime": "2024-11-08T09:04:40+08:00"
            },
            {
                "id": 1139,
                "name": "师姐，我不做门派第一了",
                "aliasName": "师姐，我不做门派第一了",
                "protagonist": "",
                "categoryId": 4,
                "categoryName": "玄幻",
                "author": "小铜钱",
                "aliasAuthor": "小铜钱",
                "isEnd": 2,
                "chapterNum": 111,
                "intro": "雁山派掌门从山下捡来根骨绝佳的孩子，取名雁心，把她托给大师姐柳云，让她传授雁山派基础武功于她，这也太耽误练功了，柳云一边揣测是因为自己天资笨拙被师父放弃，一边却坚守大师姐的职责，用心带练雁心，使其成为了门派第一。师妹的反超似乎打破了二人原有的关系，此时门派也开始内外受难……",
                "picture": "/1/1139/cover/1a85bf.webp",
                "status": 1,
                "score": 9.1,
                "chapterName": "贺图 祝贺《虎x鹤 妖师录》动画开播！ ",
                "chapterUpdateTime": "2024-11-22T10:02:58+08:00"
            }
        ],
        "extra": {
            "weeknew": 0
        },
        "count": 2,
        "pageIndex": 1,
        "pageSize": 2
    }
}
```

## 4. 增加浏览量

### 接口说明
增加浏览量。

### 请求信息
- 请求路径：`/api/v1/view`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json
  - device: 设备号
    - 测试数据: 1234567890
  - channelId: 渠道ID
    - 测试数据: 1
- 请求参数（json）：
```json
{
    "cartoonId": 1139
}
```
### 响应信息
```json
{
    "requestId": "cbfc900f-391f-40d4-ac74-1b39ebd8990e",
    "code": 200,
    "msg": "添加成功",
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

1. 首页公告信息会根据设备首次使用时间进行过滤
2. 公告已读状态会记录在数据库中