# Create Subscribe Group

创建订阅组。

## 请求格式

```
 POST {apigw-address}/dataService/subscribeGroups?orgId={}
{
        "subscribeGroupId": "DATASVC.SUB.group1",
        "enable": true,
        "persistent": true,
        "subscribeAll": false,
        "subscribeModelList": ["model1", "model2", "model3"],
        "subscribeProductList": ["product1", "product2", "product3"],
        "subscribeAssetList": ["asset1", "asset2", "asset3"],
        "subscribeDeviceList":[{
               "productKey": "productKey1",
               "deviceKey": "deviceKey1"
        },
        {
               "productKey": "productKey2",
               "deviceKey": "deviceKey2"

        }],
        "subscribeModelPointList":[{
               "modelId": "model1",
               "pointList": ["point1", "point2", "point3"]
        },
        {
               "modelId": "model2",
               "pointList": ["point1", "point2", "point3"]
        }],
        "subscribePointList":[{
               "assetId": "asset10",
               "productKey": "productKey10",
               "deviceKey": "deviceKey10",
               "pointList": ["point1", "point2", "point3"]
        },
        {
               "assetId": "",
               "productKey": "productKey11",
               "deviceKey": "deviceKey11",
               "pointList": ["point1", "point2", "point3"]
        }]

}
```

## 请求参数(URI)

| **名称** | **数据类型** | **是否必须** | **描述**        |
|:---------|:-------------|:-------------|:----------------|
| orgId    | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid) |


## 请求参数(Body)

| **名称**                       | **数据类型**              | **是否必须**                                           | **描述**                             |
|:-------------------------------|:--------------------------|:-------------------------------------------------------|:-------------------------------------|
| subscribeGroupId               | String                    | Subscribe group Id                                     | subscribeGroupId，应用指定，不能重复 |
| enable                         | Boolean                   | Whether the subscribe group is enable                  |                                      |
| persistent                     | Boolean                   | Whether the subscribe group is persistent              |                                      |
| subscribeAll                   | Boolean                   | Whether the subscribe group subscribes to   all points |                                      |
| subscribeModelList             | List<String>              | 订阅的模型列表，数据元素为modelId                      |                                      |
| subscribeProductList           | List<String>              | 订阅的product列表，数据元素为productKey                |                                      |
| subscribeAssetList             | List<String>              | 订阅的asset列表，数据元素为assetId                     |                                      |
| subscribeDeviceList            | List<subscribeDeviceInfo> | 订阅的device列表                                       |                                      |
| subscribeDeviceList.productKey | String                    | device的product   key                                  |                                      |

## 响应参数

| **名称**                               | **数据类型**                  | **描述**                                                                                                               |
|:---------------------------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| data                                   |                               |                                                                                                                        |
| data.id                                | String                        | 内部使用的id，无须关注                                                                                                 |
| data.subscribeGroupId                  | String                        | Subscribe group Id                                                                                                     |
| data.enable                            | Boolean                       | Whether the subscribe group is enable                                                                                  |
| data.persistent                        | Boolean                       | Whether the subscribe group is persistent                                                                              |
| data.subscribeAll                      | Boolean                       | Whether the subscribe group subscribes to   all points                                                                 |
| data.subscribeModelList                | List<String>                  | 订阅的模型列表，数据元素为modelId                                                                                      |
| data.subscribeProductList              | List<String>                  | 订阅的product列表，数据元素为productKey                                                                                |
| data.subscribeAssetList                | List<String>                  | 订阅的asset列表，数据元素为assetId                                                                                     |
| data.subscribeDeviceList               | List<subscribeDeviceInfo>     | 订阅的device列表                                                                                                       |
| data.subscribeDeviceList.productKey    | String                        | device的product   key                                                                                                  |
| data.subscribeDeviceList.deviceKey     | String                        | device的device key                                                                                                     |
| data.subscribeModelPointList           | List<subscribeModelPointInfo> | 订阅的模型关联的点列表                                                                                                 |
| data.subscribeModelPointInfo.modelId   | String                        | 点所属的modelId                                                                                                        |
| data.subscribeModelPointInfo.pointList | List<String>                  | 点的id列表，数据元素为点的id                                                                                           |
| data.subscribePointList                | List<subscribePointInfo>      | 订阅的设备关联的点列表                                                                                                 |
| data.subscribePointList.assetId        | String                        | 点所属的assetId，如果assetId，productKey，deviceKey同时存在，以assetId为准，assetId为空时，以productKey，deviceKey为准 |
| data.subscribePointList.productKey     | String                        | 点所属的productKey                                                                                                     |
| data.subscribePointList.deviceKey      | String                        | 点所属的deviceKey                                                                                                      |
| data.subscribePointList.pointList      | List<String>                  | 点的id列表，数据元素为点的id                                                                                           |

## 示例 1

### 返回示例

```
 {
        "status": 0,
        "msg": "Success",
        "submsg": null,
    "data": {
               "id": "dsfasdfdasfdsaf",
               "subscribeGroupId": "DATASVC.SUB.group1",
               "enable": true,
               "persistent": true,
               "subscribeAll": false,
               "subscribeModelList": ["model1", "model2", "model3"],
               "subscribeProductList": ["product1", "product2", "product3"],
               "subscribeAssetList": ["asset1", "asset2", "asset3"],
               "subscribeDeviceList":[{
                       "productKey": "productKey1",
                       "deviceKey": "deviceKey1"
               },
               {
                       "productKey": "productKey2",
                       "deviceKey": "deviceKey2"

               }],
               "subscribeModelPointList":[{
                       "modelId": "model1",
                       "pointList": ["point1", "point2", "point3"]
               },
               {
                       "modelId": "model2",
                       "pointList": ["point1", "point2", "point3"]
               }],
               "subscribePointList":[{
                       "assetId": "asset10",
                       "productKey": "productKey10",
                       "deviceKey": "deviceKey10",
                       "pointList": ["point1", "point2", "point3"]
               },
               {
                       "assetId": "",
            "productKey": "productKey11",
                       "deviceKey": "deviceKey11",
                       "pointList": ["point1", "point2", "point3"]
               }]
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
