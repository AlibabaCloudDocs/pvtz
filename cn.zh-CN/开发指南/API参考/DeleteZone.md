# DeleteZone {#doc_api_pvtz_DeleteZone .reference}

调用DeleteZone删除private zone。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DeleteZone&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteZone|系统规定参数。取值：**DeleteZone**。

 |
|Lang|String|否|en|语言

 |
|UserClientIp|String|否|用户Ip|用户Ip

 |
|ZoneId|String|否|AgIDE1MA\_150|Zone ID

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|E246E023-F2EB-4034-83F7-B13FCF31459C|请求ID

 |
|ZoneId|String|AgIDE1MA\_150|Zone ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://pvtz.aliyuncs.com/?Action=DeleteZone
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteZoneResponse>
    <RequestId>B5174E6E-0AA6-4524-BCE4-603DED055319</RequestId>
    <ZoneId>AgIDE1MA_151</ZoneId>
</DeleteZoneResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"3852E9B7-417E-40C6-AD98-B691CA82C4F4",
	"ZoneId":"AgIDE1MA_150"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

