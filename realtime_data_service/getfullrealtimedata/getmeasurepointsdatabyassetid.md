# Get Measurepoints Data By Asset Id

获取单个设备的模型点实时数据。

## 请求格式

```
GET /dataService/devices/{assetId}/measurepoints/latestData?orgId={}
```

## 请求参数(URI)

| **名称** | **数据类型** | **是否必须** | **描述**               |
|:---------|:-------------|:-------------|:-----------------------|
| orgId    | String       | true         | Organization ID        |
| assetId  | String       | true         | Asset ID of the device |


## 响应参数

| **名称**         | **数据类型**       | **描述**                                                                                                                           |
|:-----------------|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------|
| data             | List<Measurepoint> | List of latest measurepoint data                                                                                                   |
| data.pointId     | String             | Measurepoint ID                                                                                                                    |
| data.dataType    | String             | Measurepoint type, including ARRAY, BOOL,   DATE, ENUM, INT, FLOAT, DOUBLE, STRUCT, TEXT, NUMBER, TIMESTAMP, FILE, MAP   and so on |
| data.subDataType | String             | data.dataType为ARRAY时，此字段有效，表示数组中数据的子类型，可能取值为INT, FLOAT, DOUBLE,TEXT                                      |
| data.time        | Long               | UTC timestamp (millisecond)                                                                                                        |
| data.value       | String             | Measurepoint value                                                                                                                 |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": [
        {
               "pointId": "point1",
               "dataType": "INT",
               "subDataType": null,
               "time": 1536667537046,
               "value": 88
        },
        {
               "pointId": "point2",
               "dataType": "ARRAY",
               "subDataType": "INT",
               "time": 1536667537046,
               "value": [11,22,33]
        }

        ]
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
