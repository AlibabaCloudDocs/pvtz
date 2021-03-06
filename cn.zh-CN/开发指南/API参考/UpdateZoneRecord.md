# UpdateZoneRecord {#doc_api_pvtz_UpdateZoneRecord .reference}

调用UpdateZoneRecord修改解析记录。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=UpdateZoneRecord&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateZoneRecord|系统规定参数。取值：**UpdateZoneRecord**。

 |
|RecordId|Long|是|5809|解析记录ID。

 |
|Rr|String|是|www|主机记录。

 如果要解析@.exmaple.com，主机记录要填写"@”，而不是空。

 |
|Type|String|是|A|解析记录类型。

 |
|Value|String|是|1.1.1.1|记录值。

 |
|Lang|String|否|en|语言。

 |
|Priority|Integer|否|60|MX记录的优先级，取值范围：**\\\[1,10\\\]**。

 记录类型为MX记录时，此参数必选。

 |
|Ttl|Integer|否|60|生存时间。

 |
|UserClientIp|String|否|2.2.2.2|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordId|Long|5809|解析记录ID。

 |
|RequestId|String|250E2C38-D0AD-4518-851D-1C1055805F82|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=UpdateZoneRecord
&Rr=www
&Type=A
&Ttl=60
&Value=1.1.1.1
&RecordId=5809
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateZoneRecordResponse>
    <RecordId>5809</RecordId>
    <RequestId>43909504-7C3E-4660-AF75-59EE0C480681</RequestId>
</UpdateZoneRecordResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RecordId":5809,
	"RequestId":"250E2C38-D0AD-4518-851D-1C1055805F82"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

