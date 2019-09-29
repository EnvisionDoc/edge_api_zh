# List Subscribe Groups

列出所有订阅组。

## 请求格式

```
GET {apigw-address}/dataService/subscribeGroups?pageSize={}&pageToken={}&orgId={}
```

## 请求参数(URI)

| **名称**  | **数据类型** | **是否必须** | **描述**                         |
|:----------|:-------------|:-------------|:---------------------------------|
| orgId     | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)                  |
| pageSize  | Int          | false        | Page size，默认为0，表示读取所有 |
| pageToken | String       | false        | Page token. 默认为1，表示第一页  |



## 响应参数

| **名称**                                 | **数据类型**                  | **描述**                                                                                                               |
|:-----------------------------------------|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| data                                     | Object                        | Data object                                                                                                            |
| data.pageSize                            | Int                           | Page size                                                                                                              |
| data.totalsize                           | String                        | Total number of returned records                                                                                       |
| data.pageToken                           | String                        | Page token                                                                                                             |
| data.data                                | List<SubscribeGroup>          | Paged list of subscribeGroups                                                                                          |
| data.data.id                             | String                        | 内部使用的id，无须关注                                                                                                 |
| data.data.subscribeGroupId               | String                        | Subscribe group Id                                                                                                     |
| data.data.enable                         | Boolean                       | Whether the subscribe group is enable                                                                                  |
| data.data.persistent                     | Boolean                       | Whether the subscribe group is persistent                                                                              |
| data.data.subscribeAll                   | Boolean                       | Whether the subscribe group subscribes to   all points                                                                 |
| data.data.subscribeModelList             | List<String>                  | 订阅的模型列表，数据元素为modelId                                                                                      |
| data.data.subscribeProductList           | List<String>                  | 订阅的product列表，数据元素为productKey                                                                                |
| data.data.subscribeAssetList             | List<String>                  | 订阅的asset列表，数据元素为assetId                                                                                     |
| data.data.subscribeDeviceList            | List<subscribeDeviceInfo>     | 订阅的device列表                                                                                                       |
| data.data.subscribeDeviceList.productKey | String                        | device的product   key                                                                                                  |
| data.data.subscribeDeviceList.deviceKey  | String                        | device的device key                                                                                                     |
| data.subscribeModelPointList             | List<subscribeModelPointInfo> | 订阅的模型关联的点列表                                                                                                 |
| data.subscribeModelPointInfo.modelId     | String                        | 点所属的modelId                                                                                                        |
| data.subscribeModelPointInfo.pointList   | List<String>                  | 点的id列表，数据元素为点的id                                                                                           |
| data.data.subscribePointList             | List<subscribePointInfo>      | 订阅的点列表                                                                                                           |
| data.data.subscribePointList.assetId     | String                        | 点所属的assetId，如果assetId，productKey，deviceKey同时存在，以assetId为准，assetId为空时，以productKey，deviceKey为准 |
| data.data.subscribePointList.productKey  | String                        | 点所属的productKey                                                                                                     |
| data.data.subscribePointList.deviceKey   | String                        | 点所属的deviceKey                                                                                                      |
| data.data.subscribePointList.pointList   | List<String>                  | 点的id列表，数据元素为点的id                                                                                           |

## 示例 1

### 返回示例

```
{
   "status": 0,
   "msg": "Success",
   "submsg": null,
   "body": null,
   "data": {
      "pageToken": 1,
      "pageSize": 10,
      "totalSize": 22,
      "data": [{
               "id":"dfasdfdsfsadf",
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
          },
          {
               "id":"fdafdsafdsfas",
               "subscribeGroupId": "DATASVC.SUB.group2",
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
