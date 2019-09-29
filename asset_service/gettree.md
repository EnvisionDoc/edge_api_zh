# Get Tree

获取资产树详情。

## 请求格式

```
GET {apigw-address}/assetService/assetTrees/{assetTreeId}?orgId={}
```

## 请求参数(URI)

| **名称**    | **数据类型** | **是否必须** | **描述**        |
|:------------|:-------------|:-------------|:----------------|
| orgId       | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)  |
| assetTreeId | String       | true         | 资产树ID   |



## 响应参数

| **名称**     | **数据类型**  | **描述**                        |
|:-------------|:--------------|:--------------------------------|
| data         | Tree          | 资产树详细信息 |
| id           | String        | 资产树ID                   |
| rootNodeId   | String        | 资产树根节点ID         |
| rootNodeName | TSLStringI18n | 资产树根节点名称       |
| createBy     | String        | 创建人  |
| createTime   | String        | 创建时间           |

## 示例 1

### 返回示例

```
 {
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {"id":"xxx",
        "rootNodeId":"xxx",
        "rootNodeName":"xxx",
        "createBy":"xxx",
        "createTime":"xxx"

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
    "status": 1710003,
    "msg": "invalid treeId",
    "submsg": "invalid treeId "+treeId
}

```
