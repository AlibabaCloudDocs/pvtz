# CheckZoneName {#doc_api_pvtz_CheckZoneName .reference}

调用CheckZoneName根据规则校验zone是否可添加。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=CheckZoneName&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CheckZoneName|系统规定参数。取值：**CheckZoneName**。

 |
|Lang|String|否|en|语言。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |
|ZoneName|String|否|demo.com|zone的名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Check|Boolean|true|取值：

 -   **true**：可添加
-   **false**：不可添加

 |
|RequestId|String|CA29B88F-A571-4123-80D5-768AC2F7F806|请求ID。

 |
|Success|Boolean|true|是否成功。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=CheckZoneName
&ZoneName=demo.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CheckZoneNameResponse>
    <Check>true</Check>
    <RequestId>CA29B88F-A571-4123-80D5-768AC2F7F806</RequestId>
</CheckZoneNameResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Check":true,
	"RequestId":"0AF4FE63-5904-4E62-B1AC-B36810377811"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

