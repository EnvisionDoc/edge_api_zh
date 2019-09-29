# Get Product

获取产品。

## 请求格式

```
GET {apigw-address}/connectService/products/{productKey}?orgId={}
```

## 请求参数

| **名称**   | **数据类型** | **是否必须** | **描述**        |
|:-----------|:-------------|:-------------|:----------------|
| orgId      | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid)|
| productKey | String       | true         | Product key标识符     |

## 响应参数

| **名称**      | **数据类型**       | **描述**            |
|:--------------|:-------------------|:--------------------|
| data          | Product            | 产品信息|
| productId     | String             | 产品ID          |
| productKey    | String             | Product Key标识符        |
| name          | String             | 产品名称     |
| productSecret | String             | Product Secret标识符     |
| productDesc   | String             | 产品描述|
| dataType      | String             | 数据类型         |
| nodeType      | String             | 节点类型        |
| productTags   | Map<String,String> | 产品标签      |
| modelId       | String             | 模型ID          |
| dynamic       | String             | Dynamic             |

## 示例 1

### 返回示例

```
 {
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
            "productId": "Db39paeA",
               "productKey": "eb27piAg",
               "productName": "XXX",
               "productSecret": "sEs7nQvugaslWk6b9eig",
               "productDesc": "XXX",
            "dataType": 1,
            "nodeType": 1,
            "productTags": {},
            "modelId": "oiu9u3D0c",
            "dynamic": false
        }
}
```
