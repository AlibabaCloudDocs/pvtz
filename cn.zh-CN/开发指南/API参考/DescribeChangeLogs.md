# DescribeChangeLogs {#doc_api_pvtz_DescribeChangeLogs .reference}

调用DescribeChangeLogs获取变更日志。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeChangeLogs&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeChangeLogs|系统规定参数。取值：**DescribeChangeLogs**。

 |
|EndTimestamp|Long|否|1516779348000|结束时间（时间戳）。

 |
|EntityType|String|否|PV\_ZONE|获取的日志类型。

 -   **PV\_ZONE**为zone的操作日志。
-   **PV\_RECORD**为解析记录的操作日志。

 其它值则忽略，获取所有日志。

 |
|Keyword|String|否|test|关键字，按照“%KeyWord%”模式搜索，不区分大小写。

 |
|Lang|String|否|en|语言。

 |
|PageNumber|Integer|否|1|当前页数，起始值为**1**，默认为**1**。

 |
|PageSize|Integer|否|100|分页查询时设置的每页行数，最大值**100**，默认为**20**。

 |
|StartTimestamp|Long|否|1516779348000|开始时间（时间戳）。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |
|ZoneId|String|否|6726|Zone ID。

 **说明：** 若ZoneId不为空，则获取变更日志，若ZoneId为空，则获取操作记录。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ChangeLogs| | |变更日志。

 |
|Content|String|add test-api.com|操作详情。

 |
|EntityId|String|CAgICA1OA\_58|操作对象ID。

 |
|EntityName|String|test-api.com|操作对象名称。

 |
|Id|Long|6726|记录ID。

 |
|OperAction|String|add|操作动作。

 |
|OperIp|String|1.1.1.1|操作Ip。

 |
|OperObject|String|PV\_ZONE|操作对象类型。

 |
|OperTime|String|2018-01-24T07:35Z|操作时间。

 |
|OperTimestamp|Long|1516779348000|操作时间戳。

 |
|PageNumber|Integer|2|当前页码。

 |
|PageSize|Integer|1|当前页面大小。

 |
|RequestId|String|F0FCB52A-D512-41A0-8595-40234EDCFD8B|请求ID。

 |
|TotalItems|Integer|100|日志列表总数。

 |
|TotalPages|Integer|100|总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=AddZoneRecord
&ZoneId=CAgICA1OA_58
&Rr=www
&Type=A
&Ttl=60
&Value=1.1.1.1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeChangeLogsResponse>
    <PageNumber>1</PageNumber>
    <ChangeLogs>
        <ChangeLog>
            <OperTimestamp>1516779348000</OperTimestamp>
            <OperAction>add</OperAction>
            <OperObject>PV_ZONE</OperObject>
            <OperIp>106.11.34.7</OperIp>
            <Id>6726</Id>
            <EntityName>test-api.com</EntityName>
            <OperTime>2018-01-24T07:35Z</OperTime>
            <Content>add test-api.com</Content>
            <EntityId>CAgICA1OA_58</EntityId>
        </ChangeLog>
    </ChangeLogs>
    <PageSize>1</PageSize>
    <RequestId>F0FCB52A-D512-41A0-8595-40234EDCFD8B</RequestId>
    <TotalItems>224</TotalItems>
    <TotalPages>224</TotalPages>
</DescribeChangeLogsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"PageSize":1,
	"ChangeLogs":{
		"ChangeLog":[
			{
				"OperTimestamp":1516779348000,
				"OperAction":"add",
				"OperObject":"PV_ZONE",
				"OperIp":"106.11.34.7",
				"OperTime":"2018-01-24T07:35Z",
				"EntityName":"test-api.com",
				"Id":6726,
				"Content":"add test-api.com",
				"EntityId":"CAgICA1OA_58"
			}
		]
	},
	"RequestId":"50C60A29-2E93-425A-ABA8-068686E28873",
	"TotalItems":224,
	"TotalPages":224
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

