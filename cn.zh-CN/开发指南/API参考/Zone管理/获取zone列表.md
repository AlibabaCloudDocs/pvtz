# 获取zone列表

调用DescribeZones查询用户的zone列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=DescribeZones&type=RPC&version=2018-01-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZones|系统规定参数。取值：**DescribeZones**。 |
|Lang|String|否|en|语言。 |
|PageNumber|Integer|否|1|当前页数，起始值为**1**，默认为**1**。 |
|PageSize|Integer|否|100|分页查询时设置的每页行数，最大值**100**，默认为**20**。 |
|Keyword|String|否|test|关键字，按照“%KeyWord%”模式搜索，不区分大小写。 |
|SearchMode|String|否|LIKE|搜索模式。取值：

 -   **LIKE**：模糊搜索
-   **EXACT**：精确搜索，默认不填为精确搜索 |
|QueryRegionId|String|否|cn-hangzhou|所属地域ID。 |
|QueryVpcId|String|否|vpc-xxxxx|VPC ID。 |
|ResourceGroupId|String|否|rg-xxxxx|资源组ID。 |
|ZoneType|String|否|CLOUD\_PRODUCT\_ZONE|Zone查询类型；默认取值AUTH\_ZONE，查权威Zone列表。

 取值范围：

 -   AUTH\_ZONE: 查权威Zone列表。
-   CLOUD\_PRODUCT\_ZONE:使用的云产品Zone列表。 |
|ZoneTag.N|RepeatList|否|BLINK|-   若查权威Zone列表，则忽略此参数；
-   若查使用或者管理的云产品PrivateZone，则查询对应的云产品类型Zone列表。 |
|ResourceTag.N.Key|String|否|env|资源标签键。 |
|ResourceTag.N.Value|String|否|daily|资源标签值。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|页码。 |
|PageSize|Integer|20|页面大小。 |
|RequestId|String|6856BCF6-11D6-4D7E-AC53-FD579933522B|请求ID。 |
|TotalItems|Integer|3|总个数。 |
|TotalPages|Integer|3|总页数。 |
|Zones|Array of Zone| |zone列表。 |
|Zone| | | |
|CreateTime|String|2017-12-28T13:08Z|创建时间。 |
|CreateTimestamp|Long|1514466483000|创建时间（时间戳）。 |
|IsPtr|Boolean|true|-   true，是反解zone
-   false，非反解zone |
|ProxyPattern|String|ZONE|-   **ZONE**: 全部劫持
-   **RECORD**：开启递归解析代理 |
|RecordCount|Integer|2|解析记录数。 |
|Remark|String|test|zone备注信息。 |
|ResourceGroupId|String|rg-xxxxx|资源组ID。 |
|ResourceTags|Array of ResourceTag| |资源标签列表。 |
|ResourceTag| | | |
|Key|String|env|资源标签键。 |
|Value|String|daily|资源标签值。 |
|UpdateTime|String|2018-01-03T08:57Z|更新时间。 |
|UpdateTimestamp|Long|1514969843000|更新时间（时间戳）。 |
|ZoneId|String|ICAgICAgI\_24|zone ID。 |
|ZoneName|String|test.com|zone名称。 |
|ZoneTag|String|BLINK|云产品类型：

 -   若ZoneType为权威zone，则此为空；
-   若ZoneType为云产品zone，则此为云产品类型。 |
|ZoneType|String|CLOUD\_PRODUCT\_ZONE|Zone类型：

 -   AUTH\_ZONE: 权威Zone。
-   CLOUD\_PRODUCT\_ZONE: 云产品PrivateZone。 |

## 示例

请求示例

```
http(s)://pvtz.aliyuncs.com/?Action=DescribeZones
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<PageSize>20</PageSize>
<RequestId>6856BCF6-11D6-4D7E-AC53-FD579933522B</RequestId>
<PageNumber>1</PageNumber>
<TotalPages>3</TotalPages>
<TotalItems>3</TotalItems>
<Zones>
    <Zone>
        <ZoneName>test.com</ZoneName>
        <ResourceGroupId>rg-xxxxx</ResourceGroupId>
        <ZoneId>ICAgICAgI_24</ZoneId>
        <ProxyPattern>ZONE</ProxyPattern>
        <ZoneTag>BLINK</ZoneTag>
        <CreateTime>2017-12-28T13:08Z</CreateTime>
        <UpdateTime>2018-01-03T08:57Z</UpdateTime>
        <UpdateTimestamp>1514969843000</UpdateTimestamp>
        <CreateTimestamp>1514466483000</CreateTimestamp>
        <RecordCount>2</RecordCount>
        <IsPtr>true</IsPtr>
        <ZoneType>CLOUD_PRODUCT_ZONE</ZoneType>
        <Remark>test</Remark>
        <ResourceTags>
            <ResourceTag>
                <Value>daily</Value>
                <Key>env</Key>
            </ResourceTag>
        </ResourceTags>
    </Zone>
</Zones>
```

`JSON`格式

```
{
    "PageSize": "20",
    "RequestId": "6856BCF6-11D6-4D7E-AC53-FD579933522B",
    "PageNumber": "1",
    "TotalPages": "3",
    "TotalItems": "3",
    "Zones": {
        "Zone": [
            {
                "ZoneName": "test.com",
                "ResourceGroupId": "rg-xxxxx",
                "ZoneId": "ICAgICAgI_24",
                "ProxyPattern": "ZONE",
                "ZoneTag": "BLINK",
                "CreateTime": "2017-12-28T13:08Z",
                "UpdateTime": "2018-01-03T08:57Z",
                "UpdateTimestamp": "1514969843000",
                "CreateTimestamp": "1514466483000",
                "RecordCount": "2",
                "IsPtr": "true",
                "ZoneType": "CLOUD_PRODUCT_ZONE",
                "Remark": "test",
                "ResourceTags": {
                    "ResourceTag": [
                        {
                            "Value": "daily",
                            "Key": "env"
                        }
                    ]
                }
            }
        ]
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

