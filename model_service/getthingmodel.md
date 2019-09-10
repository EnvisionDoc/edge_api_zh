# Get Thing Model

获取单个模型详情。

## 请求格式

```
GET /modelService/thingModels/{thingModelId}?orgId={}
```

## 请求参数

| **名称**     | **数据类型** | **是否必须** | **描述**        |
|:-------------|:-------------|:-------------|:----------------|
| orgId        | String       | true         | Organization ID |
| thingModelId | String       | true         | Thing Model ID  |


## 响应参数

| **名称**     | **数据类型**        | **描述**                                                                                      |
|:-------------|:--------------------|:----------------------------------------------------------------------------------------------|
| data         | ThingModel          | Thing model details                                                                           |
| id           | String              | Thing model ID                                                                                |
| orgId        | String              | Organization to which the thing model   belongs                                               |
| name         | Object              | International name of the thing model                                                         |
| defaultValue | String              | Default name                                                                                  |
| i18nValue    | Map<String, String> | List of international names, pairs of   locales and names                                     |
| en_US        | String              | English name                                                                                  |
| zh_CN        | String              | Chinese name                                                                                  |
| desc         | String              | Thing model description                                                                       |
| category     | String              | Thing model category                                                                          |
| jsonschema   | String              | Complete definition of thing model, a   json schema                                           |
| parentId     | String              | Parent model ID. <br> If the value is null,   the thing model is not inherited.               |
| copyFromId   | String              | Copy model ID. <br> If the value is null, the   thing model is not copied from another model. |
| tags         | Map<String, String> | Tags created by users on the thing model                                                      |

## 示例 1

### 返回示例

```
{
​        "status": 0,
​        "msg": "Success",
​        "data": {
​          "id": "cshan111603",
​          "orgId": "1ad3889266800000",
​          "name": {
​            "defaultValue": "cshan111603",
​            "i18nValue": {
​              "en_US": ""
​            }
​          },
​          "desc": "dfdfdf",
​          "category": "",
​          "jsonschema": "{\"id\":\"\",\"type\":\"object\",\"properties\":{\"measurepoints\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"attributes\":{\"id\":\"\",\"type\":\"object\",\"properties\":{\"int111\":{\"title\":\"{\\\"default\\\":\\\"int111\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"unit\\\":\\\"\\\",\\\"unit_multiplier\\\":\\\"ONE\\\",\\\"actualdesc\\\":\\\"\\\",\\\"numbertype\\\":\\\"INT\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"int111\",\"default\":111,\"type\":\"integer\",\"minimum\":-2147483648,\"maximum\":2147483647},\"str222\":{\"title\":\"{\\\"default\\\":\\\"str222\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"actualdesc\\\":\\\"\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"str222\",\"default\":\"222\",\"type\":\"string\",\"maxLength\":1024},\"float333\":{\"title\":\"{\\\"default\\\":\\\"float333\\\",\\\"en_US\\\":\\\"\\\"}\",\"description\":\"{\\\"unit\\\":\\\"\\\",\\\"unit_multiplier\\\":\\\"ONE\\\",\\\"actualdesc\\\":\\\"\\\",\\\"numbertype\\\":\\\"FLOAT\\\",\\\"accessmode\\\":true,\\\"tags\\\":{}}\",\"id\":\"float333\",\"default\":33.3,\"type\":\"number\",\"minimum\":-3.4028235E38,\"maximum\":3.4028235E38}},\"required\":[\"str222\"],\"additionalProperties\":false},\"services\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false},\"events\":{\"id\":\"\",\"type\":\"object\",\"additionalProperties\":false}},\"required\":[\"attributes\"],\"additionalProperties\":false}",
​          "parentId": null,
​          "copyFromId": "cshan111602",
​          "tags": {
​            "year": "2000",
​            "author": "cshan"
​          }
​        }
}
```


### 异常示例

```
{
​    "status": 400,
​    "msg": "Invalid Argument orgId",
​    "submsg": "orgId not exists"
}
```
