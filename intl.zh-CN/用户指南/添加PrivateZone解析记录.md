添加PrivateZone解析记录 
======================================

在添加一个Zone以后，您需要先为其设置相应PrivateZone解析记录，然后才能将这个Zone关联到VPC。Zone关联VPC以后，在VPC环境内，Zone的PrivateZone记录会覆盖其公网解析记录。

在添加一个Zone以后，您需要先为其设置相应PrivateZone解析记录，然后才能将这个Zone关联到VPC。Zone关联VPC以后，在VPC环境内，Zone的PrivateZone记录会覆盖其公网解析记录。

**操作步骤** 

参照以下步骤来为Zone添加PrivateZone解析记录：

1. 登录到 [云解析DNS控制台](https://dc.console.aliyun.com/dns/)，并前往 **PriviteZone** 页面。

   

2. 找到需要配置PrivateZone解析记录的Zone，并单击其名称，进入解析设置控制台。

   

3. 在 **解析设置** 页面，单击 **添加记录** 为该Zone（私有域名）添加PrivateZone解析记录。

   ![添加记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242781.png)

   关于PrivateZone解析记录支持的记录类型及使用说明，请参考 [PrivateZone解析记录支持的记录类型](~~64634~~)。
   




**示例** 

**A记录** 

参照下图配置，为PrivateZone解析添加一条 **A** 记录。

![添加A记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242782.png)

**CNAME记录** 

参照下图配置，为PrivateZone解析添加一条 **CNAME** 记录。

![添加CNAME记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242783.png)

**注意** ：相同主机记录的CNAME记录只能添加一条，且不能与其他任何记录共存。

**MX记录** 

参照下图配置，为PrivateZone解析添加一条 **MX** 记录。

![添加MX记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242784.png)

**TXT记录** 

参照下图配置，为PrivateZone解析添加一条 **TXT** 记录。

![添加TXT记录](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242785.png)

**PTR记录** 

添加PTR记录前需要先配置反解Zone，具体操作请参考 [反向解析及PTR记录](~~64638~~)。



**SRV记录** 

SRV 记录用来标识某台服务器使用了某个服务，常见于微软系统的目录管理。

* 记录类型： 选择 **SRV** 。

  

* 主机记录： 格式为 **服务的名字.协议的类型** 。

  例如：_sip._tcp
  

* 记录值：格式为 **优先级 权重 端口 目标地址** ，每项中间需以空格分隔。

  例如：0 5 5060 sipserver.example.com
  

* TTL：为缓存时间，数值越小，修改记录各地生效时间越快，默认为 **60秒** 。

  




![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/7972704161/p242788.png)
