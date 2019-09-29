# Get Domain Point Mapping

获取领域点映射关系。

## 请求格式

```
GET {apigw-address}/mdmService/getDomainPointMapping?orgId={}&mdmids={}&points={}
```

## 请求参数

| **名称** | **数据类型** | **是否必须** | **描述**|
|:---------|:-------------|:-------------|:--------------------|
| orgId    | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)  |
| mdmids   | String       | true         | 资产ID列表，逗号分隔，如assetId1,assetId2,assetId3，或者productKey1@@deviceKey1,productKey2@@deviceKey2,productKey3@@deviceKey3这种形式 |
| points   | String       | true         | 领域点列表，逗号分隔，为空时表示获取所有领域点的映射类型|


## 响应参数

| **名称** | **数据类型**        | **描述**|
|:---------|:--------------------|:------------------------------------------------------|
| status   | Integer             | 状态码。0:正常|
| msg      | String              | 状态码说明|
| data     | Map<String, String> | 返回结果。数值的含义如下：<br>·    -1 INVALID  <br>·  0 NO_MAPPING  <br>·  1 EQUAL  <br>·  2 CONTROL_SET  <br>·  3 RATIO_AGAINST_SUM  <br>·  4 SUM  <br>·  5 RATIO  <br>·  6 LOGICAL_OR  <br>·  7 MULTICHANNEL  <br>·  8 MULTIBIT  <br>·  9 BIT_N   <br>· 10 IF_EQUAL |

## 示例 1

### 返回示例

```json
{
​    "status": 0,
​    "msg": "Success",
​    "submsg": null,
​    "data": {
​        "assetId1": {
​            "CBX.STATUS002": 1,
​            "CBX.STATUS008": 1,
​            "CBX.STATUS009": 1
​        },
​        "assetId2": {
​            "CBX.STATUS002": 1,
​            "CBX.STATUS008": 1,
​            "CBX.STATUS009": 1
​        }
​    }
}
```

或者

```
{
​    "status": 0,
​    "msg": "Success",
​    "submsg": null,
​    "data": {
​        "productKey1@@deviceKey1": {
​            "CBX.STATUS002": 1,
​            "CBX.STATUS008": 1,
​            "CBX.STATUS009": 1
​        },
​        "productKey2@@deviceKey2": {
​            "CBX.STATUS002": 1,
​            "CBX.STATUS008": 1,
​            "CBX.STATUS009": 1
​        }
​    }
}
```

### 异常示例

```
{
​    "status": 400,
​    "msg": "Invalid Argument orgId",
​    "submsg": "orgId does not exist"
}
```
