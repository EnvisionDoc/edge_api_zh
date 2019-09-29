# Delete Subscribe Group

删除订阅组。

## 请求格式

```
DELETE {apigw-address}/dataService/subscribeGroups/{subscribeGroupId}?orgId={}
```

## 请求参数(URI)

| **名称**         | **数据类型** | **是否必须** | **描述**           |
|:-----------------|:-------------|:-------------|:-------------------|
| orgId            | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)    |
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
