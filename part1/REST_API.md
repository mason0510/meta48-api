# REST API for Ant Chain   

## 开始使用   
REST，即Representational State Transfer的缩写，是目前最流行的一种互联网软件架构。它结构清晰、符合标准、易于理解、扩展方便，正得到越来越多网站的采用。其优点如下：
- 在RESTful架构中，每一个URL代表一种资源；
- 客户端和服务器之间，传递这种资源的某种表现层；
- 客户端通过四个HTTP指令，对服务器端资源进行操作，实现“表现层状态转化”。  

建议开发者使用REST API进行合约调用部署等操作。

## 请求交互 

REST访问的根URL:`http://101.71.63.249/api/v1`

所有请求基于Https协议，请求头信息中contentType需要统一设置为：`application/json`

请求交互说明
1. 请求参数：根据接口请求参数规定进行参数封装。
2. 提交请求参数：将封装好的请求参数通过POST方式提交至服务器。
3. 服务器响应：服务器首先对用户请求数据进行参数安全校验，通过校验后根据业务逻辑将响应数据以JSON格式返回给用户。
4. 数据处理：对服务器响应数据进行处理。 

## API参考  

### 获取积分数据
1. POST /api/v1/antScore/queryAccountScore    获取积分余额

URL `http://101.71.63.249/api/v1/queryAccountScore`  100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/queryAccountScore
# Response
{
    "code": 0,
    "message": "success",
    "data": {
        "balance": "9000965105"
    }
}
```

返回值说明

```
balance:账户积分余额

```

请求参数

| 参数名        |	参数类型|	必填| 	描述         |
|:-----------| :-----   | :-----    |:------------|
| contractId |String|是| 用户的合约Id     |
| userName   |String|是| 用户名         |
| chain      |String|是| 区块链的类别      |
| api_key    |String|是| 用户申请的apiKey |
| sign       |String|是| 请求参数的签名     |

2. POST /api/v1/antScore/issue    发行积分

URL `http://101.71.63.249/api/v1/antScore/issue`  访问频率 100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/antScore/issue
# Response
{
    "code": 0,
    "message": "success",
    "data": null
}
```

返回值说明

```
message:发行成功

```

请求参数

|参数名|	参数类型|	必填| 	描述            |
| :-----    | :-----   | :-----    |:---------------|
|totalSupply|String|是| 发行的积分数量，每次调用累加 |
| chain      |String|是| 区块链的类别         |
| api_key    |String|是| 用户申请的apiKey    |
| sign       |String|是| 请求参数的签名        |

3. POST /api/v1/antScore/transferFor    获取积分余额

URL `http://101.71.63.249/api/v1/transferFor`  100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/transferFor
# Response
{
    "code": 0,
    "message": "success",
    "data": {
        "transferHash": "227015d7f23192d40f57d172dbb9b98020dd2d68e9a57b622e3b8de6541c4006"
    }
}
```

返回值说明

```
transferHash:交易哈希

```

请求参数

| 参数名        |	参数类型|	必填| 	描述         |
|:-----------| :-----   | :-----    |:------------|
| from       |String|是| 转账来自于谁      |
| to         |String|是| 到谁的账户       |
| id         |String|是| 转账数额        |
| contractId |String|是| 合约Id        |
| chain      |String|是| 区块链的类别      |
| key        |String|是| 用户申请的apiKey |
| sign       |String|是| 请求参数的签名     |

4. POST /api/v1/antScore/transfer    admin账户为用户充值

URL `http://101.71.63.249/api/v1/transfer`  100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/transfer
# Response
{
    "code": 0,
    "message": "success",
    "data": {
        "transferHash": "227015d7f23192d40f57d172dbb9b98020dd2d68e9a57b622e3b8de6541c4006"
    }
}
```

返回值说明

```
transferHash:交易哈希

```

请求参数

| 参数名        |	参数类型|	必填| 	描述         |
|:-----------| :-----   | :-----    |:------------|
| to         |String|是| 到谁的账户       |
| amount         |String|是| 转账数额        |
| contractId |String|是| 合约Id        |
| chain      |String|是| 区块链的类别      |
| key        |String|是| 用户申请的apiKey |
| sign       |String|是| 请求参数的签名     |

5. POST /api/v1/antScore/transferFrom    用户间转移积分

URL `http://101.71.63.249/api/v1/antScore/transferFrom`  100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/antScore/transferFrom
# Response
{
    "code": 0,
    "message": "success",
    "data": true
}
```

返回值说明

```
transferHash:交易哈希

```

请求参数

| 参数名        |	参数类型|	必填| 	描述         |
|:-----------| :-----   | :-----    |:------------|
| from       |String|是| 转账来自于谁      |
| to         |String|是| 到谁的账户       |
| id         |String|是| 转账数额        |
| contractId |String|是| 合约Id        |
| chain      |String|是| 区块链的类别      |
| key        |String|是| 用户申请的apiKey |
| sign       |String|是| 请求参数的签名     |

6. POST /api/v1/antScore/approve    用户为其他人授权使用积分额度

URL `http://101.71.63.249/api/v1/antScore/approve`  100次/1秒

示例

```
# Request
POST http://101.71.63.249/api/v1/antScore/approve
# Response
{
    "code": 0,
    "message": "success",
    "data": null
}
```

返回值说明

```
message:交易哈希

```

请求参数

| 参数名        |	参数类型|	必填| 	描述         |
|:-----------| :-----   | :-----    |:------------|
| fromUser       |String|是| 转账来自于谁      |
| to         |String|是| 授信额度        |
| amount         |String|是| 转账数额        |
| contractId |String|是| 合约Id        |
| chain      |String|是| 区块链的类别      |
| key        |String|是| 用户申请的apiKey |
| sign       |String|是| 请求参数的签名     |

