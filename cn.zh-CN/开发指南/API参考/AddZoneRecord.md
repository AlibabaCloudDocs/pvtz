# AddZoneRecord {#doc_api_pvtz_AddZoneRecord .reference}

调用AddZoneRecord添加prviate zone的解析记录。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=AddZoneRecord&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddZoneRecord|系统规定参数。取值：**AddZoneRecord**。

 |
|Rr|String|是|www|主机记录。

 如果要解析@.exmaple.com，主机记录要填写"@”，而不是空。

 |
|Type|String|是|A|解析记录类型，目前仅支持**A**, **CNAME**, **TXT**, **MX**, **PTR**。

 |
|Value|String|是|1.1.1.1|记录值。

 |
|ZoneId|String|是|CAgICA1OA\_58|Zone ID。

 |
|Lang|String|否|en|语言。

 |
|Priority|Integer|否|5|MX记录的优先级，取值范围：**\\\[1,10\\\]**。

 |
|Ttl|Integer|否|60|生存时间，默认值为**60**。

 |
|UserClientIp|String|否|2.2.2.2|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordId|Long|5808|解析记录ID。

 |
|RequestId|String|0B7AD377-7E86-44A8-B9A8-53E8666E72FE|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=AddZoneRecord
&ZoneId=CAgICA1OA_58
&Rr=www
&Type=A
&Ttl=60
&Value=1.1.1.1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddZoneRecordResponse>
    <RecordId>5809</RecordId>
    <RequestId>D4AD014E-46F6-4311-815B-AAB3ACE06F9C</RequestId>
</AddZoneRecordResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RecordId":5808,
	"RequestId":"0B7AD377-7E86-44A8-B9A8-53E8666E72FE"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

