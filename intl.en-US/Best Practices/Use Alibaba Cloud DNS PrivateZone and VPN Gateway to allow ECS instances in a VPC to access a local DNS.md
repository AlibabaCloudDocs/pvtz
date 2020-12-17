Use Alibaba Cloud DNS PrivateZone and VPN Gateway to allow ECS instances in a VPC to access a local DNS 
============================================================================================================================



Scenario 
-----------------------------

An enterprise runs services in two isolated network environments, including a local data center and an Alibaba Cloud virtual private cloud (VPC). The enterprise needs to access services between the local data center and VPC by using Domain Name System (DNS) resolution. If operations and maintenance (O\&M) engineers of the enterprise manage a separate set of DNS data for each network environment, they must perform a lot of repetitive work and face the high risk of data inconsistency and service instability. Therefore, O\&M engineers need to share DNS data between the local data center and VPC to allow real-time access between services. This topic describes how to use Alibaba Cloud DNS PrivateZone and Virtual Private Cloud (VPN) Gateway to allow Elastic Compute Service (ECS) instances in a VPC to access a local DNS.

![architecture](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3890718061/p201715.png)

Solutions 
------------------------------

In this topic, three solutions are available to allow ECS instances in a VPC to access a local DNS. This topic describes the configuration procedure and verification method of solution 1 in detail.



Solution 1: Use the Resolver feature of Alibaba Cloud DNS PrivateZone to allow ECS instances in a VPC to access a local DNS

1. Connect the VPC to the local data center by using a smart access gateway (SAG), an Express Connect circuit, or a virtual private network (VPN). For example, you can use an IPsec-VPN connection to connect the VPC to the local data center.

2. Use the Resolver feature of Alibaba Cloud DNS PrivateZone to forward DNS requests of ECS instances in the VPC to the local DNS.

The Resolver feature is free for trial use. For more information, see [Trial of Resolver](https://www.alibabacloud.com/help/zh/doc-detail/179151.htm?spm=a2c63.l28256.b99.2.585950b7XwyFNZ).



Solution 2: Modify the DNS server information on ECS instances in a VPC to allow the ECS instances to access a local DNS

1. Connect the VPC to the local data center by using an SAG, an Express Connect circuit, or a VPN. For example, you can use an IPsec-VPN connection to connect the VPC to the local data center.

2. Modify the DNS server information on ECS instances in the VPC. Then, the ECS instances can send DNS requests to the local DNS.

\[centos\]# vim /etc/resolv.conf

    # Change the nameserver values to the IP addresses of the local DNS.
    nameserver 2.2.2.2
    nameserver 3.3.3.3





Solution 3: Use the Secondary DNS feature of Alibaba Cloud DNS PrivateZone to allow ECS instances in a VPC to access a local DNS

1. Connect the VPC to the local data center by using an SAG, an Express Connect circuit, or a VPN. For example, you can use an IPsec-VPN connection to connect the VPC to the local data center.

2. Configure a secondary DNS. For more information, see [Secondary DNS](https://www.alibabacloud.com/). You can synchronize DNS data from the local DNS to the secondary DNS to resolve domain names.
**Note**



We recommend that you use Berkeley Internet Name Domain (BIND) to build the local DNS. The Secondary DNS feature does not provide full support for Windows DNS Server.

Use the Resolver feature of Alibaba Cloud DNS PrivateZone to allow ECS instances in a VPC to access a local DNS 
------------------------------------------------------------------------------------------------------------------------------------

**What is Resolver?** 

The Resolver feature of Alibaba Cloud DNS PrivateZone allows you to create domain name-based forwarding rules and DNS outbound endpoints. For DNS requests that are sent within private zones associated with VPCs, you can use the created rules and endpoints to forward the requests to a third-party DNS. This ensures that services deployed in a local data center, an Alibaba Cloud VPC, and a hybrid cloud environment can access each other by using domain names.

**Preparations** 

1. Use Alibaba Cloud ECS instances to simulate a local data center. Then, use BIND to build a local DNS.

2. Create a VPC.

3. Activate Alibaba Cloud DNS PrivateZone.

**References** 

* [Connect on-premises data centers to VPC networks](https://www.alibabacloud.com/help/zh/doc-detail/65072.htm)

  

* [Configure local gateways](https://www.alibabacloud.com/help/zh/doc-detail/65372.htm)

  






**Procedure** 

![12](../images/p143517.png)

**Step 1: Create a VPN gateway** 

To create a VPN gateway, perform the following steps:

1. Log on to the [VPC console](https://vpc.console.aliyun.com/vpc/cn-hangzhou/vpcs).

2. In the left-side navigation pane, choose **VPN** **\>** **VPN Gateways** .

3. On the **VPN Gateways** page, click **Create VPN Gateway** .

4. On the page that appears, set the parameters for creating a VPN gateway, click **Buy Now** , and then complete the payment.

5. On the VPN Gateways page, view the created VPN gateway. In this example, the public IP address of the VPN gateway that is associated with the VPC is x.x.x.217.

   




The status of a newly created VPN gateway is Preparing and then changes to Normal after about 2 minutes. After the status changes to Normal, the VPN gateway is ready to use.

**Step 2: Create a customer gateway** 

To create a customer gateway, perform the following steps:

1. In the left-side navigation pane, choose **VPN** **\>** **Customer Gateways** .

2. Select the region where the customer gateway resides.

   

3. On the **Customer Gateways** page, click **Create Customer Gateway** .

4. On the **Create Customer Gateway** page, set the parameters for creating a customer gateway and click **Submit** .






**Step 3: Create an IPsec-VPN connection** 

To create an IPsec-VPN connection, perform the following steps:

1. In the left-side navigation pane, choose **VPN** **\>** **IPsec Connections** .

2. Select the region where the IPsec-VPN connection resides.

   

3. On the **IPsec Connections** page, click **Create IPsec Connection** .

4. On the **Create IPsec Connection** page, set the parameters for creating an IPsec-VPN connection and click **Submit** .






<!-- -->



<!-- -->



<!-- -->



<!-- -->



<!-- -->



<!-- -->





**Step 4: Load the configurations of the IPsec-VPN connection to the gateway deployed in the local data center** 

To load the configurations of the IPsec-VPN connection to the gateway deployed in the local data center, perform the following steps:

1. In the left-side navigation pane, choose **VPN** **\>** **IPsec Connections** .

2. Select the region where the IPsec-VPC connection resides.

   

3. On the **IPsec Connections** page, find the target IPsec-VPN connection and choose **More** \> **Download Configuration** in the Actions column.

4. Load the configurations of the IPsec-VPN connection to the gateway deployed in the local data center. For more information, see

   [Configure local gateways](https://www.alibabacloud.com/help/zh/doc-detail/65372.html).
   

5. In this example, strongSwan is used to establish the IPsec-VPN connection. To deploy strongSwan, perform the following steps:

   




<!-- -->



(1) \[centos \~\]# vim /etc/strongswan/ipsec.conf

    # ipsec.conf - strongSwan IPsec configuration file
    # basic configuration
    
    config setup
        # strictcrlpolicy=yes
        uniqueids = never
    
    conn %default
            ikelifetime=1440m   
            keylife=60m
            rekeymargin=3m
            keyingtries=0
            keyexchange=ikev1   # The IKE version.
            authby=psk
    
    conn toMyIdc
          left=%defaultroute
          leftid=x.x.x.44    # The public IP address of the gateway deployed in the local data center.
          leftsubnet=172.28.0.0/16    # The CIDR block of the local data center. To ensure that the IPsec-VPN connection is available to all devices in the local data center, you must specify the CIDR block of the local center with this parameter.
          right=x.x.x.152      # The public IP address of the VPN gateway.
          rightid=x.x.x.152    # The public IP address of the VPN gateway.
          rightsubnet=172.17.0.0/16     # The CIDR block of the VPC with which the VPN gateway is associated.
          auto=start   # Load the connection immediately at the IPsec startup.
          type=tunnel
          ike=3des-md5-modp1024
          esp=3des-md5



(2) Configure the ipsec.secrets file. The configurations in this example are for reference only.

    [centos ~]# vi /etc/strongswan/ipsec.secrets
    # ipsec.secrets - strongSwan IPsec secrets file
    x.x.x.44 x.x.x.152 : PSK 1234567



(3) Configure the ./etc/sysctl.conf file. The configurations in this example are for reference only.

    [centos ~]# vim /etc/sysctl.conf
    
    # Enable forwarding of IPv4 packets. Default value: 0.
    net.ipv4.ip_forward = 1
    # Disable accepting and sending of IPv4 redirected packets. This prevents malicious users from modifying the route table on a remote host by using IP redirects.
    net.ipv4.conf.all.accept_redirects = 0
    net.ipv4.conf.all.send_redirects = 0
    
    # Make the configurations take effect.
    [centos ~]# sysctl -p



c. Start strongSwan.

\[centos \~\]# systemctl start strongswan.service



d. Add a route. In this example, the route is added on the GUI.

On the GUI of the gateway deployed in the local data center, add the route for sending traffic to 172.17.0.0/16. The next-hop address is set to the strongSwan IP address 172.28.0.7.

![image.png](../images/p139980.png "image.png")

**Step 5: Configure routes for the VPN gateway** 

To configure routes for the VPN gateway, perform the following steps:

1. In the left-side navigation pane, choose **VPN** **\>** **VPN Gateways** .

2. Select the region where the VPN gateway resides.

   

3. On the **VPN Gateways** page, find the target VPN gateway and click the instance ID in the **Instance ID/Name** column.

4. On the **Destination-based routing** tab, click **Add Route Entry** .

5. In the **Add Route Entry** dialog box, set the parameters for adding a route entry and click **OK** .








**Step 6: Verify the settings** 

Log on to an ECS instance that is not assigned a public IP address in the VPC. Run the **ping** command to ping the private IP address of a server that resides in the local data center, and test the connectivity.

**Step 7: Build the local DNS** 

1. Run the yum install -y \*bind command to install BIND.

2. Run the vim /etc/named.conf command to open the named.conf file and configure the file. The configurations in this example are for reference only.

    zone "alidns-example.com" IN {
            type master;
            file "alidns-example.com.zone";
            allow-update {127.0.0.1; };
    };



3. Run the vim /var/name d/alidns-example.com.zone command to open the alidns-example.com.zone file and configure the file. The configurations in this example are for reference only.

    $TTL 3600
    @       IN SOA  172.28.0.7. admin.alidns-example.com. (
                                            8       ; serial
                                            1D      ; refresh
                                            1H      ; retry
                                            1W      ; expire
                                            3H )    ; minimum
    @       IN      NS      172.28.0.7.
    @       IN      A       15.15.15.15



4. Run the systemctl start named.service command to start BIND.



**Step 8: Configure Resolver** 

For more information, see [Use the Resolver feature](https://www.alibabacloud.com/help/zh/doc-detail/177601.html).



1. Create an outbound endpoint.

To create an outbound endpoint, perform the following steps:

(1) Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/). In the left-side navigation pane, click **PrivateZone** . On the PrivateZone page, click the Resolver tab. On the Resolver tab, click Outbound Endpoints on the left. On the page that appears, click Create Outbound Endpoint.

![image.png](../images/p139981.png "image.png")

(2) In the Create Outbound Endpoint dialog box, set the parameters as required.

* Endpoint Name: Enter a name for the outbound endpoint. In this example, enter Test.

  

* Outbound VPC: Select the VPC where the outbound endpoint resides. Resolver forwards all the outbound DNS requests for the specified VPC. In this example, select the VPC in the China (Beijing) region.

  

* Security Group: Select a security group that is associated with the VPC. The forwarding rules of the security group are applied to the VPC. In this example, inbound and outbound traffic through TCP or UDP port 53 is allowed.

  

* Source IP Address of Outbound Traffic: Set the IP addresses from which DNS requests are forwarded. Available IP addresses are those in subnets in the zones of the specified region. The IP addresses must not be occupied by ECS instances.

  




![image.png](../images/p139982.png "image.png")

2. Create a forwarding rule.

On the Resolver tab, click Forwarding Rules on the left. On the page that appears, click Create Forwarding Rule. In the Create Forwarding Rule dialog box, set the parameters as required.

* Rule Name: Enter a name for the forwarding rule. In this example, enter Test.

  

* Rule Type: Set the type of the forwarding rule. You can set this parameter only to Forward to External DNS.

  

* Forwarding Zone: Enter the domain name for which DNS requests need to be forwarded. In this example, enter alidns-example.com.

  

* Outbound Endpoint: Select the outbound endpoint used to forward DNS requests. In this example, select the outbound endpoint Test that is created in the previous step.

  

* IP Address and Port of External DNS: Enter the IP address and port number of the DNS server in the local data center to which DNS requests are forwarded. In this example, set the IP address to 172.28.0.7 and port number to 53.

  **Notice**

  

  If you enter a public IP address, but the ECS instances in the VPC where the outbound endpoint resides do not have public IP addresses, you must activate [NAT Gateway](https://www.alibabacloud.com/help/zh/doc-detail/32322.htm) and configure the [SNAT feature](https://www.alibabacloud.com/help/zh/doc-detail/65202.htm).
  




![image.png](../images/p139983.png "image.png")

3. Associate the forwarding rule with the VPC where the outbound endpoint resides.

Find the target forwarding rule and click Bind VPC in the Actions column. Select the VPC where the outbound endpoint resides and click Confirm. Resolver allows you to associate a forwarding rule with a VPC that belongs to another Alibaba Cloud account. For more information, see [Associate VPC across accounts](https://www.alibabacloud.com/help/zh/doc-detail/146483.htm?spm=a2c63.p38356.b99.25.5d2a1832sAqfEQ).

![image.png](../images/p139984.png "image.png")

**Step 9: Verify DNS resolution** 

Log on to an ECS instance in the VPC, run the following command, and then check whether the domain name is resolved as expected.

\[centos \~\]# dig alidns-example.com

![1](../images/p139986.png)

