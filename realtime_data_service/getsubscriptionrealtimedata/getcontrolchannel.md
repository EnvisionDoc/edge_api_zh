# Get Control Channel

获取控制通道详情。

## 请求格式

```
GET {apigw-address}/dataService/controlChannels/{controlChannelId}?orgId={}
```

## 请求参数(URI)

| **名称**         | **数据类型** | **是否必须** | **描述**        |
|:-----------------|:-------------|:-------------|:----------------|
| orgId            | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid) |
| controlChannelId | String       | true         | 控制通道Id      |



## 请求参数(Body)

| **名称** | **数据类型** | **是否必须** | **描述** |
|:---------|:-------------|:-------------|:---------|
|          |              |              |          |



## 响应参数

| **名称**              | **数据类型** | **描述**               |
|:----------------------|:-------------|:-----------------------|
| data                  |              |                        |
| data.id               | String       | 内部使用的id，无须关注 |
| data.controlChannelId | String       | controlChannelId       |
| data.desc             | String       | 描述                   |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
    "data": {
               "id": "dsfasdfdasfdsaf",
               "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
               "desc":"desc"
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
