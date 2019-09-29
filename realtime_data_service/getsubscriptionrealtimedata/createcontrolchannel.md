# Create Control Channel

控制通道controlChannelId的值必须以DATASVC.CONTROL.开头

控制通道controlChannelId的值只能为大小写英文字母、数字、下划线、点、中横线的一种或多种的组合，长度最大为64字节。

## 请求格式

```
 POST {apigw-address}/dataService/controlChannels?orgId={}
{
        "controlChannelId": "DATASVC.CONTROL.controlChannelId1",
        "desc":"desc"
}
```



## 请求参数(URI)

| **名称** | **数据类型** | **是否必须** | **描述**        |
|:---------|:-------------|:-------------|:----------------|
| orgId    | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid) |


## 请求参数(Body)

| **名称**         | **数据类型** | **是否必须** | **描述**                                                         |
|:-----------------|:-------------|:-------------|:-----------------------------------------------------------------|
| controlChannelId | String       | true         | controlChannelId，应用指定，不能重复，用于接收异步控制的返回消息 |
| desc             | String       | false        | 描述                                                             |



## 响应参数

| **名称**              | **数据类型** | **描述**               |
|:----------------------|:-------------|:-----------------------|
| data                  |              |                        |
| data.id               | String       | 内部使用的id，无须关注 |
| data.controlChannelId | String       | controlChannelId       |

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
