Create a PrivateZone pay-as-you-go instance 
================================================================



API operation 
----------------------------------

[CreateInstance](https://www.alibabacloud.com/help/zh/doc-detail/91835.htm?spm=a2c63.l28256.b99.42.18303fd5WUR7Xh)

Request parameters 
---------------------------------------



|     Parameter     |  Type  | Required |                                 Description                                  |  Valid value  |
|-------------------|--------|----------|------------------------------------------------------------------------------|---------------|
| ProductCode       | String | Yes      | The service code.                                                            | pvtz          |
| ProductType       | String | Yes      | The service type.                                                            | pvtzpost      |
| SubscriptionType  | String | Yes      | The billing method.                                                          | PayAsYouGo    |
| Parameter.1.Code  | String | Yes      | The code of the first parameter. CommodityType indicates the commodity type. | CommodityType |
| Parameter.1.Value | String | Yes      | The value of the first parameter.                                            | pvtz          |



Sample requests 
------------------------------------

    https://business.aliyuncs.com/? Action=CreateInstance
    &ProductCode=pvtz
    &ProductType=pvtzpost
    &SubscriptionType=PayAsYouGo
    &Parameter.1.Code=CommodityType
    &Parameter.1.Value=pvtz



