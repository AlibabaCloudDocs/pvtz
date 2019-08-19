# DescribeZoneInfo {#doc_api_pvtz_DescribeZoneInfo .reference}

调用DescribeZoneInfo获取指定zone的详细信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeZoneInfo&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZoneInfo|系统规定参数。取值：**DescribeZoneInfo**。

 |
|Lang|String|否|en|语言。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |
|ZoneId|String|否|AgIDE1MA\_149|Zone ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BindVpcs| | |绑定的Vpc列表。

 |
|RegionId|String|1304|地域ID。

 |
|RegionName|String|1304|地域名称。

 |
|ReionId|String|1304|地域ID。

 |
|VpcId|String|daily-vpc-id|Vpc ID。

 |
|VpcName|String|daily-vpc-name|Vpc名称。

 |
|CreateTime|String|2018-01-23T03:15Z|创建时间。

 |
|CreateTimestamp|Long|1516775741000| 

 创建时间（时间戳）。

 |
|IsPtr|Boolean|false|-   true，是反解zone
-   false，非反解zone

 |
|ProxyPattern|String|ZONE|-   **ZONE**：完全劫持
-   **RECORD**：递归解析代理

 |
|RecordCount|Integer|2|含有的解析记录总数。

 |
|Remark|String|specialZone|备注。

 |
|RequestId|String|F73F41A3-B6DD-42CA-A793-FFF93277835D|请求ID。

 |
|SlaveDns|Boolean|true|是否开启辅助DNS。取值：

 -   **true**：已开启
-   **false**：未开启

 |
|UpdateTime|String|2018-01-24T06:35Z|更新时间。

 |
|UpdateTimestamp|Long|1516775741000|更新时间（时间戳）。

 |
|ZoneId|String|AgIDE0OQ\_149<|Zone ID。

 |
|ZoneName|String|test.com|Zone名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=DescribeZoneInfo
&ZoneId=AgIDE1MA_149
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeZoneInfoResponse>
    <ZoneName>niu.com</ZoneName>
    <IsPtr>false</IsPtr>
    <CreateTimestamp>1516677356000</CreateTimestamp>
    <RecordCount>2</RecordCount>
    <BindVpcs>
        <Vpc>
            <VpcName>daily-vpc-name</VpcName>
            <RegionName>1304</RegionName>
            <ReionId>1304</ReionId>
            <VpcId>daily-vpc-id</VpcId>
        </Vpc>
    </BindVpcs>
    <UpdateTimestamp>1516775741000</UpdateTimestamp>
    <CreateTime>2018-01-23T03:15Z</CreateTime>
    <RequestId>F73F41A3-B6DD-42CA-A793-FFF93277835D</RequestId>
    <UpdateTime>2018-01-24T06:35Z</UpdateTime>
    <ZoneId>AgIDE0OQ_149</ZoneId>
    <Remark>specialZone</Remark>
</DescribeZoneInfoResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ZoneName":"niu.com",
	"CreateTimestamp":1516677356000,
	"IsPtr":false,
	"RecordCount":2,
	"BindVpcs":{
		"Vpc":[
			{
				"VpcName":"daily-vpc-name",
				"RegionName":"1304",
				"ReionId":"1304",
				"VpcId":"daily-vpc-id"
			}
		]
	},
	"RequestId":"29D0F8F8-5499-4F6C-9FDC-1EE13BF55925",
	"CreateTime":"2018-01-23T03:15Z",
	"UpdateTimestamp":1516775741000,
	"UpdateTime":"2018-01-24T06:35Z",
	"ZoneId":"AgIDE0OQ_149",
	"Remark":"specialZone"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Zone.Invalid.Id|Zone id is invalid.|Zone的ID不正确|

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

