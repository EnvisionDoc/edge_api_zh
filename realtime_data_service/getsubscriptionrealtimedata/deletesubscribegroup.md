# Delete Subscribe Group

删除订阅组。

## 请求格式

```
DELETE /dataService/subscribeGroups/{subscribeGroupId}?orgId={}
```

## 请求参数(URI)

| **名称**         | **数据类型** | **是否必须** | **描述**           |
|:-----------------|:-------------|:-------------|:-------------------|
| orgId            | String       | true         | Organization ID    |
| subscribeGroupId | String       | true         | Subscribe group Id |



## 响应参数

空

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
