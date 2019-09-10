# Set Measurepoint By Device Key

## 请求格式

```
 PUT /dataService/products/{productKey}/devices/{deviceKey}/measurepoints/{measurepointId}/set?orgId={}&timeout={}&requestId={}
{
        "arg":10
}
```

## 请求参数(URI)

| **名称**       | **数据类型** | **是否必须** | **示例值** | **描述**                                                    |
|:---------------|:-------------|:-------------|:-----------------|:------------------------------------------------------------|
| orgId          | String       | true         |                  | Organization ID                                             |
| measurepointId | String       | true         | measurepoint1    | Measurepoint ID                                             |
| productKey     | String       | true         |                  | Product Key                                                 |
| deviceKey      | String       | true         |                  | Device Key                                                  |
| timeout        | Long         | false        | 30000            | Service timeout ，单位毫秒，默认为30000，最大不能超过300000 |
| requestId      | String       | true         |                  |                                                             |
| callbackUrl    | String       | false        |                  | Callback URL，无须关注                                      |

## 请求参数(Body)

| **名称** | **数据类型** | **是否必须** | **示例值** | **描述**       |
|:---------|:-------------|:-------------|:-----------------|:---------------|
| value    | Map          | true         | {   "arg":10   } | 需要写的数据值 |

## 响应参数

| **名称**                       | **数据类型** | **描述**                                      |
|:-------------------------------|:-------------|:----------------------------------------------|
| data                           | Object       | Response data                                 |
| data.requestId                 | String       | Request ID                                    |
| data.orgId                     | String       | Org ID                                        |
| data.callType                  | String       | "SYNC"表示同步，"ASYNC"表示异步               |
| data.setMeasurepointChannelId  | String       | data.callType为异步时有效，写值返回的MQ topic |
| data.productKey                | String       | Product key                                   |
| data.deviceKey                 | String       | Device key                                    |
| data.assetId                   | String       | Asset ID                                      |
| data.measurepointId            | String       | 写值的数据点ID                                |
| data.callbackUrl               | String       | callback URL，无须关注                        |
| data.inputData                 | Map          | Input data                                    |
| data.status                    | int          | 0表示成功，其他表示失败                       |
| data.msg                       | String       | 返回消息，一般是对data.status的描述           |
| data.submsg                    | String       | 返回消息，一般是对data.status的描述           |
| data.timeout                   | long         | 超时时间，单位为毫秒，默认30000               |
| data.gmtSetMeasurepointRequest | long         | 写值请求时间戳                                |
| data.gmtSetMeasurepointReply   | long         | 写值返回时间戳                                |
## 示例 1

### 返回示例

```
 {

        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
               "requestId": "testRequestId",
               "orgId":"aaa",
               "callType": "SYNC",
               "setMeasurepointChannelId": "DATASVC.SET.setMeasurepointChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "measurepointId": "measurepointId1",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "status":0,
               "msg":"SUCCESS",
               "submsg":null,
               "timeout":30000,
               "gmtSetMeasurepointRequest": 1536638267507,
               "gmtSetMeasurepointReply": 1536638267509,
        }
}
```

### 异常示例

```
{
        "status": 400,
        "msg": "Invalid Argument orgId",
        "submsg": "orgId does not exist"
}
```
