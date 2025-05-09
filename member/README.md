# 用户模块 API 文档
1. [用户注册和登录](#1-用户注册和登录)
2. [用户登出](#2-用户登出)
3. [获取当前登录会员信息](#3-获取当前登录会员信息)
4. [更新用户信息](#4-更新用户信息)
5. [修改密码](#5-修改密码)
6. [绑定手机号](#6-绑定手机号)
7. [获取用户基本信息](#7-获取用户基本信息)

## 1. 用户注册和登录

### 接口说明
用户登录接口，用于验证用户身份并获取访问令牌。

### 请求信息
- 请求路径：`/api/v1/login`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json
  - device: 设备号
  - platformId: 平台ID
  - appId: 应用ID
  - channelId: 渠道ID（已弃用，填1即可）

- 请求参数
```json
{
  "captcha": "1234", // 验证码
  "event": "reg", // 事件类型，reg为注册，login为登录
  "password": "test", // 密码，明文即可
  "username": "test", // 昵称
  "mobile": "15523266543" // 手机号
}
```

### 响应信息
```json
{
    "code": 200,
    "data": {
        "id": 446420,
        "username": "test",
        "email": "",
        "avatar": "",
        "gender": 0,
        "score": 0,
        "mobile": "15523266543",
        "nickname": "用户92625383",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NzgzMDM3ODYsImlkZW50aXR5Ijo0NDY0MjAsIm5pY2UiOiJ0ZXN0Iiwib3JpZ19pYXQiOjE3NDY3Njc3ODZ9.uWRnMMxlMT8DGHNc6TR7EhloajQVM1KF_Yy7V1bBhXY",
        "birthday": null
    },
    "msg": "登录成功"
}
```

## 2. 用户登出

### 接口说明
用户登出接口，用于清除用户的登录状态。

### 请求信息
- 请求路径：`/api/v1/logout`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}

### 响应信息
```json
{
    "code": 200,
    "data": null,
    "msg": "退出成功"
}
```

## 3. 获取当前登录会员信息

### 接口说明
获取当前登录用户的详细信息。

### 请求信息
- 请求路径：`/api/v1/member`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - appId: 应用ID

### 响应信息
```json
{
    "requestId": "884e5019-ea71-4804-b12f-4f9326760d65",
    "code": 200,
    "msg": "查询成功",
    "data": {
        "id": 446420,  // 用户ID
        "username": "test",  // 用户名
        "email": "",  // 邮箱
        "avatar": "",  // 头像URL
        "gender": 0,  // 性别（0：未知，1：男，2：女）
        "score": 0,  // 积分
        "mobile": "15523266543",  // 手机号
        "nickname": "用户92625383",  // 昵称
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE3NzgzMDQ2NDEsImlkZW50aXR5Ijo0NDY0MjAsIm5pY2UiOiJ0ZXN0Iiwib3JpZ19pYXQiOjE3NDY3Njg2NDF9.ERwlm5vwB8I9fz9xp1lNyLDddSplTsuVS_Y6BE25EBk",
        "birthday": null
    }
}
```

## 4. 更新用户信息

### 接口说明
更新当前登录用户的基本信息。

### 请求信息
- 请求路径：`/api/v1/updateprofile`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json
  - device: 设备号
  - appId: 应用ID

- 请求参数
```json
{
    "gender": 1,          // 性别,0.未知,1.男,2.女
    "nickname": "测试程序员",        // 昵称，不能为空
    "avatar": "" // 头像，为空则不更新
}
```

### 响应信息
```json
{
    "requestId": "12459910-5c16-46f7-9262-8f0c1cb081c6",
    "code": 200,
    "msg": "信息审核中，请稍后查看",
    "data": null
}
```

## 5. 修改密码

### 接口说明
修改当前登录用户的密码。

### 请求信息
- 请求路径：`/api/v1/changePassword`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Content-Type: application/json

- 请求参数
```json
{
    "mobile": "15523266543",
    "code": "1234",
    "userName": "test",
    "newPassword": "new_test"
}
```

### 响应信息
```json
{
    "requestId": "b47852fe-0b58-45c1-8f43-e7e238baa921",
    "code": 200,
    "msg": "修改成功",
    "data": null
}
```

## 6. 绑定手机号

### 接口说明
绑定用户的手机号。由于我们在注册的时候就已经绑定了手机号，所以这个接口一般不会被调用。

### 请求信息
- 请求路径：`/api/v1/bindMobile`
- 请求方法：POST
- 请求头：
  - X-Package: 应用包名
  - Authorization: Bearer {token}
  - Content-Type: application/json

- 请求参数
```json
{
    "mobile": "15523266543",
    "code": "1234"
}
```

### 响应信息
```json
{
    "requestId": "507246aa-fe37-4cfb-80fe-e3bbadcb246d",
    "code": 500,
    "msg": "您已绑定过手机",
    "status": "error",
    "data": null
}
```

## 7. 获取用户基本信息

### 接口说明
获取用户的基本信息（昵称和头像）。

### 请求信息
- 请求路径：`/api/v1/memberInfo`
- 请求方法：GET
- 请求头：
  - X-Package: 应用包名

- 请求参数（表单数据）：
  - memberId: 用户ID

### 响应信息
```json
{
    "requestId": "47ae374f-43cd-4e7a-ada9-b8520d224bac",
    "code": 200,
    "msg": "获取成功",
    "data": {
        "nickname": "测试程序员",
        "avatar": ""
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

1. 所有需要认证的接口都必须在请求头中包含有效的JWT token
2. 密码在传输前需要进行MD5加密
3. 手机号验证码的有效期为5分钟
4. 头像URL必须是完整的可访问地址
5. 用户状态为0时无法登录系统 