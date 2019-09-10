# Multi Set Measurepoint Async

执行异步多点写值时，需要先使用createSetMeasurepointChannel 创建写值通道，输入参数中setMeasurepointChannelId的值就是填写createSetMeasurepointChannel创建的通道。

## 请求格式

```
 PUT /dataService/devices/multiSet?orgId={}
{
        "data": [
               {
                       "requestId":"dfsadfdsafdsaf",
                       "orgId":"adadad",
                       "callType":"ASYNC",
                       "setMeasurepointChannelId":"DATASVC.SET.afdasfasdf",
                       "productKey":"dfasdf",
                       "deviceKey":"dsfa",
                       "assetId":"aaa",
                       "measurepointId":"bbb",
                       "callbackUrl":null,
                       "inputData":{
                               "arg":10
                       },
                       "timeout":30000,
                       "gmtServiceRequest":132132465464
               },
               {
                       "requestId":"12321321321",
                       "orgId":"adadad",
                       "callType":"ASYNC",
                       "setMeasurepointChannelId":"DATASVC.SET.afdasfasdf",
                       "productKey":"dfasdf",
                       "deviceKey":"dsfa",
                       "assetId":"aaa",
                       "measurepointId":"ccc",
                       "callbackUrl":null,
                       "inputData":{
                               "arg":11
                       },
                       "timeout":30000,
                       "gmtServiceRequest":132132465464
               }
        ]
}
```

## 请求参数(URI)

| **名称** | **数据类型** | **是否必须** | **描述**        |
|:---------|:-------------|:-------------|:----------------|
| orgId    | String       | true         | Organization ID |


## 请求参数(Body)

| **名称**                      | **数据类型**                   | **是否必须** | **描述**                                                  |
|:------------------------------|:-------------------------------|:-------------|:----------------------------------------------------------|
| data                          | `List<SetMeasurepointRequest>` | true         |                                                           |
| data.requestId                | String                         | true         | 写值唯一标识                                              |
| data.orgId                    | String                         | true         | ORG ID                                                    |
| data.callType                 | String                         | false        | 会自动置为"ASYNC"                                         |
| data.setMeasurepointChannelId | String                         | true         | 异步写值返回使用的MQ TOPIC                                |
| data.productKey               | String                         | true         | product key                                               |
| data.deviceKey                | String                         | true         | device key                                                |
| data.assetId                  | String                         | true         | asset ID，要么填写product key+device key，要么填写assetId |
| data.measurepointId           | String                         | true         | measurepoint ID                                           |
| data.callbackUrl              | String                         | false        | callback URL，无须理会                                    |
| data.inputData                | Map                            | false        | 输入值                                                    |
| data.timeout                  | long                           | false        | 超时时间，单位为毫秒，默认30000，最大300000               |
| data.gmtServiceRequest        | long                           | false        | 控制请求时间                                              |


## 响应参数

| **名称**                      | **数据类型**             | **描述**                                               |
|:------------------------------|:-------------------------|:-------------------------------------------------------|
| data                          | List<ServiceInvokeReply> | Data returned by the service                           |
| data.requestId                | String                   | Service request ID                                     |
| data.orgId                    | String                   | org ID                                                 |
| data.callType                 | String                   | Service request type，“SYNC”表示同步，“ASYNC”表示异步  |
| data.setMeasurepointChannelId | String                   | data.callType为“ASYNC”时有效，表示写值返回时的MQ topic |
| data.productKey               | String                   | Key of the product to which the service   belongs      |
| data.deviceKey                | String                   | Device key                                             |
| data.assetId                  | String                   | Asset ID of the device                                 |
| data.measurepointId           | String                   | measurepoint ID                                        |
| data.callbackUrl              | String                   | Callback URL，无须关注                                 |
| data.inputData                | Map                      | Input parameter                                        |
| data.status                   | int                      | 写值状态，0表示成功，其他表示失败                      |
| data.msg                      | String                   | 返回消息，一般是对data.status的描述                    |
| data.submsg                   | String                   | 返回子消息，一般是对data.status的描述                  |
| data.timeout                  | long                     | 超时时间                                               |
| data.gmtServiceRequest        | long                     | Service request time                                   |
| data.gmtServiceReply          | long                     | Service reply                                          |

## 示例 1

### 返回示例

除了整体的参数错误（如body中数据格式错误）、orgId错误，其他立即能发现的控制错误均会在restful接口中直接返回（如某个写值的measurePointId没填，超时时间设的不对，requestId为空等），restful接口中返回的成功为下发写值命令成功，并不表示写值成功，写值结果会在指定的MQ TOPIC中返回。

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": [{
               "requestId": "testRequestId1",
               "orgId": "aaa",
               "callType": "ASYNC",
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
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509
        },
        {
               "requestId": "testRequestId2",
               "orgId": "aaa",
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "setMeasurepointChannelId": "DATASVC.SET.setMeasurepointChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "measurepointId": "measurepointId2",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "status":1000,
               "msg":"para error",
               "submsg":"para error",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509
        }]
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

## 示例 2

### 返回示例 In AMQ

```
{
        "data": [{
               "requestId": "testRequestId1",
               "orgId": "aaa",
               "callType": "ASYNC",
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
               "submsg":"SUCCESS",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509
        },
        {
               "requestId": "testRequestId2",
               "orgId": "aaa",
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "setMeasurepointChannelId": "DATASVC.SET.setMeasurepointChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "measurepointId": "measurepointId2",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "status":1000205,
               "msg":"write data error",
               "submsg":"write data error",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509
        }]
}
```
