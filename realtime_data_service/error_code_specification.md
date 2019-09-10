# Error Code Specification

| **错误代码** | **错误信息**                                               | **说明**                                                                                                                   |
|:-------------|:-----------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| 400          | invalid argument orgId                                     | ordId不存在                                                                                                                |
| 404          | Invalid object id                                          | 数据id不存在                                                                                                               |
| 1000         | para error                                                 | 各种情况的输入参数错误                                                                                                     |
| 1002         | get datastore error                                        | 获取操作配置数据库的类失败                                                                                                 |
| 1003         | get bull client error                                      | 获取操作redis的类失败                                                                                                      |
| 1004         | data type error                                            | 数据类型错误，比如写值时模型点类型为Double，而传入参数类型为String                                                         |
| 1000001      | subscribe group already exists                             | 订阅通道已经存在，不能重复创建                                                                                             |
| 1000002      | subscribe group id is illegal                              | 订阅通道名字不合法，一般是订阅通道名字不符合格式要求                                                                       |
| 1000003      | subscribe group does not exist                             | 订阅通道不存在，不能获取相关信息                                                                                           |
| 1000004      | update subscribe group error                               | 更新订阅通道信息至数据库失败                                                                                               |
| 1000005      | delete subscribe group error                               | 从数据库删除订阅通道失败                                                                                                   |
| 1000006      | save subscribe group error                                 | 将订阅通道信息保存入数据库失败                                                                                             |
| 1000007      | query subscribe group error                                | 从数据库查询订阅通道信息失败                                                                                               |
| 1000008      | number of subscribe group reaches the   upper limit        | 订阅通道数量已达上限，不能再创建了                                                                                         |
| 1000101      | control group already exists                               | 控制通道已经存在，不能重复创建                                                                                             |
| 1000102      | control group id is illegal                                | 控制通道名字不合法，一般是控制通道名字不符合格式要求                                                                       |
| 1000103      | control group does not exist                               | 控制通道不存在，不能获取相关信息                                                                                           |
| 1000104      | update control group error                                 | 更新控制通道信息至数据库失败                                                                                               |
| 1000105      | delete control group error                                 | 从数据库删除控制通道失败                                                                                                   |
| 1000106      | save control group error                                   | 将控制通道信息保存入数据库失败                                                                                             |
| 1000107      | query control group error                                  | 从数据库查询控制通道信息失败                                                                                               |
| 1000108      | number of control group reaches the upper   limit          | 控制通道数量已达上限，不能再创建了                                                                                         |
| 1000201      | device does not exist                                      | 从设备的productKey，deviceKey或assetId，查询collectDevice失败，一般是这个设备并没有被该盒子使用                            |
| 1000202      | point id does not exist                                    | 该错误码暂时未使用                                                                                                         |
| 1000203      | timeout                                                    | 控制或写值超时                                                                                                             |
| 1000204      | invoke service error                                       | 控制命令执行失败                                                                                                           |
| 1000205      | write data error                                           | 写值命令执行失败                                                                                                           |
| 1000206      | number of sync control reaches the upper   limit           | 正在进行的同步控制数量超过阈值，不能再进行同步控制了，请稍后再试                                                           |
| 1000207      | number of async control reaches the upper   limit          | 正在进行的异步控制数量超过阈值，不能再进行异步控制了，请稍后再试                                                           |
| 1000208      | point id is not mapping                                    | 该错误码暂时未使用                                                                                                         |
| 1000209      | data upload failed                                         | 将写值命令操作的模型点数据上送至云端失败                                                                                   |
| 1000210      | data subscribe failed                                      | 将写值命令操作的模型点数据发送给订阅这些点的通道失败                                                                       |
| 1000211      | can not find model                                         | 无法获取设备模型                                                                                                           |
| 1000212      | control value is null                                      | 控制时，优先取调用控制接口时输入的值，如果没填，则使用mapping时填的值，如果两个都没填，则报错                              |
| 1000213      | can not find device point                                  | 控制一个没有mapping的模型点，就会报这个错误                                                                                |
| 1000301      | set measurepoint group already exists                      | 写值通道已经存在，不能重复创建                                                                                             |
| 1000302      | set measurepoint group id is illegal                       | 写值通道名字不合法，一般是写值通道名字不符合格式要求                                                                       |
| 1000303      | set measurepoint group does not exist                      | 写值通道不存在，不能获取相关信息                                                                                           |
| 1000304      | update set measurepoint group error                        | 更新写值通道信息至数据库失败                                                                                               |
| 1000305      | delete set measurepoint group error                        | 从数据库删除写值通道失败                                                                                                   |
| 1000306      | save set measurepoint group error                          | 将写值通道信息保存入数据库失败                                                                                             |
| 1000307      | query set measurepoint group error                         | 从数据库查询写值通道信息失败                                                                                               |
| 1000308      | number of set measurepoint group reaches   the upper limit | 写值通道数量已达上限，不能再创建了                                                                                         |
| 1000401      | check data cache by model error                            | 每次调用获取设备的实时数据接口时，会检查实时库中的数据模型是否和配置的模型一致，不一致则同步，检查时发生错误，则会报这个错 |
| 9998         | unknown error                                              | 未知错误                                                                                                                   |
| 9999         | internal error                                             | 内部错误                                                                                                                   |
