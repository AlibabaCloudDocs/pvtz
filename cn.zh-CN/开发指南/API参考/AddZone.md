# AddZone {#doc_api_pvtz_AddZone .reference}

调用AddZone创建private zone。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=AddZone&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddZone|系统规定参数。取值：**AddZone**。

 |
|Lang|String|否|en|语言。

 |
|ProxyPattern|String|否|ZONE|-   **ZONE**：完全劫持整个Zone
-   **RECORD**：不完全劫持，进行递归解析代理

 |
|ResourceGroupId|String|否|rg-resourcegroupid1|资源组ID。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |
|ZoneName|String|否|demo.com|zone名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|46973D4C-E3E4-4ABA-9190-9A9DE406C7E|请求ID。

 |
|Success|Boolean|true|是否成功。

 |
|ZoneId|String|AgIDE1MQ\_151|zone ID。

 |
|ZoneName|String|demo.com|zone名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=AddZone
&ZoneName=demo.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddZoneResponse>
    <ZoneName>demo.com</ZoneName>
    <RequestId>0C9959BE-3A6A-4803-8DCE-973B42ACD599</RequestId>
    <ZoneId>AgIDE1MA_150</ZoneId>
</AddZoneResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ZoneName":"demo.com",
	"RequestId":"46973D4C-E3E4-4ABA-9190-9A9DE406C7EE",
	"ZoneId":"AgIDE1MQ_151"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

