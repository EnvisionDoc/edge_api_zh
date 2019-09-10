# Multi Invoke Service Async

执行异步多点控制时，需要先使用createControlChannel 创建控制通道，输入参数中controlChannelId的值就是填写createControlChannel创建的通道。

## 请求格式

```
PUT /dataService/devices/multiInvoke?orgId={}
{
        "data": [
               {
                       "requestId":"dfsadfdsafdsaf",
                       "orgId":null,
                       "callType":"ASYNC",
                       "controlChannelId":"DATASVC.CONTROL.afdasfasdf",
                       "productKey":"dfasdf",
                       "deviceKey":"dsfa",
                       "assetId":"aaa",
                       "serviceId":"bbb",
                       "callbackUrl":null,
                       "inputData":{
                               "arg":10
                       },
                       "timeout":30000,
                       "gmtServiceRequest":132132465464
               },
               {
                       "requestId":"erwerwradf",
                       "orgId":null,
                       "callType":"ASYNC",
                       "controlChannelId":"DATASVC.CONTROL.afdasfasdf",
                       "productKey":"dfasdf",
                       "deviceKey":"dsfa",
                       "assetId":"aaa",
                       "serviceId":"ccc",
                       "callbackUrl":null,
                       "inputData":{
                               "arg":10
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

| **名称**               | **数据类型**                 | **是否必须** | **描述**                                                  |
|:-----------------------|:-----------------------------|:-------------|:----------------------------------------------------------|
| data                   | `List<ServiceInvokeRequest>` | true         |                                                           |
| data.requestId         | String                       | true         | 控制唯一标识                                              |
| data.orgId             | String                       | true         | ORG ID                                                    |
| data.callType          | String                       | false        | 会自动置为"ASYNC"                                         |
| data.controlChannelId  | String                       | true         | 异步控制返回使用的MQ TOPIC                                |
| data.productKey        | String                       | true         | product key                                               |
| data.deviceKey         | String                       | true         | device key                                                |
| data.assetId           | String                       | true         | asset ID，要么填写product key+device key，要么填写assetId |
| data.serviceId         | String                       | true         | service ID                                                |
| data.callbackUrl       | String                       | false        | callback URL，无须理会                                    |
| data.inputData         | Map                          | false        | 输入值                                                    |
| data.timeout           | long                         | false        | 超时时间，单位为毫秒，默认30000，最大300000               |
| data.gmtServiceRequest | long                         | false        | 控制请求时间                                              |


## 响应参数

| **名称**               | **数据类型**             | **描述**                                               |
|:-----------------------|:-------------------------|:-------------------------------------------------------|
| data                   | List<ServiceInvokeReply> | Data returned by the service                           |
| data.requestId         | String                   | Service request ID                                     |
| data.messageId         | String                   | Service message ID，无须关注                           |
| data.requestMethod     | String                   | Service request method，无须关注                       |
| data.callType          | String                   | Service request type，“SYNC”表示同步，“ASYNC”表示异步  |
| data.controlChannelId  | String                   | data.callType为“ASYNC”时有效，表示遥控返回时的MQ topic |
| data.productKey        | String                   | Key of the product to which the service   belongs      |
| data.deviceKey         | String                   | Device key                                             |
| data.assetId           | String                   | Asset ID of the device                                 |
| data.serviceName       | String                   | Service name，无须关注                                 |
| data.serviceId         | String                   | Service Id                                             |
| data.callbackUrl       | String                   | Callback URL，无须关注                                 |
| data.inputData         | Map                      | Input parameter                                        |
| data.outputData        | Map                      | Output data                                            |
| data.status            | int                      | 控制状态，0表示成功，其他表示失败                      |
| data.msg               | String                   | 返回消息，一般是对data.status的描述                    |
| data.submsg            | String                   | 返回子消息，一般是对data.status的描述                  |
| data.timeout           | long                     | 超时时间                                               |
| data.gmtServiceRequest | long                     | Service request time                                   |
| data.gmtServiceReply   | long                     | Service reply                                          |
| data.gmtDeviceReply    | long                     | Device reply                                           |

## 示例 1

### 返回示例

除了整体的参数错误（如body中数据格式错误）、orgId错误，其他立即能发现的控制错误均会在restful接口中直接返回（如某个控制的serviceId没填，超时时间设的不对，requestId为空等），restful接口中返回的成功为下发控制命令成功，并不表示控制成功，控制结果会在指定的MQ TOPIC中返回。

```
 {

        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": [{
               "requestId": "testRequestId1",
               "messageId": null,
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "serviceName": "testService",
               "serviceId": "d",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "outputData": {},
               "status":0,
               "msg":"SUCCESS",
               "submsg":null,
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509,
               "gmtDeviceReply": -1
        },
        {
               "requestId": "testRequestId2",
               "messageId": null,
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "serviceName": "testService",
               "serviceId": "d",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "outputData": {},
               "status":1000,
               "msg":"para error",
               "submsg":"para error",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509,
               "gmtDeviceReply": -1
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
               "messageId": null,
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "serviceName": "testService",
               "serviceId": "d",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "outputData": {},
               "status":0,
               "msg":"SUCCESS",
               "submsg":"SUCCESS",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509,
               "gmtDeviceReply": -1
        },
        {
               "requestId": "testRequestId2",
               "messageId": null,
               "requestMethod": "thing.service.d",
               "callType": "ASYNC",
               "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
               "productKey": "6Bt59ySj",
               "deviceKey": "zBAofs6D4s",
               "assetId": "YCdyvNmc",
               "serviceName": "testService",
               "serviceId": "d",
               "callbackUrl": null,
               "inputData": {
                       "testArg": 1.0
               },
               "outputData": {},
               "status":1000204,
               "msg":"invoke service error",
               "submsg":"invoke service error",
               "timeout":30000,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509,
               "gmtDeviceReply": -1
        }]
}
```
