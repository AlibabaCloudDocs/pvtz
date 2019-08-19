# SetZoneRecordStatus {#doc_api_pvtz_SetZoneRecordStatus .reference}

调用SetZoneRecordStatus设置解析记录状态。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=SetZoneRecordStatus&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetZoneRecordStatus|系统规定参数。取值：**SetZoneRecordStatus**。

 |
|RecordId|Long|是|5809|解析记录ID。

 |
|Status|String|是|DISABLE|解析记录状态。取值：

 -   **ENABLE**: 启用解析
-   **DISABLE**: 暂停解析

 |
|Lang|String|否|en|语言。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordId|Long|5809|解析记录ID。

 |
|RequestId|String|39CB16E5-4180-49F2-A060-23C0ECEB80D9|请求ID。

 |
|Status|String|DISABLE|当前解析记录状态。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=SetZoneRecordStatus
&RecordId=5809
&Status=DISABLE
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetZoneRecordStatusResponse>
    <Status>DISABLE</Status>
    <RequestId>39CB16E5-4180-49F2-A060-23C0ECEB80D9</RequestId>
    <RecordId>5809</RecordId>
</SetZoneRecordStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Status":"DISABLE",
	"RecordId":5809,
	"RequestId":"8952D275-70D6-4634-B78E-200A3E78C28A"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

