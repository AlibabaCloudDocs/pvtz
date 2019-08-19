# DescribeZoneRecords {#doc_api_pvtz_DescribeZoneRecords .reference}

调用DescribeZoneRecords查询解析记录列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeZoneRecords&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZoneRecords|系统规定参数。取值：**DescribeZoneRecords**。

 |
|ZoneId|String|是|CAgICA1OA\_58|Zone ID。

 |
|Keyword|String|否|test|主机记录的关键字，按照”%Keyword%”模式搜索，不区分大小写。

 |
|Lang|String|否|en|语言。

 |
|PageNumber|Integer|否|1|当前页数，起始值为**1**，默认为**1**。

 |
|PageSize|Integer|否|100|分页查询时设置的每页行数，最大值**500**，默认为**20**。

 |
|SearchMode|String|否|LIKE|搜索模式。取值：

 -   **LIKE**：模糊搜索
-   **EXACT**：精确搜索（默认）

 |
|Tag|String|否|tag|标签。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|100|分页大小。

 |
|Records| | |解析记录列表。

 |
|Priority|Integer|60|MX记录的优先级，取值范围：**\\\[1,10\\\]**。

 记录类型为MX记录时，此参数必选。

 |
|RecordId|Long|5809|解析记录ID。

 |
|Rr|String|www|主机记录。

 |
|Status|String|ENABLE|状态。

 |
|Ttl|Integer|60|生存时间，默认为**60**。

 |
|Type|String|A|解析记录类型。

 |
|Value|String|1.1.1.1|记录值。

 |
|RequestId|String|7B07FBC3-3A53-4939-A3C6-2BDFE407BAB2|请求ID。

 |
|TotalItems|Integer|100|解析记录总数。

 |
|TotalPages|Integer|100|解析记录总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=DescribeZoneRecords
&ZoneId=CAgICA1OA_58
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeZoneRecordsResponse>
    <PageNumber>1</PageNumber>
    <Records>
        <Record>
            <Status>DISABLE</Status>
            <Value>1.1.1.1</Value>
            <Rr>www</Rr>
            <RecordId>5809</RecordId>
            <Ttl>60</Ttl>
            <Type>A</Type>
        </Record>
        <Record>
            <Status>ENABLE</Status>
            <Value>1.1.1.1</Value>
            <Rr>a49880308bb2</Rr>
            <RecordId>5808</RecordId>
            <Ttl>60</Ttl>
            <Type>A</Type>
        </Record>
    </Records>
    <PageSize>20</PageSize>
    <RequestId>7B07FBC3-3A53-4939-A3C6-2BDFE407BAB2</RequestId>
    <TotalItems>2</TotalItems>
    <TotalPages>1</TotalPages>
</DescribeZoneRecordsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"Records":{
		"Record":[
			{
				"Status":"DISABLE",
				"Rr":"www",
				"Value":"1.1.1.1",
				"RecordId":5809,
				"Type":"A",
				"Ttl":60
			},
			{
				"Status":"ENABLE",
				"Rr":"a49880308bb2",
				"Value":"1.1.1.1",
				"RecordId":5808,
				"Type":"A",
				"Ttl":60
			}
		]
	},
	"PageSize":20,
	"RequestId":"2748A96A-3D47-4B27-AE8B-75C41B16D652",
	"TotalItems":2,
	"TotalPages":1
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

