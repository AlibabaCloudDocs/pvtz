API概览 
==========================



云解析 PrivateZone提供以下相关API接口。

Zone管理 
---------------------------



|                                         API                                          |                           描述                           |
|--------------------------------------------------------------------------------------|--------------------------------------------------------|
| [查询服务状态](/cn.zh-CN/开发指南/API参考/Zone管理/查询服务状态.md)                   | 调用DescribeUserServiceStatus查询当前用户的服务状态，例如是否开通服务，是否欠费等。 |
| [获取zone列表](/cn.zh-CN/开发指南/API参考/Zone管理/获取zone列表.md)               | 调用DescribeZones查询用户的zone列表。                            |
| [添加zone](/cn.zh-CN/开发指南/API参考/Zone管理/添加zone.md)                   | 调用AddZone创建private zone。                               |
| [检查zone名称](/cn.zh-CN/开发指南/API参考/Zone管理/检查zone名称.md)               | 调用CheckZoneName根据规则校验zone是否可添加。                        |
| [修改zone备注信息](/cn.zh-CN/开发指南/API参考/Zone管理/修改zone备注信息.md)           | 调用UpdateZoneRemark修改zone的备注信息。                         |
| [获取zone详细信息](/cn.zh-CN/开发指南/API参考/Zone管理/获取zone详细信息.md)           | 调用DescribeZoneInfo获取指定zone的详细信息。                       |
| [删除zone](/cn.zh-CN/开发指南/API参考/Zone管理/删除zone.md)                   | 调用DeleteZone删除private zone。                            |
| [获取Region列表](/cn.zh-CN/开发指南/API参考/Zone管理/获取Region列表.md)           | 调用DescribeRegions获取可用地域列表供用户选择。                        |
| [zone关联VPC](/cn.zh-CN/开发指南/API参考/Zone管理/zone关联VPC.md)             | 调用BindZoneVpc绑定或者解绑zone与VPC列表两者之间的关系。                  |
| [设置递归解析代理](/cn.zh-CN/开发指南/API参考/Zone管理/设置递归解析代理.md)               | 调用SetProxyPattern设置递归解析代理。                             |
| [获取Zone列表和绑定的vpc](/cn.zh-CN/开发指南/API参考/Zone管理/获取Zone列表和绑定的vpc.md) | 调用DescribeZoneVpcTree获取zone列表及其绑定的 vpc 列表。             |



解析记录管理 
---------------------------



|                                  API                                   |                 描述                  |
|------------------------------------------------------------------------|-------------------------------------|
| [添加解析记录](/cn.zh-CN/开发指南/API参考/解析记录管理/添加解析记录.md)     | 调用AddZoneRecord添加prviate zone的解析记录。 |
| [修改解析记录](/cn.zh-CN/开发指南/API参考/解析记录管理/修改解析记录.md)     | 调用UpdateZoneRecord修改解析记录。           |
| [删除解析记录](/cn.zh-CN/开发指南/API参考/解析记录管理/删除解析记录.md)     | 调用DeleteZoneRecord删除解析记录。           |
| [获取解析记录列表](/cn.zh-CN/开发指南/API参考/解析记录管理/获取解析记录列表.md) | 调用DescribeZoneRecords查询解析记录列表。      |
| [设置解析记录状态](/cn.zh-CN/开发指南/API参考/解析记录管理/设置解析记录状态.md) | 调用SetZoneRecordStatus设置解析记录状态。      |
| [获取变更日志](/cn.zh-CN/开发指南/API参考/解析记录管理/获取操作日志.md)     | 调用DescribeChangeLogs获取变更日志。         |
| [更新解析记录备注](/cn.zh-CN/开发指南/API参考/解析记录管理/更新解析记录备注.md) | 修改解析记录的备注                           |



请求量管理 
--------------------------



|                                   API                                   |                  描述                  |
|-------------------------------------------------------------------------|--------------------------------------|
| [获取昨日请求量概要](/cn.zh-CN/开发指南/API参考/请求量管理/获取昨日请求量概要.md) | 调用DescribeStatisticSummary获取昨日请求量概要。 |
| [获取请求量详情](/cn.zh-CN/开发指南/API参考/请求量管理/获取请求量详情.md)     | 调用DescribeRequestGraph获取请求量详情。       |



标签 
-----------------------



|                                 API                                 |              描述              |
|---------------------------------------------------------------------|------------------------------|
| [标记资源](/cn.zh-CN/开发指南/API参考/标签/标记资源.md)             | 调用TagResources标记资源           |
| [取消标记资源](/cn.zh-CN/开发指南/API参考/标签/取消标记资源.md)         | 调用UntagResources取消标记资源       |
| [查询资源标签关系列表](/cn.zh-CN/开发指南/API参考/标签/查询资源标签关系列表.md) | 调用ListTagResources查询资源标签关系列表 |
| [查询已有的标签列表](/cn.zh-CN/开发指南/API参考/标签/查询已有的标签列表.md)   | 调用DescribeTags查询已有的标签列表      |



