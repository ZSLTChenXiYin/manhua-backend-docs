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

## 签名算法

签名用于验证请求的合法性，计算过程如下：

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

## 通用响应格式

```json
{
    "code": 0,           // 状态码，0表示成功
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

1. [用户模块](user/README.md)
   - 用户注册、登录、信息管理等

2. [设备模块（可用）](device/README.md)
   - 设备注册、更新检查等，设备注册完成后，表示该设备可以以游客身份（即设备id）访问功能

3. [漫画模块](cartoon/README.md)
   - 漫画详情、章节、搜索等

4. [配置模块（获取“系统配置”可用）](config/README.md)
   - 系统配置、第三方参数等

5. [短信模块](sms/README.md)
   - 短信验证码发送等

6. [首页模块（可用，接口整理不全后续会有更新）](home/README.md)
   - 首页数据、阅读记录等

7. [广告回调模块](adcallback/README.md)
   - 广告回调处理等

8. [日志上报模块](log-report/README.md)
   - 用户行为日志上报等

9. [OCPC模块](ocpc/README.md)
   - 百度、搜狗、沃隆OCPC相关接口

10. [漫画认证模块](cartoon-auth/README.md)
    - 漫画内容认证相关接口

11. [搜索模块](findcartoon/README.md)
    - 漫画搜索相关接口

12. [特性模块](feature/README.md)
    - 特殊功能接口

## 注意事项

1. 所有请求都需要包含正确的签名，否则会被拒绝
2. 需要认证的接口必须在请求头中包含有效的JWT token
3. 请求体为JSON格式时，Content-Type应设置为application/json
4. 时间戳使用毫秒级Unix时间戳
5. 分页参数统一使用page和page_size
6. 所有接口的响应都是JSON格式
7. 错误响应会包含具体的错误信息 