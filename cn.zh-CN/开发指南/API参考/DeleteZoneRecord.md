# DeleteZoneRecord {#doc_api_pvtz_DeleteZoneRecord .reference}

调用DeleteZoneRecord删除解析记录。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DeleteZoneRecord&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteZoneRecord|系统规定参数。取值：**DeleteZoneRecord**。

 |
|RecordId|Long|是|5808|解析记录ID。

 |
|Lang|String|否|en|语言。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordId|Long|5808|解析记录ID。

 |
|RequestId|String|0B7AD377-7E86-44A8-B9A8-53E8666E72FE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=DeleteZoneRecord
&RecordId=5808
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteZoneRecordResponse>
    <RecordId>5808</RecordId>
    <RequestId>FEAF2786-5DB3-4A1F-B859-E8B28B672E9B</RequestId>
</DeleteZoneRecordResponse>
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

