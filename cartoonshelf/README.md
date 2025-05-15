# 书架模块 API 文档
1. [加入书架](#1-加入书架)
2. [修改用户书架](#2-修改用户书架)
3. [删除书架](#3-删除书架)
4. [获取用户书架](#4-获取用户书架)
5. [用户漫画状态](#5-用户漫画状态)
6. [书架推荐](#6-书架推荐)

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
    - 测试数据: 107
  - channelId: 渠道ID
    - 测试数据: 1
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
        6533122  // 书架id
    ]
}
```

## 2. 修改用户书架

### 接口说明
修改用户书架，与加入书架的请求头和请求体结构完全相同，其作用也完全相同。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/update`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json
  - appId: 应用ID
    - 测试数据: 107
  - channelId: 渠道ID
    - 测试数据: 1
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
    "requestId": "51a06ae2-e777-4c23-ac6d-229040dbd052",
    "code": 200,
    "msg": "同步成功",
    "data": [
        6533122  // 书架id
    ]
}
```

## 3. 删除书架

### 接口说明
根据书架 ID 删除书架中的漫画，多个id通过`,`隔开。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/del/:ids`
- 请求方法：DELETE
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json

### 响应信息
```json
{
    "requestId": "62842eff-3275-4317-a4dc-aaa2f6aa0008",
    "code": 200,
    "msg": "删除成功",
    "data": null
}
```

## 4. 获取用户书架

### 接口说明
通过token获取用户书架。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/index`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json

### 响应信息
```json
{
    "requestId": "73e4c62d-7781-4666-a2ba-e5d55cacf35e",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 1,
        "pageIndex": 1,
        "pageSize": 1,
        "list": [
            {
                "id": 6533122,
                "chapter": 81980,
                "cartoonId": 1139,
                "lastReadtime": "2025-05-12T11:22:13+08:00",
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
}
```

## 5. 用户漫画状态

### 接口说明
该接口用于增加漫画的访问量和热度，用户每次通过书架观看漫画时，调用一次该接口。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/status`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json
- 请求体（json）：
```json
{
  "cartoonId": 1139,
  "from": "cartoonshelf"
}
```

### 响应信息
```json
{
    "requestId": "96698e61-84b5-4102-a03a-3da2812d92e6",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "cartoonshelfId": 6533123  // 书架id，漫画存在书架中时返回书架ID，不存在时返回0
    }
}
```

## 6. 书架推荐

### 接口说明
获取用户书架中的推荐漫画。

### 请求信息
- 请求路径：`/api/v1/cartoonshelf/recommend`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json
  - appId: 应用ID
    - 测试数据: 107
- 请求参数（表单数据）：
  - gender: 性别，1为男，2为女
  - 示例：
    - gender: 1

### 响应信息
```json
{
    "requestId": "0b753ec9-16d9-464e-b472-02e753a0e413",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "count": 4,
        "pageIndex": 1,
        "pageSize": 4,
        "list": [
            {
                "id": 0,
                "chapter": 0,
                "cartoonId": 4657,
                "lastReadtime": null,
                "name": "斗破苍穹",
                "aliasName": "斗破苍穹",
                "protagonist": "",
                "categoryId": 2,
                "categoryName": "热血",
                "author": "知音漫客",
                "aliasAuthor": "知音漫客",
                "isEnd": 2,
                "chapterNum": 624,
                "intro": "正所谓三十年河东三十年河西，天才少年因忽然失去了天生的灵力，被所有人嘲笑排挤，为了一雪前耻他亲手毁掉婚约，一心进修、打怪、升级！重登人生巅峰的他让人们知道莫欺少年穷真的很重要！",
                "picture": "/3/4657/cover/dshkkw.webp",
                "status": 1,
                "score": 9.8,
                "chapterName": "第613话 468 异震 ",
                "chapterUpdateTime": "2025-03-09T02:08:23+08:00"
            },
            {
                "id": 0,
                "chapter": 0,
                "cartoonId": 1382,
                "lastReadtime": null,
                "name": "从大树开始的进化",
                "aliasName": "从大树开始的进化",
                "protagonist": "",
                "categoryId": 8,
                "categoryName": "科幻",
                "author": "黑鸟社",
                "aliasAuthor": "黑鸟社",
                "isEnd": 2,
                "chapterNum": 347,
                "intro": "黑鸟社新作，重生成为一株柳树！？灵气复苏，万物崛起。重生的柳树也走上了进化之路。能够无限进化的它，是“神力”还是“诅咒”？",
                "picture": "/1/1382/cover/aacebt.webp",
                "status": 1,
                "score": 9.9,
                "chapterName": "第346话 生者与死者 ",
                "chapterUpdateTime": "2025-03-16T03:22:09+08:00"
            },
            {
                "id": 0,
                "chapter": 0,
                "cartoonId": 10110,
                "lastReadtime": null,
                "name": "魔皇大管家",
                "aliasName": "魔皇大管家",
                "protagonist": "吾皇魔都",
                "categoryId": 26,
                "categoryName": "冒险",
                "author": "夜枭（原著）",
                "aliasAuthor": "夜枭（原著）",
                "isEnd": 2,
                "chapterNum": 680,
                "intro": "魔皇卓一凡因得到上古魔帝传承，遭亲信背叛并引来杀身之祸。重生后修为归零的他又被心魔所困，不得不成为一个落寞家族大小姐的专属管家。从魔皇到小小管家，他究竟要怎样和自己的“心魔大小姐”相处，又如何才能带领这个没落家族和自己一起重回这片大陆的巅峰呢！",
                "picture": "/6/10110/cover/2zk0c8.webp",
                "status": 1,
                "score": 9.9,
                "chapterName": "第675话 倾城胜出 ",
                "chapterUpdateTime": "2025-03-15T23:43:48+08:00"
            },
            {
                "id": 0,
                "chapter": 0,
                "cartoonId": 3487,
                "lastReadtime": null,
                "name": "我！天命大反派",
                "aliasName": "我！天命大反派",
                "protagonist": "又名:天选之王 主角：顾长歌 叶尘  又名:修仙之我是大反派 ",
                "categoryId": 4,
                "categoryName": "玄幻",
                "author": "天命反派（原著）+绘术动漫",
                "aliasAuthor": "天命反派（原著）+绘术动漫",
                "isEnd": 2,
                "chapterNum": 236,
                "intro": "顾长歌穿越到玄幻世界，开局就拉满了模范主角、气运之子的仇恨值。不仅女主投怀送抱，还有令人眼红的贵客待遇。好在自己身份实力高人一筹，踩死一个小小的气运之子，还不简单？等等，这里还有个专门收割各路主角的系统？顾长歌微微一笑，看来这是要自己在天命大反派的路上越走越远啊！ ",
                "picture": "/2/3487/cover/3s27y2.webp",
                "status": 1,
                "score": 9.9,
                "chapterName": "第234话 柏拉图式恋爱 ",
                "chapterUpdateTime": "2025-03-17T03:33:44+08:00"
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
