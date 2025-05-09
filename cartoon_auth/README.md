# 漫画鉴权模块 API 文档

## 1. 获取漫画鉴权key

### 接口说明
获取漫画鉴权key。

### 请求信息
- 请求路径：`/api/v1/b/:rand`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - versionName: 版本号
  - device: 设备号

- 请求参数（json）：
```json
{
  "i": "<integer>",  // AppId 应用Id
  "p": "<integer>", // PlatformId 渠道Id
  "t": "<integer>", // 时间戳
  "r": "<integer>", // 随机数
  "s": "<string>", // Sign签名：算法为md5("p=渠道Id&t=时间戳&r=随机数&s=公钥md5后的字符串&pl=渠道Id")
  
  "origin": "<string>" // 来源（已弃用，填写）
}
```

### 响应信息
```json
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