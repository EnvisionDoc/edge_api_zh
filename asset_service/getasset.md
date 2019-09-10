# Get Asset

获取资产详情。

## 请求格式

```
GET /assetService/assets/{assetId}?orgId={}
```

## 请求参数(URI)

| **名称** | **数据类型** | **是否必须** | **描述**        |
|:---------|:-------------|:-------------|:----------------|
| orgId    | String       | true         | 组织ID |
| assetId  | String       | true         | 资产ID        |

## 响应参数

| **名称**     | **数据类型**        | **描述**                                                                                                                                                                                            |
|:-------------|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| data         | Asset               | 资产详细信息|
| id           | String              | 资产ID|
| orgId        | String              | 资产所属的组织ID |
| name         | Object              | 该资产的各语言名称|
| deviceKey    | String              | Device Key标识符|
| deviceSecret | String              | Device Secret标识符|
| prodcutKey   | String              | Prodcut Key标识符|
| i18nValue    | Map<String, String> | 国际化名称列表。语言环境与语言成对对应，如`"zh_CN": "Chinese name"`|
| en_US        | String              | 英文名称|
| zh_CN        | String              | 中文名称|
| desc         | String              | 资产描述|
| timezone     | String              | 资产所属时区。支持的格式有：<br> 1). '地区/城市'格式，如“Asia/Tokyo”； <br>2). 资产所属时区与格林尼治（UTC）时间的差值，如“+08:00” |
| attributes   | Map<Key为String，Value为Object>  | 资产属性|
| modelId      | String              | 资产所属模型ID|
| tags         | Map<String, String> | 用户自定义标签|

.. note:: 红色字段是Edge接口比云端接口多出的字段方便业务方使用。

## 示例 1

#### 返回示例

```
{
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
          "id": "Instance_cshan_001",
          "orgId": "1ad3889266800000",
          "deviceKey": "xxxx",
          "deviceSecret": "xxx",
          "productKey": "xxx",
          "name": {
            "defaultValue": "daniu",
            "i18nValue": {}
          },
          "desc": "hahdesc",
          "timezone": "+08:00",
          "attributes": {},
          "modelId": "cshan111602",
          "tags": {
            "year": "2000",
            "author": "cshan"
          }
        }
}
```

#### 异常示例

```
{
    "status": 400,
    "msg": "Invalid Argument orgId",
    "submsg": "orgId does not exist"
}
{
    "status": 404,
    "msg": "invalid Id",
    "submsg": "orgId not exists"
}
```
