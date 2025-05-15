# 静态资源模块 API 文档
- [基础资源](#基础资源)
  1. [拉取域名配置](#1-拉取域名配置)

- [标签资源](#标签资源)
  1. [拉取标签配置](#1-拉取标签配置)
  2. [拉取标签](#2-拉取标签)

- [栏目资源](#栏目资源)
  1. [拉取栏目列表](#1-拉取栏目列表)
  2. [拉取首页栏目静态资源](#2-拉取首页栏目静态资源)
  3. [拉取栏目详情](#3-拉取栏目详情)

- [分类资源](#分类资源)
  1. [拉取分类列表](#1-拉取分类列表)
  2. [拉取分类详情](#2-拉取分类详情)

- [地区资源](#地区资源)
  1. [拉取地区列表](#1-拉取地区列表)
  2. [拉取地区详情](#2-拉取地区详情)

- [漫画资源](#漫画资源)
  1. [拉取漫画包](#1-拉取漫画包)
  2. [拉取漫画封面](#2-拉取漫画封面)
  3. [拉取漫画图片](#3-拉取漫画图片)

- [其他资源](#其他资源)
  1. [拉取今日热点](#1-拉取今日热点)
  2. [拉取轮播图](#2-拉取轮播图)
  3. [拉取大家都在看](#3-拉取大家都在看)
  4. [拉取新书推荐](#4-拉取新书推荐)
  5. [拉取排行榜](#5-拉取排行榜)
  6. [拉取作者还画过](#6-拉取作者还画过)
  7. [拉取热门发现](#7-拉取热门发现)
  8. [拉取更新数据](#8-拉取更新数据)


## 基础资源

## 1. 拉取域名配置

### 接口说明
从固定的域名拉取用于应用内部资源获取相关的配置。若配置拉取失败，可以通过[`/api/v1/config`](../config/README.md#1-获取系统配置)接口获取配置。

### 请求信息
- 请求主机：`http://sta.bitcycle.space`
- 请求路径：`/static/config/108.json`
- 请求方法：GET

### 响应信息
```json
{
  "apiDomain": "",  // API域名（用于访问其他模块的接口）
  "staticDomain": "",  // 静态资源域名（用于拉取配置信息等资源）
  "imageDomain": "",  // 图片域名（用于拉取漫画图片等资源）
  "coverDomain": "",  // 封面域名
  "cacheDomain": "",  // 缓存域名（一般与api域名相同）
  "shareDownUrl": ""  // 分享下载地址
}
```

## 标签资源

## 1. 拉取标签配置

### 接口说明
使用staticDomain加appId和男生/女生的标签ID，拉取对应的标签配置信息。若配置拉取失败，可以通过[`/api/v1/sync/tag`](../sync/README.md#1-同步标签数据)接口获取配置。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/tag/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：标签ID，用于区分不同的性别标签（1.男, 2.女）
  - 示例（应用号：107，性别：男）：
    - 请求路径：`/static/tag/107/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": [
    {
      "id": 42,  // 标签ID
      "name": "玄幻",  // 标签名称
      "titlePicture": "",  // 标题图片
      "coverPicture": ""  // 封面图片
    },
    {
      "id": 100,
      "name": "修真",
      "titlePicture": "",
      "coverPicture": ""
    },
    // ... 其他标签信息
  ],
  "msg": "返回成功",
  "time": 1744559472
}
```

## 2. 拉取标签

### 接口说明
使用staticDomain加appId和标签Id和性别Id，拉取标签配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/tag/%d/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：标签Id，用于区分不同的标签
    - `%d`：性别Id，用于区分不同的性别（1.男, 2.女）
  - 示例（应用号：107，标签Id：100，性别：男）：
    - 请求路径：`/static/tag/107/100/1.json`
- 请求方法：GET

### 响应信息
```json
```

## 栏目资源

## 1. 拉取栏目列表

### 接口说明
使用staticDomain加appId，拉取栏目列表配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/column_index/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
  - 示例（应用号：107）：
    - 请求路径：`/static/column_index/107.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": {
    "female": [
      {
        "id": 1,  // 栏目ID
        "types": 2,  // 类型（为id+1）
        "name": "高分推荐",  // 栏目名称
        "staticPath": "/static/cartoon/index/13/2/1.json",  // 首页静态资源路径
        "listStaticPath": "/static/cartoon/index/13/2/page/1/{page}.json",  // 列表静态资源路径（带分页，从1开始计数）
        "newStaticPath": "/cartoon/index/13/2/1.json",  // 新的静态资源路径（如果老的无法使用就使用新的）
        "newListStaticPath": "/cartoon/index/13/2/page/1/{page}.json"  // 新的列表静态资源路径（如果老的无法使用就使用新的）
      },
      {
        "id": 2,
        "types": 3,
        "name": "热门推荐",
        "staticPath": "/static/cartoon/index/13/2/2.json",
        "listStaticPath": "/static/cartoon/index/13/2/page/2/{page}.json",
        "newStaticPath": "/cartoon/index/13/2/2.json",
        "newListStaticPath": "/cartoon/index/13/2/page/2/{page}.json"
      },
      // ... 其他栏目信息
    ],
    "male": [
      {
        "id": 1,
        "types": 2,
        "name": "高分推荐",
         "staticPath": "/static/cartoon/index/13/1/1.json",
        "listStaticPath": "/static/cartoon/index/13/1/page/1/{page}.json",
        "newStaticPath": "/cartoon/index/13/1/1.json",
        "newListStaticPath": "/cartoon/index/13/1/page/1/{page}.json"
      },
      {
        "id": 2,
        "types": 3,
        "name": "热门推荐",
        "staticPath": "/static/cartoon/index/13/1/2.json",
        "listStaticPath": "/static/cartoon/index/13/1/page/2/{page}.json",
        "newStaticPath": "/cartoon/index/13/1/2.json",
        "newListStaticPath": "/cartoon/index/13/1/page/2/{page}.json"
      },
      // ... 其他栏目信息
    ]
  },
  "msg": "返回成功",
  "time": 1744559475
}
```

## 2. 拉取首页栏目静态资源

### 接口说明
使用staticDomain加appId和性别Id和栏目Id，拉取首页栏目静态资源信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：
  - 旧（优先）：`/static/cartoon/index/%d/%d/%d.json`
  - 新：`/cartoon/index/%d/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别Id，用于区分不同的性别（1.男, 2.女）
    - `%d`：栏目Id，用于区分不同的栏目
  - 示例（应用号：107，性别：男，栏目：1）：
    - 旧路径：`/static/cartoon/index/107/1/1.json`
    - 新路径：`/cartoon/index/107/1/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": [
    {
      "id": 14533,  // 漫画ID
      "name": "我独自升级 : 诸神黄昏",  // 漫画名称
      "picture": "/8/14533/cover/wguw9i.webp",  // 封面图片
      "posterPic": "",  // 海报图片
      "score": 9.3,  // 评分
      "introduce": "一直默默无闻的平凡大学生程修豪， 在面临生死存亡之际， 体内沉睡的特殊血统得到觉醒！ “站起来。” 凌驾于死亡之上，支配亡灵的猎人， 敬请关注程修豪的打怪升级之路！ \n* 本作品沿用了《我独自升级》的世界观。",  // 简介
      "isEnd": 2,  // 是否完结（1.完结, 2.连载）
      "author": "JIN（主笔）",  // 作者
      "aliasAuthor": "JIN（主笔）",  // 作者别名
      "protagonist": "",  // 主角
      "categoryId": 2,  // 分类ID
      "chapterName": "第36话",  // 最新章节名称
      "chapterNum": 37,  // 章节总数
      "categoryName": "热血",  // 分类名称
      "zipurl": ""  // 压缩包URL
    },
    {
      "id": 12684,
      "name": "吕布的人生模拟器",
      "picture": "/7/12684/cover/s1cxva.webp",
      "posterPic": "",
      "score": 9.9,
      "introduce": "\"抢最美的女人，骑最快的战马，舞最强的兵器，一骑独挡关东诸侯十八路。\n一夫当关万夫莫开，乱世豪杰齐俯首。\n世人称我吕布不死，天下无可定乱之机，我笑天下皆虚伪之辈，奉先之外再无英雄。\n一朝入人生模拟，瞬息千百世轮回，\n历尽沧桑，百炼成钢。\n试问现在的吕布奉先，能否抵得住‘白门楼’的宿命之劫？\"",
      "isEnd": 2,
      "author": "有马文化传播",
      "aliasAuthor": "有马文化传播",
      "protagonist": "",
      "categoryId": 2,
      "chapterName": "117 内讧",
      "chapterNum": 123,
      "categoryName": "热血",
      "zipurl": ""
    },
    //... 其他漫画信息
  ],
  "msg": "返回成功",
  "time": 1740811054
}
```

## 3. 拉取栏目详情

### 接口说明
使用staticDomain加appId和性别Id和栏目Id和分页号，拉取栏目详情信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：
  - 旧（优先）：`/static/cartoon/index/%d/%d/page/%d/%d.json`
  - 新：`/cartoon/index/%d/%d/page/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别Id，用于区分不同的性别（1.男, 2.女）
    - `%d`：栏目Id，用于区分不同的栏目
    - `%d`：分页号，用于分页
  - 示例（应用号：107，性别：男，栏目：1，分页：1）：
    - 旧路径：`/static/cartoon/index/107/1/page/1/1.json`
    - 新路径：`/cartoon/index/107/1/page/1/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":{
    "list":[
      {
        "id":10110,  // 漫画ID
        "name":"魔皇大管家",  // 漫画名称
        "picture":"/6/10110/cover/2zk0c8.webp",  // 封面图片
        "posterPic":"",  // 海报图片
        "score":9.9,  // 评分
        "introduce":"魔皇卓一凡因得到上古魔帝传承，遭亲信背叛并引来杀身之祸。重生后修为归零的他又被心魔所困，不得不成为一个落寞家族大小姐的专属管家。从魔皇到小小管家，他究竟要怎样和自己的“心魔大小姐”相处，又如何才能带领这个没落家族和自己一起重回这片大陆的巅峰呢！",  // 简介
        "isEnd":2,  // 是否完结（1.完结, 2.连载）
        "author":"夜枭（原著）",  // 作者
        "aliasAuthor":"夜枭（原著）",  // 作者别名
        "protagonist":"吾皇魔都",  // 主角
        "categoryId":26,  // 分类ID
        "chapterName":"第675话 倾城胜出 ",  // 最新章节名称
        "chapterNum":680,  // 章节总数
        "categoryName":"冒险",  // 分类名称
        "zipurl":""  // 压缩包URL
      },
      // ... 其他漫画信息
    ],
    "total_page":1
  },
  "msg":"返回成功",
  "time":1747191958
}
```

## 分类资源

## 1. 拉取分类列表

### 接口说明
使用staticDomain加appId和性别Id，拉取分类列表配置信息。若拉取失败，可以通过[`/api/v1/sync/category`](../sync/README.md#2-同步分类数据)接口获取配置。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/category/%d/%d/all.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别Id，用于区分不同的性别（1.男, 2.女）
  - 示例（应用号：107，性别：男）：
    - 请求路径：`/static/category/107/1/all.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {
      "id":36,  // 分类ID
      "name":"权谋",  // 分类名称
      "picture":"/static/cate/a9fbcb.jpg"  // 分类图片
    },
    {
      "id":35,
      "name":"奇幻",
      "picture":"/static/cate/65fd84.jpg"
    },
    // ... 其他分类信息
  ],
  "msg":"返回成功",
  "time":1747205466
}
```

## 2. 拉取分类详情

### 接口说明
使用staticDomain加appId和分类Id和书籍状态和分页号，拉取分类详情信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/category/%d/%d/%s/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：分类Id，用于区分不同的分类
    - `%s`：书籍状态，用于区分不同的数据状态
      - `finish`：完结书籍
      - `hot`：热门书籍
      - `new`：最新书籍
      - `praise`：好评书籍
    - `%d`：分页号，用于分页
  - 示例（应用号：107，分类：36，书籍状态：new，分页：1）：
    - 请求路径：`/static/cartoon/category/107/36/new/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":{
    "list":[
      {
        "id":1553,
        "name":"殿下倾城",
        "picture":"/1/1553/cover/d1vlv4.webp",
        "posterPic":"",
        "score":9.7,
        "introduce":"【天真赤忱小皇子x疯批报社黑丞相】九皇子祁长忆继承了母妃的美貌，却是个有些痴傻的人儿。裴争是当朝丞相，一人之下万人之上的他手段凌厉，心狠手辣人尽皆知，而那颗冰冷的心却渐渐被长忆温暖。他以为那个小傻子永远都会被自己捏在掌心中，却没想过有一天小傻子也会伤心欲绝离开了他。他猩红着双眸疯魔一般四处搜寻，却始终一无所获，“没有了你，我这辈子都不会开心了，殿下，我到底要去何处寻你？” ",
        "isEnd":2,
        "author":"风荷举哦",
        "aliasAuthor":"风荷举哦",
        "protagonist":"",
        "categoryId":36,
        "chapterName":"通知07 请假条 ",
        "chapterNum":131,
        "categoryName":"",
        "zipurl":""
      },
      {
        "id":1301,
        "name":"史上最强赘婿",
        "picture":"/1/1301/cover/c9stsr.webp",
        "posterPic":"",
        "score":9.6,
        "introduce":"沈浪穿越异世成为财主家的小白脸赘婿，因太废物被赶出家门。于是他发奋图强，要找一个更有权有势绝美高贵的豪门千金做上门女婿。\r练武是不可能练武的，这辈子都不可能练武！\r我要把老婆培养成天下第一高手，谁敢惹我就让我娘子打死你！",
        "isEnd":2,
        "author":"阅文漫画",
        "aliasAuthor":"阅文漫画",
        "protagonist":"又名：浪子的奇遇",
        "categoryId":36,
        "chapterName":"277 大雪崩！ ",
        "chapterNum":279,
        "categoryName":"",
        "zipurl":""
      }
    ],
    "total_page":1
  },
  "msg":"返回成功",
  "time":1747205478
}
```

## 地区资源

## 1. 拉取地区列表

### 接口说明
使用staticDomain加appId，拉取地区列表配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/area/%d/area.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
  - 示例（应用号：107）：
    - 请求路径：`/static/area/107/area.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {"id":1,"name":"大陆"},
    {"id":2,"name":"欧漫"},
    {"id":3,"name":"韩漫"},
    {"id":4,"name":"日漫"}
  ],
  "msg":"返回成功",
  "time":1747208815
}
```

## 2. 拉取地区详情

### 接口说明
使用staticDomain加appId和地区Id和分页号，拉取地区详情信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/area/%d/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：地区Id，用于区分不同的地区
    - `%d`：分页号，用于分页
  - 示例（应用号：107，地区：2，分页：1）：
    - 请求路径：`/static/cartoon/area/107/2/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":{
    "list":[
      {
        "id":3687,  // 漫画ID
        "name":"风起苍岚",  // 漫画名称
        "picture":"/2/3687/cover/qpa5n2.webp",  // 封面图片
        "posterPic":"",  // 海报图片
        "score":9.3,  // 评分
        "introduce":" 一个是叱咤仙路的风云上神，一个是废材资质修真菜鸟，当网游遭遇修真，还有什么是不可能的呢？昔日等级榜第一大神跌落云端，废柴医师掉进修真世界。小小菜鸟又该如何一步一个脚印，攀上这云海尽头，苍岚之巅？萌兽or美男？仙术or神通？丹药or法宝？修真菜鸟的逆袭日记从现在开始书写！即使大道无情，艰险丛生，萌妹子也要闯出一片天！! ",  // 简介
        "isEnd":2,  // 是否完结（1.完结, 2.连载）
        "author":"飒飒动漫",  // 作者
        "aliasAuthor":"飒飒动漫",  // 作者别名
        "protagonist":"",  // 主角
        "categoryId":35,  // 分类ID
        "chapterName":"第2季278话 主动上门3 ",  // 最新章节名称
        "chapterNum":714,  // 章节总数
        "categoryName":"",  // 分类名称
        "zipurl":""  // 压缩包URL
      },
      // ... 其他漫画信息
    ],
    "total_page":1  // 总页数
  },
  "msg":"返回成功",
  "time":1747208816
}
```

## 漫画资源

## 1. 拉取漫画包

### 接口说明
使用staticDomain加漫画ID除2000的值（向上取整）和漫画ID，拉取漫画包。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/%d/%d.zip`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：漫画ID除2000的值（向上取整）
    - `%d`：漫画ID
  - 示例（漫画ID：1139）：
    - 请求路径：`/static/cartoon/1/1139.zip`
- 请求方法：GET

### 响应信息
获取一个zip文件，文件包含chapter.json和detail.json文件。
chapter.json文件中pictures字段解密算法（flutter版）：
```dart
import 'dart:convert';
import 'package:pointycastle/api.dart';
import 'package:pointycastle/asymmetric/api.dart';
import 'package:pointycastle/asymmetric/rsa.dart';
import 'package:pointycastle/key_generators/rsa_key_generator.dart';
import 'package:pointycastle/paddings/pkcs7.dart';
import 'package:pointycastle/paddings/pss.dart';
import 'package:pointycastle/random/fortuna_random.dart';
import 'package:pointycastle/signers/rsa_signer.dart';
import 'package:pointycastle/export.dart';

class RSADecryptor {
  static String publicDecrypt(String input, String publicKeyPem) {
    try {
      // 解析 PEM 格式的公钥
      final publicKeyBytes = parsePublicKeyFromPem(publicKeyPem);
      final publicKey = RSAPublicKey(
        BigInt.parse(publicKeyBytes['modulus'], radix: 16),
        BigInt.parse(publicKeyBytes['exponent'], radix: 16),
      );

      // 解码 Base64 输入
      final inputBytes = base64.decode(input);

      // 创建 RSA 解密器
      final decryptor = RSABlockCipher()
        ..init(false, PublicKeyParameter<RSAPublicKey>(publicKey));

      // 解密数据
      final decryptedBytes = decryptor.process(inputBytes);

      // 返回解密后的字符串
      return utf8.decode(decryptedBytes);
    } catch (e) {
      print('解密出错: $e');
      return '';
    }
  }

  static Map<String, String> parsePublicKeyFromPem(String pem) {
    final startIndex = pem.indexOf('-----BEGIN PUBLIC KEY-----');
    final endIndex = pem.indexOf('-----END PUBLIC KEY-----');
    if (startIndex == -1 || endIndex == -1) {
      throw ArgumentError('无效的 PEM 格式公钥');
    }

    final pemContent = pem.substring(
      startIndex + '-----BEGIN PUBLIC KEY-----'.length,
      endIndex,
    ).trim();

    final decodedBytes = base64.decode(pemContent);
    final sequence = ASN1Parser(decodedBytes).nextObject() as ASN1Sequence;
    final bitString = sequence.elements[1] as ASN1BitString;
    final publicKeySequence = ASN1Parser(bitString.stringValueBytes).nextObject() as ASN1Sequence;

    final modulus = (publicKeySequence.elements[0] as ASN1Integer).value.toString(16);
    final exponent = (publicKeySequence.elements[1] as ASN1Integer).value.toString(16);

    return {
      'modulus': modulus,
      'exponent': exponent,
    };
  }
}
```

## 2. 拉取漫画封面

### 接口说明
使用imageDomain加漫画ID除2000的值（向上取整）和漫画ID和图片名，拉取漫画封面。

### 请求信息
- 请求主机：`imageDomain`
- 请求路径（预组串）：`/cartoon/%d/%d/cover/%s`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：漫画ID除2000的值（向上取整）
    - `%d`：漫画ID
    - `%s`：图片名

### 响应信息
获取一个webp图片文件，文件为漫画封面。

## 3. 拉取漫画图片

### 接口说明
使用imageDomain加漫画ID除2000的值（向上取整）和漫画ID和章节ID和图片名，拉取漫画图片。

### 请求信息
- 请求主机：`imageDomain`
- 请求路径（预组串）：`/cartoon/%d/%d/cpt/%d/%s`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：漫画ID除2000的值（向上取整）
    - `%d`：漫画ID
    - `%d`：章节ID
    - `%s`：图片名

### 响应信息
获取一个webp图片文件，文件为漫画图片。

## 其他资源

## 1. 拉取今日热点

### 接口说明
使用staticDomain加性别ID，拉取今日热点配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/todayhot/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：性别ID，用于区分不同的性别（1.男, 2.女）
  - 示例（性别：男）：
    - 请求路径：`/static/cartoon/todayhot/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": [
    {
      "id": 10614,  // 漫画ID
      "name": "我！天命大反派",  // 漫画名称
      "picture": "/6/10614/cover/g7mnu6.jpg",  // 封面图片
      "posterPic": "6/10614/cover/b96642.jpg",  // 海报图片
      "score": 9.9,  // 评分
      "introduce": "顾长歌穿越到玄幻世界，开局就拉满了模范主角、气运之子的仇恨值。\r\n　　不仅女主投怀送抱，还有令人眼红的贵客待遇。\r\n　　好在自己身份实力高人一筹，踩死一个小小的气运之子，还不简单？\r\n　　等等，这里还有个专门收割各路主角的系统？\r\n　　顾长歌微微一笑，看来这是要自己在天命大反派的路上越走越远啊！\r\n　　【独家/责编：花青】",  // 简介
      "isEnd": 2,  // 是否完结（1.完结, 2.连载）
      "author": "天命反派",  // 作者
      "aliasAuthor": "天命反派（原著）+绘术动漫",  // 作者别名
      "protagonist": "又名:天选之王 主角：顾长歌 叶尘  又名:修仙之我是大反派 ",  // 主角
      "categoryId": 4,  // 分类ID
      "chapterName": "第231话 你不是他！？",  // 最新章节名称
      "chapterNum": 247,  // 章节总数
      "categoryName": "",  // 分类名称
      "zipurl": ""  // 压缩包URL
    },
    {
      "id": 11022,
      "name": "星甲魂将传",
      "picture": "/6/11022/cover/6yssi4.jpg",
      "posterPic": "",
      "score": 9.9,
      "introduce": "人族最后一位星魂师宋云祥，带着系统重生回校园时代。少年时曾因为魂脉残缺遭人白眼，因为弱小只能眼睁睁看着亲友战死在自己身前。这一世，带着系统重生归来，拥有六十年的战斗经验和知识技术，重返校园，从此一路开挂造机甲打怪兽…曾经后悔的事，曾经错过的人，这一次将不留遗憾。",
      "isEnd": 2,
      "author": "乐想动漫",
      "aliasAuthor": "乐想动漫",
      "protagonist": "",
      "categoryId": 2,
      "chapterName": "265 战前筹谋 ",
      "chapterNum": 288,
      "categoryName": "",
      "zipurl": ""
    },
    //... 其他漫画信息
  ],
  "msg": "返回成功",
  "time": 1741328705
}
```

## 2. 拉取轮播图

### 接口说明
使用staticDomain加appId和性别ID，拉取轮播图配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/%d/index/banner/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别ID，用于区分不同的性别（1.男, 2.女）
  - 示例（应用号：107，性别：男）：
    - 请求路径：`/static/13/index/banner/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": [
    {
      "id": 1,  // 轮播图ID
      "appId": 13,  // 应用ID
      "name": "我独自升级",  // 轮播图名称
      "pictureUrl": "/static/banner/40/40aaed.png",  // 轮播图图片URL
      "jumpUrl": "{\"type\":\"detail\",\"content\":\"5532\"}",  // 跳转URL
      "gender": 1,  // 性别（1.男, 2.女）
      "status": 1,  // 状态（1.启用, 2.禁用）
      "createdAt": "2022-02-25T11:48:21+08:00",  // 创建时间
      "updatedAt": "2025-02-04T21:11:10+08:00",  // 更新时间
      "createBy": 1,  // 创建人编号
      "updateBy": 1  // 更新人编号
    },
    {
      "id": 4,
      "appId": 13,
      "name": "全球冰封：我打造了末日安全屋",
      "pictureUrl": "/static/banner/25/259f58.png",
      "jumpUrl": "{\"type\":\"detail\",\"content\":\"13736\"}",
      "gender": 1,
      "status": 1,
      "createdAt": "2022-03-24T11:59:14+08:00",
      "updatedAt": "2025-02-04T21:11:31+08:00",
      "createBy": 1,
      "updateBy": 1
    },
    // ... 其他轮播图信息
  ],
  "msg": "返回成功",
  "time": 1742624483
}
```

## 3. 拉取大家都在看

### 接口说明
使用staticDomain加分页号，拉取大家都在看配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/relationread/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：页码，从1开始计数
  - 示例（页码：1）：
    - 请求路径：`/static/cartoon/relationread/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code": 200,
  "data": [
    {
      "id": 5343,  // 漫画ID
      "name": "笑战平沙",  // 漫画名称
      "picture": "/3/5343/cover/165fh3.jpg",  // 封面图片
      "posterPic": "",  // 海报图片
      "score": 5,  // 评分
      "introduce": "苏渊曾说过，如果当上了将军却没有经历过战争，是一件可怕的事情。我和苏宸当时都没有明白这话的意思，其实到了最后我想就算多可怕，我也宁愿他们俩能一直在我身边。当我们三人都不复年少，摆脱了昔日裹雪为衣的日子，位居人上，却似乎有什么发生了变化……【授权/完结责编：胡辣瞎】\r\n　　",  // 简介
      "isEnd": 2,  // 是否完结（1.完结, 2.连载）
      "author": "关耳山大风",  // 作者
      "aliasAuthor": "关耳山大风",  // 作者别名
      "protagonist": "",  // 主角
      "categoryId": 2,  // 分类ID
      "chapterName": "第4话 雪 夜",  // 最新章节名称
      "chapterNum": 4,  // 章节总数
      "categoryName": "热血"  // 分类名称
    },
    {
      "id": 4103,
      "name": "夜魔侠：黑与白",
      "picture": "/3/4103/cover/9lgye3.jpg",
      "posterPic": "",
      "score": 5,
      "introduce": "夜魔侠：黑与白漫画，盲人律师默多克通过手术重见光明，但在与靶眼的大战中发现自己的超级感官受到削弱，因为失误导致了一人丧命。正当他思索这份馈赠的意义何在时，金并出狱了。一直在背后密谋着什么的金并终于有所举动，他的意图究竟是什么呢？",
      "isEnd": 2,
      "author": "Marvel Comics",
      "aliasAuthor": "Marvel Comics",
      "protagonist": "",
      "categoryId": 2,
      "chapterName": "第1话 31P",
      "chapterNum": 1,
      "categoryName": "热血"
    },
    // ... 其他漫画信息
  ],
  "msg": "返回成功",
  "time": 1744559461
}
```

## 4. 拉取新书推荐

### 接口说明
使用staticDomain加appId和性别ID和分页号，拉取新书推荐配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/new/%d/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别ID，用于区分不同的性别（1.男, 2.女）
    - `%d`：分页号，从1开始计数
  - 示例（应用号：107，性别：男，分页：1）：
    - 请求路径：`/static/cartoon/new/107/1/1.json`

### 响应信息
```json
{
  "code":200,
  "data":{
    "list":[
      {
        "id":23902,  // 漫画ID
        "name":"神乐钵",  // 漫画名称
        "picture":"/12/23902/cover/9tibf4.webp",  // 封面图片
        "posterPic":"",  // 海报图片
        "score":9.1,  // 评分
        "introduce":"血沫横飞！用刀决战的动作大战！",  // 简介
        "isEnd":2,  // 是否完结（1.完结, 2.连载）
        "author":"外园健",  // 作者
        "aliasAuthor":"外园健",  // 作者别名
        "protagonist":"",  // 主角
        "categoryId":31,  // 分类ID
        "chapterName":"单行本加笔",  // 最新章节名称
        "chapterNum":57,  // 章节总数
        "categoryName":"",  // 分类名称
        "zipurl":""  // 压缩包URL
      },
      // ... 其他漫画信息
    ],
    "total_page":20
  },
  "msg":"返回成功",
  "time":1747204855
}
```

## 5. 拉取排行榜

### 接口说明
使用staticDomain加appId和性别ID和排行名，拉取排行榜配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/ranking/%d/%d/%s.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别ID，用于区分不同的性别（1.男, 2.女）
    - `%s`：排行名，用于区分不同的排行
      - `collect`：收藏排行
      - `finish`：完结排行
      - `hotsearch`：热搜排行
      - `new`：最新排行
      - `popularity`：人气排行
      - `praise`：好评排行
      - `reco`：推荐排行
  - 示例（应用号：107，性别：男，排行名：reco）：
    - 请求路径：`/static/ranking/107/1/reco.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {
      "id":3487,  // 漫画ID
      "name":"我！天命大反派",  // 漫画名称
      "picture":"/2/3487/cover/3s27y2.webp",  // 封面图片
      "posterPic":"",  // 海报图片
      "score":9.9,  // 评分
      "introduce":"顾长歌穿越到玄幻世界，开局就拉满了模范主角、气运之子的仇恨值。不仅女主投怀送抱，还有令人眼红的贵客待遇。好在自己身份实力高人一筹，踩死一个小小的气运之子，还不简单？等等，这里还有个专门收割各路主角的系统？顾长歌微微一笑，看来这是要自己在天命大反派的路上越走越远啊！ ",  // 简介
      "isEnd":2,  // 是否完结（1.完结, 2.连载）
      "author":"天命反派（原著）+绘术动漫",  // 作者
      "aliasAuthor":"天命反派（原著）+绘术动漫",  // 作者别名
      "protagonist":"又名:天选之王 主角：顾长歌 叶尘  又名:修仙之我是大反派 ",  // 主角
      "categoryId":4,  // 分类ID
      "chapterName":"第234话 柏拉图式恋爱 ",  // 最新章节名称
      "chapterNum":236,  // 章节总数
      "categoryName":"",  // 分类名称
      "zipurl":""  // 压缩包URL
    },
    // ... 其他漫画信息
  ],
  "msg":"返回成功",
  "time":1747206317
}
```

## 6. 拉取作者还画过

### 接口说明
使用staticDomain加作者名生成的MD5值，拉取作者还画过什么。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/author/%s.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%s`：作者名（author字段）生成的MD5值
  - 示例（作者名：三昧漫画）：
    - 请求路径：`/static/cartoon/author/0e0126ec77e2aa512e150bf024916039.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {
      "id":10571,  // 漫画ID
      "name":"星火·天启",  // 漫画名称
      "picture":"/6/10571/cover/ve8za1.webp",  // 封面图片
      "posterPic":"",  // 海报图片
      "score":9,  // 评分
      "introduce":"唐天宝末年，爆发安史之乱，奸相杨国忠接到前线密报，为调查密报中“鬼兵”一事，其派出两位门客萧辰，萧已前往西北。萧辰，萧已为化名，本命为唐昼，唐不孤，原本是西蜀唐门门主之子，因唐门内斗父母被杀故而出逃，路遇杨国忠，因其二人身负秘术故而被杨国忠收留，更是暗中栽培二人成为他门下杀手。",  // 简介
      "isEnd":2,  // 是否完结（1.完结, 2.连载）
      "author":"三昧漫画",  // 作者
      "aliasAuthor":"三昧漫画",  // 作者别名
      "protagonist":"",  // 主角
      "categoryId":13,  // 分类ID
      "chapterName":"第14话 庙堂风雨",  // 最新章节名称
      "chapterNum":15,  // 章节总数
      "categoryName":"历史",  // 分类名称
      "zipurl":""  // 压缩包URL
    }
  ],
  "msg":"返回成功",
  "time":1747207655
}
```

## 7. 拉取热门发现

### 接口说明
使用staticDomain加appId，拉取搜索时的热门发现配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/heat/%d/heat.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
  - 示例（应用号：107）：
    - 请求路径：`/static/cartoon/heat/107/heat.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {"id":23996,"name":"黑豹家族的雪豹宝宝"},
    {"id":23958,"name":"悠哉兽世：种种田，生生崽"},
    {"id":23949,"name":"沐妙妙的异世恋爱与冒险"},
    {"id":23931,"name":"亲爱的，不要按那个按钮"},
    {"id":23911,"name":"我复苏了华夏神明"},
    {"id":23910,"name":"重生后身边全是仇人幼崽"},
    {"id":23904,"name":"玄幻：我的女帝徒弟要黑化"},
    {"id":23902,"name":"神乐钵"}
  ],
  "msg":"返回成功",
  "time":1747208374
}
```

## 8. 拉取更新数据

### 接口说明
使用staticDomain加appId和性别ID，拉取更新数据配置信息。

### 请求信息
- 请求主机：`staticDomain`
- 请求路径（预组串）：`/static/cartoon/update/%d/%d.json`
  - 占位符细节（根据预组串从左到右依次向下列出）：
    - `%d`：appId，用于区分不同的应用
    - `%d`：性别ID，用于区分不同的性别（1.男, 2.女）
  - 示例（应用号：107，性别：男）：
    - 请求路径：`/static/cartoon/update/107/1.json`
- 请求方法：GET

### 响应信息
```json
{
  "code":200,
  "data":[
    {
      "id":23902,  // 漫画ID
      "name":"神乐钵",  // 漫画名称
      "picture":"/12/23902/cover/9tibf4.webp",  // 封面图片
      "posterPic":"",  // 海报图片
      "score":9.1,  // 评分
      "introduce":"血沫横飞！用刀决战的动作大战！",  // 简介
      "isEnd":2,  // 是否完结（1.完结, 2.连载）
      "author":"外园健",  // 作者
      "aliasAuthor":"外园健",  // 作者别名
      "protagonist":"",  // 主角
      "categoryId":31,  // 分类ID
      "chapterName":"单行本加笔",  // 最新章节名称
      "chapterNum":57,  // 章节总数
      "categoryName":"",  // 分类名称
      "zipurl":""  // 压缩包URL
    },
    // ... 其他漫画信息
  ],
  "msg":"返回成功",
  "time":1747209952
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
