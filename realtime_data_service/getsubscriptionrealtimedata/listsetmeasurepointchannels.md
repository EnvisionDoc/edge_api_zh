# List Set Measurepoint Channels

列出所有写值通道。


## 请求格式

```
GET /dataService/setMeasurepointChannels?pageSize={}&pageToken={}&orgId={}
```

## 请求参数(URI)



| **名称**  | **数据类型** | **是否必须** | **描述**                         |
|:----------|:-------------|:-------------|:---------------------------------|
| orgId     | String       | true         | Organization ID                  |
| pageSize  | Int          | false        | Page size，默认为0，表示读取所有 |
| pageToken | String       | false        | Page token. 默认为1，表示第一页  |



## 请求参数(Body)



| **名称** | **数据类型** | **是否必须** | **描述** |
|:---------|:-------------|:-------------|:---------|
|          |              |              |          |



## 响应参数

| **名称**                           | **数据类型**         | **描述**                         |
|:-----------------------------------|:---------------------|:---------------------------------|
| data                               | Object               | Data object                      |
| data.pageSize                      | Int                  | Page size                        |
| data.totalsize                     | String               | Total number of returned records |
| data.pageToken                     | String               | Page token                       |
| data.data                          | List<SubscribeGroup> | Paged list of subscribeGroups    |
| data.data.id                       | String               | 内部使用的id，无须关注           |
| data.data.setMeasurepointChannelId | String               | 写值通道id                       |
| data.data.desc                     | String               | 描述                             |

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
               "setMeasurepointChannelId": "DATASVC.SET.setMeasurepointChannelId1",
               "desc":desc

          },
      {
               "id":"fdafdsafdsfas",
               "setMeasurepointChannelId": "DATASVC.SET.setMeasurepointChannelId1",
               "desc":desc
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
