# API 文档

## 基本信息

- 基础URL: `http://manhua-api.nftx.pics`
- 所有请求和响应均使用JSON格式
- 字符编码：UTF-8

## 通用请求头

| 请求头 | 说明 | 示例 |
|--------|------|------|
| Authorization | JWT认证token，格式为"Bearer {token}" | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9... |
| X-Package | 应用包名，用于签名验证 | com.meimanyuan.app |
| sign | 请求签名，用于验证请求合法性 | kK_abc123_xyz789 |

## 通用响应格式

```json
{
    "code": 200,           // 状态码，200表示成功
    "message": "success", // 状态描述
    "data": {            // 响应数据，具体结构见各接口文档
        // ...
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

## 模块列表

1. [设备模块](device/README.md)
  - 设备注册
  - 获取邀请码和邀请数量
  - 获取免广告时间
  - 获取邀请用户列表
  - 获取邀请分享信息
  - 查询设备更新状态

2. [用户模块](member/README.md)
  - 用户注册和登录
  - 用户登出
  - 获取当前登录会员信息
  - 更新用户信息
  - 修改密码
  - 绑定手机号
  - 获取用户基本信息

3. [配置模块](config/README.md)
  - 获取系统配置
  - 检查更新
  - 获取第三方参数

4. [主机模块](host/README.md)
  - 获取主机名

5. [主页公告模块](home_page/README.md)
  - 获取首页公告信息
  - 设置首页公告已读

6. [推荐模块（仅“推荐信息与话题列表”下的接口可用）](recommend/README.md)
  - [推荐信息与话题列表](recommend/README.md#推荐信息与话题列表)
    - 漫画推荐列表
    - 获取话题列表
  - [推荐评论](recommend/README.md#推荐评论)
    - 获取漫画推荐评论详情
    - 获取推荐评论列表
    - 获取推荐评论回复列表
    - 获取推荐动态
  - [处理推荐相关信息](recommend/README.md#处理推荐相关信息)
    - 推荐相关
      - 点赞推荐
      - 举报推荐
      - 添加推荐
      - 删除推荐
      - 更新推荐
    - 推荐评论相关
      - 添加推荐评论
      - 点赞推荐评论
      - 删除推荐评论
      - 获取推荐评论详情
      - 举报推荐评论
    - 推荐评论回复相关
      - 添加推荐评论回复
      - 点赞推荐评论回复
      - 删除推荐评论回复

7. [漫画历史记录模块](cartoon_history/README.md)
  - 加入阅读历史
  - 获取阅读历史
  - 删除阅读历史记录

## 注意事项

1. 所有请求都需要包含正确的签名，否则会被拒绝
2. 需要认证的接口必须在请求头中包含有效的JWT token
3. 请求体为JSON格式时，Content-Type应设置为application/json
4. 时间戳使用毫秒级Unix时间戳
5. 分页参数统一使用page和page_size
6. 所有接口的响应都是JSON格式
7. 错误响应会包含具体的错误信息

## 请求头签名算法

请求头签名用于验证请求的合法性，计算过程如下：

1. 准备数据：
   - 请求方法（GET/POST等）
   - 请求URL（不包含域名）
   - 请求体（如果有）
   - 包名对应的证书数据

2. 计算步骤：
   ```python
   # 伪代码
   def calculate_sign(method, url, body, package_name):
       # 1. 拼接方法和URL
       method_url = method + url
       
       # 2. 获取包名对应的证书数据
       cert_data = get_cert_data(package_name)
       
       # 3. 填充数据到固定长度
       method_url_padded = pad(method_url, 1145, 0x1)
       body_padded = pad(body, 1145, 0x3)
       
       # 4. 合并数据
       chunk = xor(method_url_padded, cert_data)
       chunk = xor(chunk, body_padded)
       
       # 5. 生成时间戳
       timestamp = get_current_timestamp()
       timestamp = timestamp ^ 0x2301
       timestamp = timestamp ^ (0x6745 << 32)
       
       # 6. 将时间戳写入chunk
       for i in range(8):
           chunk[i+412] = chunk[i+412] ^ timestamp_bytes[i]
       
       # 7. 计算Blake2b-512哈希
       hash = blake2b_512(chunk)
       
       # 8. z85编码
       hash_z85 = z85_encode(hash)
       time_z85 = z85_encode(timestamp_bytes)
       
       # 9. 生成最终签名
       return f"kK_{hash_z85}_{time_z85}"
   ```
