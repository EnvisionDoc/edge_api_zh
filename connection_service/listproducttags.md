# List Product Tags

获取产品标签列表。

## 请求格式

```
GET /connectService/product/{productKey}/tags?orgId={}
```

## 请求参数

| **名称**   | **数据类型** | **是否必须** | **描述**          |
|:-----------|:-------------|:-------------|:------------------|
| orgId      | String       | true         | 组织ID            |
| productKey | String       | true         | Product key标识符 |


## 响应参数

| **名称** | **数据类型**       | **描述**             |
|:---------|:-------------------|:---------------------|
| data     | Map<String,String> | List of product keys |
| tagKey   | String             | Tag key              |

## 示例 1

### 返回示例

```
 {
        "status": 0,
        "msg": "Success",
        "submsg": null,
        "data": {
            "key1": "value1",
            "key2": "value2",
            "key3": "value3"
        }
}
```
