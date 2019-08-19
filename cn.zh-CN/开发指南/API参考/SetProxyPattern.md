# SetProxyPattern {#doc_api_pvtz_SetProxyPattern .reference}

调用SetProxyPattern设置递归解析代理。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=SetProxyPattern&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetProxyPattern|系统规定参数。取值：SetProxyPattern。

 |
|ZoneId|String|是|AgIDE0OQ\_149|Zone的全局ID。

 |
|Lang|String|否|en|语言。

 |
|ProxyPattern|String|否|ZONE|取值：

 -   **ZONE**: 全部劫持解析
-   **RECORD**: 开启递归解析代理

 |
|UserClientIp|String|否|1.1.1.1|用户IP。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|C6F1D541-E7A6-447A-A2B5-9F7A20B2A8FB|请求ID。

 |
|ZoneId|String|AgIDE0OQ\_149|Zone的全局ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://pvtz.aliyuncs.com/?Action=SetProxyPattern
&ZoneId=AgIDE0OQ_149
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetProxyPatternResponse>
    <RequestId>D1324D48-1E23-4AEF-9EDE-466120561C6F</RequestId>
    <ZoneId>AgIDE0OQ_149</ZoneId>
</SetProxyPatternResponse>
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

