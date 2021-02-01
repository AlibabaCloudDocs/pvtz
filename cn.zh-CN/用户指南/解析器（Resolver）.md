解析器（Resolver） 
==================================





概述 
--------------------

解析器（Resolver）通过创建域名转发规则和DNS出站终端节点，可将阿里云vpc下PrivateZone 的dns请求流量转发到外部DNS系统，能够有效解决混合云、云上\&云下的业务间调用场景。

[试用说明](https://help.aliyun.com/document_detail/179151.html)

开放地域 
-------------------------

目前解析器功能开放Region：北京、深圳、上海、上海金融云、杭州、张家口、香港。

操作流程 
----------------------

![p136500](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2302651161/p231913.png) 
---------------------------------------------------------------------------------------------------------------------------



出站终端节点 
---------------------------

一、创建出站终端节点 {#82HKN}
-------------------

1. 登录到 [云解析DNS控制台](https://dc.console.aliyun.com/dns/)，并前往 **PriviteZone** 页面。

   

2. 依次选择 **解析器** - **出站终端节点** - **创建出站终端节点** **，** 进行出站终端节点创建。

   




![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231896.png)

3. 出站终端节点创建配置。

   ![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5302512161/p237188.png)
   




* 终端节点名称

  




当前创建的终端节点名称，根据实际业务需求命名。

* 出站VPC

  




解析器所有出站的DNS查询流量都将经由此VPC进行流量转发。
**注意**



**（1）出站终端节点一旦创建，不允许修改"出站VPC"，** **避免误操作造成线上流量中断。** 

**（2）目前新品试用期间仅开放北京** **区域节点，并同步正在收集其他Region的开放优先级。如需申请其他Region，请** **[提交工单](https://selfservice.console.aliyun.com/ticket/createIndex?spm=5176.2020520129.0.0.104746aeExF3rR)** **说明申请的Region。**

* 选择安全组

  




安全组里面的规则将应用于出站VPC。
**说明**

目前仅支持选择非托管安全组。[何为托管安全组？](https://help.aliyun.com/document_detail/188745.html?spm=a2c4g.11174283.6.898.709e52feYDfEo2)

* 出站流量源IP地址
  可用区域下子网中可用的IP地址（非ECS已占用IP地址）。为了保证高可用，解析器要求至少添加两个出站源IP地址，而且建议这2个IP地址分在不同的可用区，解析器允许添加的出站源IP地址最多为6个。

  **注意**

  **若不进行IP地址的输入，则系统自动分配。**
  




4. 点击 **确认 ，** 如果角色不存在 PrivateZone会创建一个服务关联角色。

   




**注：每次创建出站终端节点时，都会进行提示，但只有当角色不存在时才会创建。** 

![角色创建](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2724651161/p231917.png)

5. 出站终端节点列表会展示刚创建的节点及已经创建完成的节点。其中出站终端节点的状态包括："正常"、"创建中"、"创建失败"、"修改中"、"修改失败"、"异常"。

   **注意**

   

   **（1）创建终端节点，约需等待5-10分钟，如状态在"创建中"时，请耐心等待即可。** 

   **（2）"创建中"的节点不允许修改和删除。如状态提示"异常"、"修改失败"，请** **[提交工单](https://selfservice.console.aliyun.com/ticket/createIndex?spm=5176.2020520129.0.0.104746aeExF3rR)** **排查与处理。**
   




![异常截图](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/2724651161/p231919.png)



二、修改出站终端节点 {#HNFhx}
-------------------

1. 登录到 [云解析DNS控制台](https://dc.console.aliyun.com/dns/)，并前往 **PriviteZone** 页面。

   

2. 依次选择 **解析器** - **出站终端节点，** 点击终端节点后面的 **修改** ，对"终端节点名称"及"出站流量源IP地址"进行修改 **。**

   




![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231897.png)

3. 修改完，点击确认后，列表中的终端节点状态会变更为"修改中"，且无法进行修改及删除。

   




![4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231898.png)



三、删除出站终端节点 {#ZXJMu}
-------------------

* 1.登录到 [云解析DNS控制台](https://dc.console.aliyun.com/dns/)，并前往 **PriviteZone** 页面。




1. 2.依次选择 **解析器** - **出站终端节点，** 点击终端节点后面的 **删除** 。



* ![6](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231899.png)

  

* ![8](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231900.png)

* ![11](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231901.png)

* 根据业务需要及业务含义进行规则命名。

* 目前仅支持选择"转发至外部DNS系统"。

* 填写需要转发解析请求的Zone名称。

* 使用该出站终端节点将DNS查询流量转发到目标IP地址列表中指定的IP地址。

* DNS查询流量被转发的目标服务器的IP地址和端口。（最多只能创建6个）

* 4. 配置完毕点击确认后，在转发规则列表中会生成一条转发规则。

* ![9](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231902.png)

* ![22](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231903.png)

* ![33](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231904.png)

* ![333](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231905.png)

* ![55](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231906.png)

* 创建完 **转发规则** 后，需要进行 **VPC关联** ，转发规则才能对VPC内生效。

* ![1111](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/3302651161/p231907.png)![2212](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4302651161/p231908.png)![1231](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4302651161/p231909.png)

* 若要进行取消VPC关联，请参考以下步骤：

* 1.单击已经关联VPC的转发规则后方的"关联VPC"操作按钮。

* ![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5635651161/p231975.png)

* 2.在关联VPC配置页面，删除已经关联的VPC，并单击确认。

* ![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/5635651161/p231977.png)


