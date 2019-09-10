# Search Nodes

根据资产ID和模型ID搜索相应的节点信息。

## 请求URL

```
GET /assetService/assetTrees/{assetTreeId}/nodes?orgId={}&searchKey={}&searchValue={}&pageToken={}&pageSize={}

```

## 请求参数（URI）

| **名称**    | **数据类型** | **是否必须** | **描述**                       |
|:------------|:-------------|:-------------|:-------------------------------|
| orgId       | String       | true         | 设备所属的组织ID               |
| assetTreeId | String       | true         | 资产树ID                       |
| searchKey   | String       | true         | 搜素类别，可填assetId或modelId |
| searchValue | String       | true         | 资产ID值或模型ID值       |
| pageToken   | String       | true         | 当前页码                       |
| pageSize    | int          | true         | 每页记录数                       |



## 响应参数

| **名称** | **数据类型** | **描述**           |
|:---------|:-------------|:-------------------|
| nodeInfo | NodeInfo     | 节点详情           |
| node     | Node         | 当前节点的信息     |
| path     | List<Node>   | 当前节点的祖先节点 |

## 示例 1

### 返回示例

```
{
        "status": 0,
        "requestId": "fe759eda1015432fba1f26ed48faac56",
        "msg": "Success",
        "submsg": null,
        "data": [{ "id":"",
                "modelId":"",
                "instanceId":"",
                "name":"",
                "treeId":"",
                "isDeviceInstance":"",
                "hasChild":"",
                "extraInfo":{
                    "createBy":"",
                    "createTime":"",
                    "updateBy":"",
                    "updateTime":""
                }
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
