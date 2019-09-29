# Get Thing Model

获取单个模型详情。

## 请求格式

```
GET {apigw-address}/modelService/thingModels/{thingModelId}?orgId={}
```

## 请求参数

| **名称**     | **数据类型** | **是否必须** | **描述**        |
|:-------------|:-------------|:-------------|:----------------|
| orgId        | String       | true         | 资产所属的组织ID。[如何获取orgId信息>>](/docs/api/zh_CN/2.0.9/api_faqs#id-orgid-orgid) |
| thingModelId | String       | true         | 物模型ID  |


## 响应参数

| **名称**     | **数据类型**        | **描述**                                                                                      |
|:-------------|:--------------------|:----------------------------------------------------------------------------------------------|
| data         | ThingModel          | 物模型详情                                                                           |
| id           | String              | 物模型ID                                                                                |
| orgId        | String              | 模型所属的组织ID                                               |
| name         | Object              | 物模型的各种语言名称|
| defaultValue | String              | 默认名称                                                                          |
| i18nValue    | Map<String, String> | 国际化名称列表。语言环境与语言成对对应，如`"zh_CN": "Chinese name"`                                |
| en_US        | String              | 英文名称                                                                                 |
| zh_CN        | String              | 中文名称                                                                              |
| desc         | String              | 物模型描述                                                                       |
| category     | String              | 物模型类别                                                                       |
| jsonschema   | String              | 物模型的完整描述，是一个json schema                                           |
| parentId     | String              | 父模型ID。<br> 若值为空，则该物模型不是继承模型               |
| copyFromId   | String              | 复制模型ID。<br> 若值为空，则该模型不是由其它模型复制而来 |
| tags         | Map<String, String> | 用户对物模型的自定义标签                                                      |

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
