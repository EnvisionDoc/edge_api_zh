# List Thing Models

获取模型列表。

## 请求格式

```
GET /modelService/thingModels?orgId={}&pageSize={}&pageToken={}&scope={}
```

## 请求参数

| **名称**  | **数据类型** | **是否必须** | **示例值** | **描述**                                                                                                                                                                                                                                          |
|:----------|:-------------|:-------------|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| orgId     | String       | true         |                  | Organization ID                                                                                                                                                                                                                                   |
| scope     | Integer      | false        | 0                | Query scope. <br>·  0: Query private models in   the specified orgId only; <br>·  1: Query private models in the specified orgId and   public models of the platform; <br>·  2: Query public models of the platform only.   <br>The default is 0. |
| pageSize  | Integer      | true         | 5                | Page size                                                                                                                                                                                                                                         |
| pageToken | Integer      | true         | 1                | Page token of the current page                                                                                                                                                                                                                    |



## 响应参数

| **名称**   | **数据类型**        | **描述**                                                                                 |
|:-----------|:--------------------|:-----------------------------------------------------------------------------------------|
| data       | Object              | Paged list of thing models                                                               |
| pageToken  | Integer             | Current page number                                                                      |
| pageSize   | Integer             | Page size                                                                                |
| totalSize  | Integer             | Total size                                                                               |
| data       | List<ThingModel>    | List of thing models                                                                     |
| id         | String              | Thing model ID                                                                           |
| orgId      | String              | Organization to which the thing model   belongs                                          |
| name       | Object              | International name of the thing model                                                    |
| desc       | String              | Thing model description                                                                  |
| category   | String              | Thing model category                                                                     |
| jsonschema | String              | Complete definition of thing model, a   json schema                                      |
| parentId   | String              | Parent model ID. If the value is null,   the thing model is not inherited.               |
| copyFromId | String              | Copy model ID. If the value is null, the   thing model is not copied from another model. |
| tags       | Map<String, String> | Tags created by users on the thing model                                                 |

## 示例 1

### 返回示例

```
 {
  "status": 0,
  "msg": "Success",
  "submsg": null,
  "data": {
    "page": 1,
    "pageSize": 5,
    "totalSize": 2,
    "data": [
      {
        "id": "cshan111603",
        "orgId": "1ad3889266800000",
        "name": {
          "defaultValue": "cshan111603",
          "i18nValue": {
            "en_US": ""
          }
        },
        "desc": "dfdfdf",
        "category": "",
        "jsonschema": "{\"id\":\"\",\"type\":\"object\",\"properties\":{\"measurepoints\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"attributes\":{\"id\":\"\",\"type\":\"object\",\"properties\":{\"int111\":{\"title\":\"{\\\"default\\\":\\\"int111\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"unit\\\":\\\"\\\",\\\"unit_multiplier\\\":\\\"ONE\\\",\\\"actualdesc\\\":\\\"\\\",\\\"numbertype\\\":\\\"INT\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"int111\",\"default\":111,\"type\":\"integer\",\"minimum\":-2147483648,\"maximum\":2147483647},\"str222\":{\"title\":\"{\\\"default\\\":\\\"str222\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"actualdesc\\\":\\\"\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"str222\",\"default\":\"222\",\"type\":\"string\",\"maxLength\":1024},\"float333\":{\"title\":\"{\\\"default\\\":\\\"float333\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"unit\\\":\\\"\\\",\\\"unit_multiplier\\\":\\\"ONE\\\",\\\"actualdesc\\\":\\\"\\\",\\\"numbertype\\\":\\\"FLOAT\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"float333\",\"default\":33.3,\"type\":\"number\",\"minimum\":-3.4028235E38,\"maximum\":3.4028235E38}},\"required\":[\"str222\"],\"additionalProperties\":false},\"services\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"events\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false}},\"required\":[\"attributes\"],\"additionalProperties\":false}",
        "parentId": null,
        "copyFromId": "cshan111602",
        "tags": {
          "year": "1990",
          "author": "cshan"
        }
      },
      {
        "id": "cshan111602",
        "orgId": "1ad3889266800000",
        "name": {
          "defaultValue": "cshan111602",
          "i18nValue": {
            "en_US": ""
          }
        },
        "desc": "aa",
        "category": "",
        "jsonschema": "{\"id\":\"\",\"type\":\"object\",\"properties\":{\"measurepoints\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"attributes\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"services\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"events\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false}},\"required\":[\"attributes\"],\"additionalProperties\":false}",
        "parentId": null,
        "copyFromId": null,
        "tags": {
          "author": "cshan"
        }
      }
    ]
  }
}
```

.. note:: 模型中带质量位的测点 type 是 object  ；signaltype 需要从 properties.value.decription 中取

![](../media/properties_value_decriotion.png)

### 异常示例

```
{
    "status": 400,
    "msg": "Invalid Argument orgId",
    "submsg": "orgId does not exist"
}
```
