# List Child Nodes

获取子节点列表。

## 请求格式

```
GET /assetService/assetTrees/{assetTreeId}/nodes/{nodeId}/childNodes?orgId={}&nodeId={}&pageToken={}&pageSize={}
```

## 请求参数(URI)

| **名称**    | **数据类型** | **是否必须** | **描述**                                          |
|:------------|:-------------|:-------------|:--------------------------------------------------|
| orgId       | String       | true         | 组织ID                                   |
| assetTreeId | String       | true         | 资产树ID                                     |
| nodeId      | String       | true         | 节点ID                                           |
| pageToken   | String       | false        | 从此节点开始返回节点信息 |
| pageSize    | Int          | true         | 每页记录数  |



## 响应参数

| **名称** | **数据类型** | **描述**                       |
|:---------|:-------------|:-------------------------------|
| data     | Object       | 节点信息的分页列表 |


## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
            "pageToken": 1,
            "pageSize": 5,
            "nextPageToken": 2,
            "data": [{ "id":"",
                "modelId":"",
                "instanceId":"",
                "name":"",
                "treeId":"",
                "parentId":"",
                "isDeviceInstance":,
                "hasChild":,
                "extraInfo":{
                    "createBy":"",
                    "createTime":"",
                    "updateBy":"",
                    "updateTime":""
                }
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
