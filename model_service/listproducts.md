# List Products

获取产品列表。

## 请求格式

```
GET /connectService/products?pageSize={}&pageToken={}&orgId={}
```

## 请求参数

| **名称**  | **数据类型** | **是否必须** | **描述**                                                              |
|:----------|:-------------|:-------------|:----------------------------------------------------------------------|
| orgId     | String       | true         | Organization ID                                                       |
| pageSize  | Int          | false        | Page size                                                             |
| pageToken | String       | false        | Page token. <br>If not specified, return the   first page by default. |

## 响应参数

| **名称**      | **数据类型**       | **描述**                         |
|:--------------|:-------------------|:---------------------------------|
| data          | Object             | Data object                      |
| pageSize      | Int                | Page size                        |
| totalsize     | String             | Total number of returned records |
| pageToken     | String             | Page token                       |
| data          | List<Product>      | Paged list of products           |
| productId     | String             | Product ID                       |
| productKey    | String             | Product Key                      |
| name          | String             | Product name                     |
| productSecret | String             | Product Secret                   |
| productDesc   | String             | Product description              |
| dataType      | String             | Data type                        |
| nodeType      | String             | Node type                        |
| productTags   | Map<String,String> | Product tags                     |
| modelId       | String             | Model ID                         |
| dynamic       | String             | Dynamic                          |

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
      "data": [
         {
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
```
