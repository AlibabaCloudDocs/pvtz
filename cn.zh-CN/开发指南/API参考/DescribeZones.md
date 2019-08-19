# DescribeZones {#doc_api_pvtz_DescribeZones .reference}

调用DescribeZones查询用户的zone列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeZones&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZones|系统规定参数。取值：**DescribeZones**。

 |
|Keyword|String|否|test|关键字，按照“%KeyWord%”模式搜索，不区分大小写。

 |
|Lang|String|否|en|语言。

 |
|PageNumber|Integer|否|1|当前页数，起始值为**1**，默认为**1**。

 |
|PageSize|Integer|否|100|分页查询时设置的每页行数，最大值**100**，默认为**20**。

 |
|QueryRegionId|String|否|cn-hangzhou|所属地域ID。

 |
|QueryVpcId|String|否|vpc-xxxxx|VPC ID。

 |
|ResourceGroupId|String|否|rg-xxxxx|资源组ID。

 |
|SearchMode|String|否|LIKE|搜索模式。取值：

 -   **LIKE**：模糊搜索
-   **EXACT**：精确搜索，默认不填为精确搜索

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|页码。

 |
|PageSize|Integer|20|页面大小。

 |
|RequestId|String|6856BCF6-11D6-4D7E-AC53-FD579933522B|请求ID。

 |
|TotalItems|Integer|3|总个数。

 |
|TotalPages|Integer|3|总页数。

 |
|Zones| | |zone列表。

 |
|CreateTime|String|2017-12-28T13:08Z|创建时间。

 |
|CreateTimestamp|Long|1514466483000|创建时间（时间戳）。

 |
|IsPtr|Boolean|true|-   true，是反解zone
-   false，非反解zone

 |
|ProxyPattern|String|ZONE|-   **ZONE**: 全部劫持
-   **RECORD**：开启递归解析代理

 |
|RecordCount|Integer|2|解析记录数。

 |
|Remark|String|test|zone备注信息。

 |
|UpdateTime|String|2018-01-03T08:57Z|更新时间。

 |
|UpdateTimestamp|Long|1514969843000|更新时间（时间戳）。

 |
|ZoneId|String|ICAgICAgI\_24|zone ID。

 |
|ZoneName|String|test.com|zone名称。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://pvtz.aliyuncs.com/?Action=DescribeZones
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeZonesResponse>
    <PageNumber>1</PageNumber>
    <PageSize>20</PageSize>
    <RequestId>42532529-0608-4B9B-81EC-BFA995B1AC2C</RequestId>
    <TotalItems>22</TotalItems>
    <TotalPages>2</TotalPages>
    <Zones>
        <Zone>
            <ZoneName>niu.com</ZoneName>
            <IsPtr>false</IsPtr>
            <CreateTimestamp>1516677356000</CreateTimestamp>
            <RecordCount>2</RecordCount>
            <UpdateTimestamp>1516775741000</UpdateTimestamp>
            <CreateTime>2018-01-23T03:15Z</CreateTime>
            <UpdateTime>2018-01-24T06:35Z</UpdateTime>
            <ZoneId>AgIDE0OQ_149</ZoneId>
            <Remark>specialZone</Remark>
        </Zone>
        <Zone>
            <ZoneName>walpole.test</ZoneName>
            <IsPtr>false</IsPtr>
            <CreateTimestamp>1516635773000</CreateTimestamp>
            <RecordCount>3</RecordCount>
            <UpdateTimestamp>1516637934000</UpdateTimestamp>
            <CreateTime>2018-01-22T15:42Z</CreateTime>
            <UpdateTime>2018-01-22T16:18Z</UpdateTime>
            <ZoneId>AgIDE0OA_148</ZoneId>
        </Zone>
        <Zone>
            <ZoneName>zone.com</ZoneName>
            <IsPtr>false</IsPtr>
            <CreateTimestamp>1516616030000</CreateTimestamp>
            <RecordCount>2</RecordCount>
            <UpdateTimestamp>1516622372000</UpdateTimestamp>
            <CreateTime>2018-01-22T10:13Z</CreateTime>
            <UpdateTime>2018-01-22T11:59Z</UpdateTime>
            <ZoneId>AgIDE0Nw_147</ZoneId>
            <Remark>abc</Remark>
        </Zone>
    </Zones>
</DescribeZonesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"PageSize":20,
	"RequestId":"6856BCF6-11D6-4D7E-AC53-FD579933522B",
	"TotalItems":3,
	"TotalPages":1,
	"Zones":[
		{
			"ZoneName":"demo111.com",
			"IsPtr":false,
			"CreateTimestamp":1514466483000,
			"RecordCount":0,
			"UpdateTimestamp":1514969843000,
			"CreateTime":"2017-12-28T13:08Z",
			"UpdateTime":"2018-01-03T08:57Z",
			"ZoneId":"ICAgICAgI_24",
			"Remark":"ddddd"
		},
		{
			"ZoneName":"demo111.com",
			"IsPtr":false,
			"CreateTimestamp":1514454600000,
			"RecordCount":0,
			"UpdateTimestamp":1514454600000,
			"CreateTime":"2017-12-28T09:50Z",
			"UpdateTime":"2017-12-28T09:50Z",
			"ZoneId":"ICAgICAgI_22",
			"Remark":"aaaa"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

