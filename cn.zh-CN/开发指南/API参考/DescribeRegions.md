# DescribeRegions {#doc_api_pvtz_DescribeRegions .reference}

调用DescribeRegions获取可用地域列表供用户选择。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeRegions&type=RPC&version=2018-01-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRegions|系统规定参数。取值：**DescribeRegions**。

 |
|AcceptLanguage|String|否|zh-CN|支持的语言。包括以下取值：

 -   中文：zh-CN
-   英文：en-US
-   日文：ja

 |
|Lang|String|否|en|语言。

 |
|UserClientIp|String|否|1.1.1.1|用户Ip。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Regions| | |地域列表。

 |
|LocalName|String|华北2（北京）|地域名称。

 |
|RegionEndpoint|String|pvtz.aliyuncs.com|Region服务的Endpoint地址。

 |
|RegionId|String|cn-shenzhen| 

 地域ID。

 |
|RegionName|String|China South 1|地域名称。

 |
|RequestId|String|AF7D4DCE-0776-47F2-A9B2-6FB85A87AA60|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://pvtz.aliyuncs.com/?Action=DescribeRegions
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeRegionsResponse>
    <RequestId>AF7D4DCE-0776-47F2-A9B2-6FB85A87AA60</RequestId>
    <Regions>
        <Region>
            <RegionName>China North 2</RegionName>
            <RegionId>cn-beijing</RegionId>
        </Region>
        <Region>
            <RegionName>China South 1</RegionName>
            <RegionId>cn-shenzhen</RegionId>
        </Region>
    </Regions>
</DescribeRegionsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"8043FAEA-4E1B-4349-AEBF-9D0FCCE5AE2F",
	"Regions":{
		"Region":[
			{
				"RegionName":"China North 2",
				"RegionId":"cn-beijing"
			},
			{
				"RegionName":"China South 1",
				"RegionId":"cn-shenzhen"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

