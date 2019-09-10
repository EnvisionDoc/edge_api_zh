# Delete Set Measurepoint Channel

删除写值通道。


## 请求格式

```
DELETE /dataService/setMeasurepointChannels/{setMeasurepointChannelId}?orgId={}
```

## 请求参数(URI)



| **名称**                 | **数据类型** | **是否必须** | **描述**        |
|:-------------------------|:-------------|:-------------|:----------------|
| orgId                    | String       | true         | Organization ID |
| setMeasurepointChannelId | String       | true         | 写值通道Id      |



## 请求参数(Body)



| **名称** | **数据类型** | **是否必须** | **描述** |
|:---------|:-------------|:-------------|:---------|
|          |              |              |          |



## 响应参数

| **名称** | **数据类型** | **描述** |
|:---------|:-------------|:---------|
|          |              |          |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": null
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
