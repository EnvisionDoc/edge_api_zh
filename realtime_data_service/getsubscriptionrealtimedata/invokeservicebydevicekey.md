# Invoke Service By Device Key

调用设备服务。

## 请求格式

```
 PUT {apigw-address}/dataService/products/{productKey}/devices/{deviceKey}/services/{serviceId}/invoke?orgId={}&requestId={}
{
        "args": 1
}
```

## 请求参数(URI)

| **名称**    | **数据类型** | **是否必须** | **描述**                                                                                                                     |
|:------------|:-------------|:-------------|:-----------------------------------------------------------------------------------------------------------------------------|
| orgId       | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)|
| serviceId   | String       | true         | Service ID                                                                                                                   |
| requestId   | String       | true         | Request ID of the call. If specified, the   request ID will be included in the response for tracking the request.            |
| callbackUrl | String       | false        | After the call, if the service is   required to automatically execute another request, specify the URL of the new   request. |
| timeout     | Long         | false        | Service execution timeout，单位毫秒，默认30000，最大不能超过300000                                                           |
| productKey  | String       | true         | Product key to which the device belongs                                                                                      |
| deviceKey   | String       | true         | Device key                                                                                                                   |

## 请求参数(Body)

| **名称** | **数据类型**        | **是否必须** | **描述**                   |
|:---------|:--------------------|:-------------|:---------------------------|
| args     | Map<String, Object> | true         | Service request parameters |



## 响应参数

| **名称**               | **数据类型** | **描述**                                               |
|:-----------------------|:-------------|:-------------------------------------------------------|
| data                   | Object       | Data returned by the service                           |
| data.requestId         | String       | Service request ID                                     |
| data.messageId         | String       | Service message ID，无须关注                           |
| data.requestMethod     | String       | Service request method，无须关注                       |
| data.callType          | String       | Service request type，“SYNC”表示同步，“ASYNC”表示异步  |
| data.controlChannelId  | String       | data.callType为“ASYNC”时有效，表示遥控返回时的MQ topic |
| data.productKey        | String       | Key of the product to which the service   belongs      |
| data.deviceKey         | String       | Device key                                             |
| data.assetId           | String       | Asset ID of the device                                 |
| data.serviceName       | String       | Service name，无须关注                                 |
| data.callbackUrl       | String       | Callback URL，无须关注                                 |
| data.inputData         | Map          | Input parameter                                        |
| data.outputData        | Map          | Output data                                            |
| data.status            | int          | 控制状态，0表示成功，其他表示失败                      |
| data.msg               | String       | 返回消息，一般是对data.status的描述                    |
| data.submsg            | String       | 返回子消息，一般是对data.status的描述                  |
| data.timeout           | long         | 超时时间                                               |
| data.gmtServiceRequest | long         | Service request time                                   |
| data.gmtServiceReply   | long         | Service reply                                          |
| data.gmtDeviceReply    | long         | Device reply                                           |

## 示例 1

### 返回示例

```
 {
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
               "requestId": "testRequestId",
               "messageId": "2078724684846989312",
               "requestMethod": "thing.service.d",
               "callType": "SYNC",
               "controlChannelId": "controlChannelId1",
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
               "timeout":30,
               "gmtServiceRequest": 1536638267507,
               "gmtServiceReply": 1536638267509,
               "gmtDeviceReply": -1
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
