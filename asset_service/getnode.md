# Get Node

获取节点详情。

## 请求格式

```
GET {apigw-address}/assetService/assetTrees/{assetTreeId}/nodes/{nodeId}?orgId={}
```

## 请求参数(URI)

| **名称**    | **数据类型** | **是否必须** | **描述**        |
|:------------|:-------------|:-------------|:----------------|
| orgId       | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)  |
| assetTreeId | String       | true         | 资产树ID   |
| nodeId      | String       | true         | 节点ID         |



## 响应参数

| **名称**            | **数据类型** | **描述**                   |
|:--------------------|:-------------|:---------------------------|
| nodeInfo            | NodeInfo     | 节点详细信息  |
| node                | Node         | 当前节点信息  |
| path                | List<Node>   | 当前节点的祖先节点   |
| id                  | String       | 节点ID                     |
| name                | String       | 节点名称                       |
| modelId          | String       | 模型ID                 |
| instanceId       | String       | 绑定在节点上的资产的ID |
| treeId           | String       |资产树ID                     |
| isDeviceInstance | Boolean      | 绑定deviceInstance  |
| hasChild            | Boolean      | 有子节点                   |
| extraInfo           | Obejct       |其它信息|


## 示例 1

### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
            "node":{"id":"",
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
            },
           "path":[{ "id":"",
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
            }
                ]
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
{
    "status": 1710002,
    "msg": "invalid nodeId",
    "submsg": "invalid "+nodeId
}
```
