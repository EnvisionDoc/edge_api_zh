# Update Control Channel

## 请求格式

```
PUT {apigw-address}/dataService/controlChannels/{controlChannelId}?orgId={}
{
        "controlChannelId": "DATASVC.CONTROL.aaa",
        "desc":"aaaaaaa"
}
```

## 请求参数(URI)

| **名称**         | **数据类型** | **是否必须** | **描述**           |
|:-----------------|:-------------|:-------------|:-------------------|
| orgId            | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)  |
| controlChannelId | String       | true         | control channel Id |

## 请求参数(Body)


| **名称**         | **数据类型** | **是否必须** | **描述**                |
|:-----------------|:-------------|:-------------|:------------------------|
| controlChannelId | String       | false        | control channel Id      |
| desc             | String       | false        | desc of control channel |


## 响应参数

| **名称**              | **数据类型** | **描述**                |
|:----------------------|:-------------|:------------------------|
| data                  |              |                         |
| data.controlChannelId | String       | control channel Id      |
| data.desc             | String       | desc of control channel |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
               "controlChannelId":"DATASVC.CONTROL.aaa",
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
