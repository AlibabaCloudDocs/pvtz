Resolver 
=============================





Overview 
--------------------------

The Resolver feature of Alibaba Cloud DNS PrivateZone allows you to create domain name-based forwarding rules and Domain Name System (DNS) outbound endpoints. For DNS requests that are sent within private zones associated with virtual private clouds (VPCs), you can use the created rules and endpoints to forward the requests to a third-party DNS or a on-premises DNS. This ensures that services deployed in a data center, an Alibaba Cloud VPC, and a hybrid cloud environment can access each other by using domain names.

Supported regions 
--------------------------------------

The Resolver feature is available in the following regions: China (Beijing), China (Shenzhen), China (Shanghai), , China (Hangzhou), China (Zhangjiakou), China（Huhehaote）、 China (Hong Kong)、USA（Virginia），a total of 8 public cloud Regions；2 Financial Cloud Regions in Shanghai and Shenzhen.

Procedure 
---------------------------

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5140975161/p249615.png) 
---------------------------------------------------------------------------------------------------------------------

Manage outbound endpoints 
----------------------------------------------

1. Create an outbound endpoint {#82HKN}
---------------------------------------

1. Log on to the [Alibaba Cloud DNS console](https://dc.console.aliyun.com/dns/). In the left-side navigation pane, click **PrivateZone** .

   

2. On the PrivateZone page, click the **Resolver** tab. On the **Resolver** tab, click **Outbound Endpoints** . Then, click **Create Outbound Endpoint** .

   




![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249616.png)

3. Configure the outbound endpoint.

   ![3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249617.png)
   




* Endpoint Name

  




The name of the outbound endpoint. Name the endpoint based on business requirements.

* Outbound VPC

  




The VPC where the outbound endpoint resides. The Resolver forwards all the outbound DNS requests for the specified VPC.
**Notice**



**(1) You cannot change the specified VPC after an outbound endpoint is created. This avoids the interruption of forwarding DNS requests caused by misoperations.** 

**(2)** **Please refer to "Supported Regions" above for the current open Regions.The Alibaba Cloud DNS team will provide more available regions in the future based on their priorities. If you need to deploy outbound endpoints in other regions,** [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.12818093.top-nav.dticket.6cb216d0lhCUgm#/ticket/list) **with a description of the required region.**

* Security Group

  




The security group that is associated with the VPC. The forwarding rules of the security group will be applied to the VPC.
**Note**

Only security groups not in managed mode are supported.

* Source IP Address of Outbound Traffic
  The IP addresses from which DNS requests are forwarded. Available IP addresses are those in subnets in the zones of the specified region. The IP addresses must not be occupied by Elastic Compute Service (ECS) instances. You must specify two to six IP addresses for the outbound endpoint to guarantee high availability. We recommend that you specify the IP addresses in different zones.

  **Notice**

  **If you do not specify IP addresses, the system automatically allocates IP addresses for the outbound endpoint.**
  




4. Click **Confirm** . If the PrivateZone feature assumes no RAM role, a RAM role will be created for the feature.

   




**Note: The following message appears each time you create an outbound endpoint. If the RAM role exists, no RAM role will be created for PrivateZone.** 

![11](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249620.png)

5. View the created outbound endpoint on the Outbound Endpoints page. You can view the status of each endpoint on this page. An endpoint may be in the following states: Normal, Creating, Failed, Being Modified, Modification Failed, and Abnormal.

   **Notice**

   

   **(1) It takes about 5 to 10 minutes to create an endpoint. If the status is Creating, wait patiently.** 

   **(2) You cannot modify or delete an outbound endpoint that is in the Creating state. If the status is Abnormal or Modification Failed,** [submit a ticket](https://workorder-intl.console.aliyun.com/?spm=5176.12818093.top-nav.dticket.6cb216d0lhCUgm#/ticket/list) **to troubleshoot the issue.**
   




![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249621.png)

2. Modify an outbound endpoint {#HNFhx}
---------------------------------------

1. Log on to the [Alibaba Cloud DNS console](https://dc.console.aliyun.com/dns/). In the left-side navigation pane, click **PrivateZone** .

   

2. On the PrivateZone page, click the **Resolver** tab. On the **Resolver** tab, click **Outbound Endpoints** . On the page that appears, find the outbound endpoint and click **Edit** . Modify the Endpoint Name and Source IP Address of Outbound Traffic parameters.

   




![123](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249624.png)

3. Click Confirm. After you modify an outbound endpoint, the endpoint enters the Being Modified state and you cannot modify or delete the endpoint when it is in the state.

   




![321](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249626.png)



3. Delete an outbound endpoint {#ZXJMu}
---------------------------------------

* 1. Log on to the [Alibaba Cloud DNS console](https://dc.console.aliyun.com/dns/). In the left-side navigation pane, click **PrivateZone** .




1. 2. On the PrivateZone page, click the **Resolver** tab. On the Resolver tab, click **Outbound Endpoints** . On the page that appears, find the outbound endpoint and click **Delete** .



* ![22](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249627.png)![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249628.png)

  

* ![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249630.png)

* ![4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249632.png)

* Specify a rule name based on your business requirements.

* You can set this parameter only to Forward to External DNS.

* The domain name that requires DNS request forwarding.

* The outbound endpoint used to forward DNS requests to the specified IP addresses.

* The IP address and port of the third-party DNS to which DNS requests are forwarded. You can specify up to six pairs of IP addresses and ports.

* 4. Click Confirm. The created forwarding rule appears on the Forwarding Rules page.

* ![1233331233](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6140975161/p249634.png)

* ![555](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249636.png)

* ![1244](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249637.png)![22222222](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249638.png)

* ![123](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249639.png)

* ![122](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249640.png)

* After you create a forwarding rule, you must associate the forwarding rule with a VPC to enable the rule in the VPC.

* ![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249642.png)![2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249644.png)

* ![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249646.png)

* Perform these steps to disassociate a forwarding rule from a VPC:

* 1. In the forwarding rule list, find the forwarding rule and click Bind VPC in the Actions column.

* ![123](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249647.png)

* 2. In the Bind VPC pane, remove the VPC from the associated VPC list and click Confirm.

* ![9099](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7140975161/p249649.png)


