# UpdateZoneRemark {#doc_api_pvtz_UpdateZoneRemark .reference}

调用UpdateZoneRemark修改zone的备注信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=UpdateZoneRemark&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateZoneRemark|系统规定参数。取值：**UpdateZoneRemark**。

 |
|ZoneId|String|是|AgIDE1MA\_149|Zone ID。

 |
|Lang|String|否|en|语言。

 |
|Remark|String|否|test|备注。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C6F1D541-E7A6-447A-A2B5-9F7A20B2A8FB|请求ID。

 |
|ZoneId|String|AgIDE1MA\_149|Zone ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?&Action=UpdateZoneRemark
&ZoneId=AgIDE1MA_149
&Remark=specialZone
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateZoneRemarkResponse>
    <RequestId>D1324D48-1E23-4AEF-9EDE-466120561C6F</RequestId>
    <ZoneId>AgIDE0OQ_149</ZoneId>
</UpdateZoneRemarkResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"C6F1D541-E7A6-447A-A2B5-9F7A20B2A8FB",
	"ZoneId":"AgIDE0OQ_149"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

