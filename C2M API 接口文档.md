# C2M接口文档

## 1.1. 接口说明

- 接口基准地址：`http://c2m.tq.yhlcps.com/backend/c2m`
- 服务端已开启 CORS 跨域支持
- 暂时先不做接口认证
- 使用 HTTP Status Code 标识状态
- 数据返回格式统一使用 JSON

### 1.1.1. 支持的请求方法

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- DELETE（DELETE）：从服务器删除资源。

### 1.1.2. 通用返回状态说明

| 状态码 | 含义                | 说明 |
| -------- | --------------------- | -------------------- |
| 200      | OK                    | 请求成功                                      |
| 201      | CREATED               | 创建成功                                      |
| 204      | DELETED               | 删除成功                                      |
| 400      | BAD REQUEST           | 请求的地址不存在或者包含不支持的参数          |
| 401      | UNAUTHORIZED          | 未授权                                        |
| 403      | FORBIDDEN             | 被禁止访问                                    |
| 404      | NOT FOUND             | 请求的资源不存在                              |
| 422      | Unprocesable entity   | [POST/PUT] 当创建一个对象时，发生一个验证错误 |
| 500      | INTERNAL SERVER ERROR | 内部错误      |

------

## 1.2. 订单

### 1.2.1. 创建订单

#### 1.2.1.1. 名片

-   请求路径：order

-   请求方法：post

-   请求参数：

| 参数名              | 参数说明       | 备注     |
| ------------------- | -------------- | -------- |
| cmd                 | 消息类型       | 不能为空 |
| goods_type          | 密码           | 不能为空 |
| user_openid         | 用户微信openID | 不能为空 |
| draw_info.body_name | 打印的姓名     |          |
| draw_info.cor_name  | 打印的公司名   |          |
| draw_info.cor_addr  | 打印的地址     |          |
| draw_info.cor_phone | 打印的电话号   |          |
| draw_info.cor_email | 打印的邮箱     |          |

-   请求数据：

```json
{
    "cmd": "create_order",
    "goods_type": "名片",
    "user_openid": "user_name",
    "draw_info": {
        "body_name": "body_name",
        "cor_name": "cor_name",
        "cor_addr": "cor_addr",
        "cor_phone": "cor_phone",
        "cor_email": "cor_email"
    }
}
```

-   响应数据：

```json
{
    "meta": {
        "status": 200,
        "message": "order create success"
    }
}
```

#### 1.2.1.2. 名片夹

-   请求路径
-   请求方法
-   请求参数
-   请求数据
-   响应参数
-   响应数据

#### 1.2.1.2. 后略

### 1.2.2 查询订单

-   请求路径：order
-   请求方法：get
-   请求参数

| 参数名   | 参数说明     | 备注     |
| -------- | ------------ | -------- |
| pagenum  | 当前页码     | 不能为空 |
| query    | 查询参数     | 可以为空 |
| pagesize | 每页显示条数 | 不能为空 |

-   请求数据
-   响应参数

```json
{
    "data": {
        "totalpage": 5,
        "pagenum": 4,
        "orders": [
            {
                "id": 1,
                "username": "<username>",
                "mobile":"18616358651",
                "good_type": 1,
                "email": "tige112@163.com",
                "create_time": "2020-11-09T20:36:26.000Z",
            },
          ...,
            {
                "id": 99,
                "username": "<username>",
                "mobile": "13950026283",
                "good_type": 3,
                "email": "tiget@qq.com",
                "create_time": "2020-11-09T21:39:26.000Z",
            }
        ]
    },
    "meta": {
        "msg": "获取成功",
        "status": 200
    }
}
```

- 响应数据

  1.2.3 删除订单

  - 请求路径：order

  - 请求方法：post

  - 请求参数

    | 参数名 | 参数说明 | 备注 |
    | ------ | -------- | ---- |
    |        |          |      |
    |        |          |      |
    |        |          |      |

    

