# Update Set Measurepoint Channel

更新写值通道。

## 请求格式

```
PUT /dataService/setMeasurepointChannels/{setMeasurepointChannelId}?orgId={}
{
        "setMeasurepointChannelId": "DATASVC.SET.aaa",
        "desc":"aaaaaaa"
}
```

## 请求参数(URI)

| **名称**                 | **数据类型** | **是否必须** | **描述**                   |
|:-------------------------|:-------------|:-------------|:---------------------------|
| orgId                    | String       | true         | Organization ID            |
| setMeasurepointChannelId | String       | true         | setMeasurepoint channel Id |



## 请求参数(Body)

| **名称**                 | **数据类型** | **是否必须** | **描述**                   |
|:-------------------------|:-------------|:-------------|:---------------------------|
| setMeasurepointChannelId | String       | false        | setMeasurepoint channel Id |
| desc                     | String       | false        | desc of control channel    |



## 响应参数

| **名称**                      | **数据类型** | **描述**                        |
|:------------------------------|:-------------|:--------------------------------|
| data                          |              |                                 |
| data.setMeasurepointChannelId | String       | setMeasurepoint channel Id      |
| data.desc                     | String       | desc of setMeasurepoint channel |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
               "setMeasurepointChannelId":"DATASVC.SET.aaa",
               "desc": "aaaaaa"
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