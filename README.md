# API 文档

## 基本信息

- 基础URL: `http://manhua-api.nftx.pics`
- 所有请求和响应均使用JSON格式
- 字符编码：UTF-8

## 通用请求头

| 请求头 | 说明 | 示例 |
|-------|-----|------|
| Authorization | JWT认证token，格式为"Bearer {token}" | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9... |
| X-Package | 应用包名，用于日志记录 | com.meimanyuan.app |

## 通用响应格式

```json
{
    "code": 200,           // 状态码，200表示成功
    "message": "success", // 状态描述
    "data": {            
        // 响应数据，具体结构见各接口文档
    }
}
```

## 通用状态码

| 状态码 | 说明 |
|--------|------|
| 200 | 成功 |
| 400 | 请求参数错误 |
| 401 | 未认证或认证失败 |
| 403 | 无权限访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

## [功能映射文档](mapping/README.md)
可以查看应用界面组件与接口的关系
#### 1. [首页](mapping/README.md#1-首页)
  - [公告](mapping/README.md#公告)
  - [搜索](mapping/README.md#搜索)
  - [分类](mapping/README.md#分类)
  - [标签导航栏](mapping/README.md#标签导航栏)
  - [轮播图](mapping/README.md#轮播图)
  - [排行榜](mapping/README.md#排行榜)
  - [推荐（新书推荐）](mapping/README.md#推荐新书推荐)
  - [完结](mapping/README.md#完结)
  - [最近在看](mapping/README.md#最近在看)
  - [热门推荐](mapping/README.md#热门推荐)
#### 2. [书架](mapping/README.md#2-书架)
  - [最近收藏](mapping/README.md#最近收藏)
  - [最近在看](mapping/README.md#最近在看)
  - [猜你喜欢](mapping/README.md#猜你喜欢)
#### 3. [我的](mapping/README.md#3-我的)
  - [反馈找书](mapping/README.md#反馈找书)
  - [浏览历史](mapping/README.md#浏览历史)
#### 4. [广场](mapping/README.md#4-广场)
  - [话题](mapping/README.md#话题)
  - [推荐列表](mapping/README.md#推荐列表)
  - [推荐细节](mapping/README.md#推荐细节)
#### 5. [漫评](mapping/README.md#5-漫评)
  - [漫评](mapping/README.md#漫评)
  - [漫评回复](mapping/README.md#漫评回复)

## 模块列表

#### 1. [设备模块](device/README.md)
  - 设备注册
  - 获取邀请码和邀请数量
  - 获取免广告时间
  - 获取邀请用户列表
  - 获取邀请分享信息
  - 查询设备更新状态

#### 2. [用户模块](member/README.md)
  - 用户注册和登录
  - 用户登出
  - 获取当前登录会员信息
  - 更新用户信息
  - 修改密码
  - 绑定手机号
  - 获取用户基本信息

#### 3. [配置模块](config/README.md)
  - 获取系统配置
  - 检查更新
  - 获取第三方参数

#### 4. [主机模块](host/README.md)
  - 获取主机名

#### 5. [主页公告模块](home_page/README.md)
  - 获取首页公告信息
  - 设置首页公告已读

#### 6. [推荐模块](recommend/README.md)
  - [推荐信息与话题列表](recommend/README.md#推荐信息与话题列表)
    - 漫画推荐列表
    - 获取话题列表
  - [推荐评论](recommend/README.md#推荐评论)
    - 获取漫画推荐评论详情（接口逻辑存在问题，暂不可用）
    - 根据漫画推荐评论id获取评论列表
    - 漫画推荐评论回复列表
    - 漫画推荐动态列表（接口逻辑存在问题，暂不可用）
  - [处理推荐相关信息](recommend/README.md#处理推荐相关信息)
    - [推荐相关](recommend/README.md#推荐相关)
      - 点赞/取消点赞（漫画推荐）
      - 推荐举报
      - 增加漫画推荐
      - 删除漫画推荐
      - 更新漫画推荐
    - [推荐评论相关](recommend/README.md#推荐评论相关)
      - 发表推荐评论
      - 漫画推荐评论点赞
      - 删除自己写的推荐评论
      - 根据recommend_id获取我的评论
    - [推荐评论回复相关](recommend/README.md#推荐评论回复相关)
      - 漫画推荐评论发表回复
      - 漫画推荐评论回复删除
      - 漫画推荐评论回复点赞
    - [推荐评论与推荐评论回复相关](recommend/README.md#推荐评论与推荐评论回复相关)
      - 举报评论&举报回复

#### 7. [漫画历史记录模块（阅读历史不是书架）](cartoon_history/README.md)
  - 加入阅读历史
  - 获取阅读历史
  - 删除阅读历史记录

#### 8. [漫画首页模块](cartoon/README.md)
  - 检查漫画更新信息
  - 猜你喜欢
  - 搜索漫画信息
  - 增加浏览量

#### 9. [同步模块](sync/README.md)
  - 同步标签数据
  - 同步分类数据

#### 10. [书架模块（使用该模块需要注册会员账号）](cartoonshelf/README.md)
  - 加入书架
  - 修改用户书架
  - 删除书架
  - 获取用户书架
  - 用户漫画状态
  - 书架推荐

#### 11. [静态资源模块](static/README.md)
  - [基础资源](static/README.md#基础资源)
    - 拉取域名配置

  - [标签资源](static/README.md#标签资源)
    - 拉取标签配置
    - 拉取标签

  - [栏目资源](static/README.md#栏目资源)
    - 拉取栏目列表
    - 拉取首页栏目静态资源
    - 拉取栏目详情

  - [分类资源](static/README.md#分类资源)
    - 拉取分类列表
    - 拉取分类详情

  - [地区资源](static/README.md#地区资源)
    - 拉取地区列表
    - 拉取地区详情

  - [漫画资源](static/README.md#漫画资源)
    - 拉取漫画包
    - 拉取漫画封面
    - 拉取漫画图片

  - [其他资源](static/README.md#其他资源)
    - 拉取今日热点
    - 拉取轮播图
    - 拉取大家都在看
    - 拉取新书推荐
    - 拉取排行榜
    - 拉取作者还画过
    - 拉取热门发现
    - 拉取更新数据

#### 12. [反馈模块](feedback/README.md)
  - 用户反馈标签列表
  - 用户反馈列表
  - 提交用户反馈
  - 提交章节纠错

#### 13. [日志上报模块](log_report/README.md)
  - 设备信息上报
  - 广告上报

#### 14. [通知模块](notification/README.md)
  - 获取消息通知列表
  - 获取消息详情
  - 获取消息未读总数
  - 消息批量已读

#### 15. [漫评模块](comment/README.md)
  - 根据漫画id获取评论列表
  - 评论详情
  - ta的影评/我的影评
  - 发表评论
  - 点赞
  - 删除评论

#### 16. [漫评回复模块](comment_reply/README.md)
  - 评论回复列表
  - 发表回复
  - 点赞回复
  - 删除回复

## 注意事项

1. 需要认证的接口必须在请求头中包含有效的JWT token
2. 请求体为JSON格式时，Content-Type应设置为application/json
3. 时间戳使用毫秒级Unix时间戳
4. 错误响应会包含具体的错误信息
