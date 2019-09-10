# List Assets

获取资产列表。

## 请求格式

```
GET /assetService/assets?orgId={}
```

## 请求参数(URI)

| **名称**  | **数据类型** | **是否必须** | **示例值** | **描述**                                                          |
|:----------|:-------------|:-------------|:-----------------|:------------------------------------------------------------------|
| orgId     | String       | true         |                  | 组织ID |
| pageSize  | int          | true         | 5                | 每页记录数|
| pageToken | int          | true         | 1                | 请求页数。若不指定，默认返回第一页|

## 响应参数

| **名称**  | **数据类型** | **描述**             |
|:----------|:-------------|:---------------------|
| data      | Object       | 资产的分页列表 |
| pageToken | Int          | 当前页数 |
| pageSize  | Int          | 每页记录数           |
| totalSize | Int          | Total size           |
| data      | List<Asset>  | 资产列表       |

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
    "totalSize": 53,
    "data": [
      {
        "id": "XNvG2gIH",
        "orgId": "1ad3889266800000",
        "name": {
          "defaultValue": null,
          "i18nValue": {}
        },
        "deviceKey": "xxxx",
        "deviceSecret": "xxx",
        "productKey": "xxx",
        "desc": null,
        "timezone": "+08:00",
        "attributes": {
          "cddddddddd": "lalalla"
        },
        "modelId": "yj_sub2",
        "tags": {}
      },
      {
        "id": "oH9tnHlu",
        "orgId": "1ad3889266800000",
        "name": {
          "defaultValue": null,
          "i18nValue": {}
        },
        "deviceKey": "xxxx",
        "deviceSecret": "xxx",
        "productKey": "xxx",
        "desc": null,
        "timezone": "Asia/Tokyo",
        "attributes": {
          "capacity": null
        },
        "modelId": "INVETER_TEST",
        "tags": {}
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
        "submsg": null
}
```
