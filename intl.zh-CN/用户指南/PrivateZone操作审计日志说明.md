PrivateZone操作审计日志说明 
========================================

阿里云 PrivateZone 已与 阿里云 ActionTrail 集成，您可以在 ActionTrail 中查看和检索用户行为日志，同时通过ActrionTrail 将日志投递到日志服务 LogStore 或指定的 OSS Bucket 中，满足实时审计、问题回溯分析等需要。

ActionTrail 中记录的 PrivateZone 操作日志 
------------------------------------------------------

PrivateZone 的操作审计日志主要包含的是 API 事件，其中 OpenAPI 事件在 ActionTrail 中记录的 eventType 取值为 ApiCall，其含义可以参考 [PrivateZone的API说明](https://www.alibabacloud.com/help/zh/doc-detail/66234.htm?spm=a2c63.l28256.b99.30.c3c850b7OUghWz)。

部分 API 事件目前尚未包含在上述的 API 说明文档中，这些事件的含义参考如下：


|---------|-------------------------|--------------|
| 事件类型    | 事件名称                    | 事件含义         |
| ApiCall | ImportEcsHostName       | 添加主机名记录      |
| ApiCall | UpdateSyncEcsHostTasK   | 更新自动同步主机名配置  |
| ApiCall | UpdateSlaveDnsConfig    | 更新辅助DNS的配置   |
| ApiCall | SetSlaveDnsConfigStatus | 开启/关闭辅助DNS同步 |
| ApiCall | DeleteSlaveDnsConfig    | 删除辅助DNS的配置   |
| ApiCall | AddSlaveDnsConfig       | 添加辅助DNS的配置   |


注：部分API由于还在调整优化中，文档中暂时未记录。

PrivateZone 的日志样例 
--------------------------------------

下面展示了一个 ActionTrail 中记录的 PrivateZone创建解析记录的日志，该条日志记录了 PrivateZone AddZoneRecord 操作记录的详细信息：

    {
      "eventId": "99680534-****-****-****-DCFD92E18FAB",
      "eventVersion": 1,
      "responseElements": {
        "RequestId": "99680534-****-****-****-DCFD92E18FAB",
        "RecordId": 175***657,
        "Success": true
      },
      "eventSource": "pvtz.aliyuncs.com",
      "requestParameters": {
        "Rr": "abc",
        "userClientIp": "100.**.***.69",
        "AcsHost": "pvtz.aliyuncs.com",
        "ZoneId": "d696741102e*******0ca13e934bd07",
        "RequestId": "99680534-****-****-****-DCFD92E18FAB",
        "Lang": "zh",
        "HostId": "pvtz.aliyuncs.com",
        "Ttl": 60,
        "Type": "A",
        "ServiceCode": "pvtz",
        "AcsProduct": "pvtz",
        "UserClientIp": "100.**.***.69",
        "Value": "5.*.*.5",
        "RegionId": "cn-hangzhou"
      },
      "sourceIpAddress": "Internal",
      "userAgent": "AlibabaCloud (Linux; amd64) Java/1.**_172-b9 Core/***.6 HTTPClient/ApacheHttpClient",
      "eventType": "ApiCall",
      "referencedResources": {
        "ACS::PrivateZone::ZoneRecord": [
          "175***657"
        ]
      },
      "userIdentity": {
      updateZOne  "sessionContext": {
          "attributes": {
            "mfaAuthenticated": "false"
          }
        },
        "accountId": "12046******1685",
        "principalId": "12046******1685",
        "type": "root-account",
        "userName": "root"
      },
      "serviceName": "PrivateZone",
      "additionalEventData": {
        "Scheme": "http"
      },
      "apiVersion": "2018-01-01",
      "requestId": "99680534-****-****-****-DCFD92E18FAB",
      "eventTime": "2021-01-08T04:56:37Z",
      "isGlobal": false,
      "acsRegion": "cn-hangzhou",
      "eventName": "AddZoneRecord"
    }



