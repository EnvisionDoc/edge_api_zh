# 有关Edge API

<!--描述-->


## API列表

- [通用服务](docs/edge-api/zh_CN/2.0.9/common_service/overview.html)：
- [接入服务](/docs/edge-api/zh_CN/2.0.9/connection_service/overview.html)：
- [模型服务](/docs/edge-api/zh_CN/2.0.9/model_service/overview.html)：
- [资产服务](/docs/edge-api/zh_CN/2.0.9/asset_service/overview.html)：
- [实时数据服务](/docs/edge-api/zh_CN/2.0.9/realtime_data_service/overview.html)：


## API Request结构

EnOS API请求包含以下组成部分：

### Request URI

```
{URI-scheme}://{apigw-address}/{Request-URL}?{query-param=value}
```

其中：

- URI-sheme：协议，支持HTTP协议。
- apigw-address：该Edge环境API服务的IP地址。
- Request-URL：服务和资源，如assetService/assets/abcd。
- query-param：对目标资源的选择条件，如orgId=1234。当有多个query参数时，用&符号连接。

以获取某OU内某个资产信息为例，API请求格式如下：

```
GET
http://{apigw-address}/assetService/assets/abcd?orgId=1234
```

### Request Header

Request URI的REST API规范和HTTP规范所需的任何其他字段，绑定在request header中。

常用的request header为`Content-Type`，代表数据提交方式，一般情况下它的值可设为 `application/json;charset=UTF-8`；若执行文件上传或其他表单提交，值设为`multipart/form-data;charset=UTF-8`。

### Request Body

用于补充Request URI以提供更加复杂的输入参数，如以下示例request body中包含的参数指定了更新资产的时区、描述、标签等属性：

```
POST
http://{apigw-address}/dataService/devices/123/measurepoints/measurepoint1/set?orgId=1234&requestId=USCADA1
{
  "arg":10
}
```

## API Response结构

Edge API的返回为以下格式的JSON结构体：

```json
{
  "status": 0,
  "msg": "OK",
  "submsg": "OK",
  "data": {
  }
}
```


对返回参数的详细说明如下：

| **名称** | **数据类型**    | **是否必须** | **描述**                                                                                          |
|:---------|:----------------|:-------------|:--------------------------------------------------------------------------------------------------|
| code     | Integer         | true         | API请求状态码，0表示请求成功。<br> 其它状态码的含义，参考公共返回码和API文档中的错误码解释。<br/> |
| msg      | String          | true         | 对状态码的解释和说明。<br>成功为“OK”。<br>若API请求失败，返回具体错误信息。                       |
| submsg   | String          | true         | 更加具体的错误信息。                                                                              |
| data     | Array 或 Object | false        | API响应返回结果集，数据类型包括：基本数据类型、复杂类型或数组。详见每个API的文档。                |
