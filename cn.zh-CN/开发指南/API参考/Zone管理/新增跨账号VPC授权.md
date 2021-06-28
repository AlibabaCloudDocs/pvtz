# 新增跨账号VPC授权

通过调用AddUserVpcAuthorization进行跨账号VPC授权。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=pvtz&api=AddUserVpcAuthorization&type=RPC&version=2018-01-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddUserVpcAuthorization|系统规定参数。取值：AddUserVpcAuthorization。 |
|AuthorizedUserId|Long|是|111222333|授权资源的所属用户主账号ID。 |
|AuthChannel|String|否|AUTH\_CODE|授权渠道，取值范围：

 -   AUTH\_CODE：验证码授权，验证AuthCode传入的验证码是否正确。
-   RESOURCE\_DIRECTORY: 资源目录授权，验证AuthorizedUserId与当前账户是否存在资源目录授信。
-   传空时，同AUTH\_CODE，即验证码授权。 |
|AuthCode|String|否|123456|验证码，AuthChannel取”AUTH\_CODE“或传空时为必传。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|46973D4C-E3E4-4ABA-9190-9A9DE406C7E|唯一请求识别码 |

## 示例

请求示例

```
http(s)://pvtz.aliyuncs.com/?Action=AddUserVpcAuthorization
&AuthorizedUserId=111222333
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>46973D4C-E3E4-4ABA-9190-9A9DE406C7E</RequestId>
```

`JSON`格式

```
{
    "RequestId":"46973D4C-E3E4-4ABA-9190-9A9DE406C7E"
    }
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/pvtz)查看更多错误码。

