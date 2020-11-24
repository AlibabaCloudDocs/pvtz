PrivateZone\&VPN网关联动实现云上访问云下资源 
===================================================



背景描述 
-------------------------

自建IDC和 阿里云VPC分别属于两套网络环境，但部署在自建IDC和阿里云VPC内的业务都需要通过DNS解析进行业务间调用，并且分别管理两套数据不仅给运维工程师带来重复性工作的增加，同时也会产生数据一致性管理的风险，给业务带来很高的不确定性，所以需要在自建IDC和阿里云VPC共享DNS解析数据，来实现业务间能实时调用。本文章将讲解如何实现云上PrivateZone访问云下DNS解析数据的方法。

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/8486909951/p161354.png)

解决方案 
-------------------------

实现云上访问云下资源，可以通过3种解决方案实现。本文则主要为您详细说明方案一：通过解析器实现云上访问云下资源 的操作步骤和验证方法。



（一）通过解析器实现云上访问云下资源

1.通过SAG/专线/VPN等连接方式，将云上VPC与传统数据中心互联。本示例采用IPsec-VPN隧道方式。

2.在云上通过PrivateZone的解析器功能，将转发请求直接Forward至线下自建DNS。

[解析器试用说明](https://www.alibabacloud.com/help/zh/doc-detail/179151.htm?spm=a2c63.l28256.b99.2.585950b7XwyFNZ)



（二）通过修改云上服务器的LocalDns实现云上访问云下资源

1.通过SAG/专线/VPN等连接方式，将云上VPC与传统数据中心互联。本示例采用IPsec-VPN隧道方式。

2.通过修改云上服务器的LocalDns，客户端发起直接向线下自建DNS服务器发起解析请求。

\[centos\]# vim /etc/resolv.conf

    #根据线下自建DNS实际IP修改下方nameserver
    nameserver 2.2.2.2
    nameserver 3.3.3.3





（三）通过辅助DNS实现云上访问云下资源

1.通过SAG/专线/VPN等连接方式，将云上VPC与传统数据中心互联。本示例采用IPsec-VPN隧道方式。

2.[辅助DNS](https://www.alibabacloud.com/)。通过辅助DNS将线下自建DNS的解析同步至云上进行解析。
**说明**



自建DNS建议使用Bind，目前辅助DNS对Windows DNS Server不提供完整支持。

通过解析器实现云上访问云下资源 
------------------------------------

**什么是解析器？** 

解析器（Resolver）通过创建域名转发规则和DNS出站终端节点，可将阿里云vpc下PrivateZone 的dns请求流量转发到外部DNS系统，能够有效解决混合云、云上\&云下的业务间调用场景。

**资源准备** 

1.使用阿里云服务器模拟线下IDC，然后通过Bind搭建自建DNS服务。

2.阿里云VPC侧VPN网关产品服务

3.云解析PrivateZone产品服务

**参考链接：** 

* [建立VPC到本地数据中心的连接](https://www.alibabacloud.com/help/zh/doc-detail/65072.htm)

  

* [本地网关配置](https://www.alibabacloud.com/help/zh/doc-detail/65372.htm)

  






**操作步骤** 

![12](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p143517.png)

**步骤一：创建VPN网关** 

完成以下操作，创建VPN网关。

1. 登录[专有网络管理控制台](https://vpc.console.aliyun.com/vpc/cn-hangzhou/vpcs) 。

2. 在左侧导航栏，单击 **VPN** **\>** **VPN网关** 。

3. 在 **VPN网关** 页面，单击 **创建VPN网关** 。

4. 在购买页面，根据以下信息配置VPN网关，然后单击 **立即购买** 完成支付。

5. 返回VPN网关页面，查看创建的VPN网关。本示例VPC公网IP为：x.x.x.217

   




刚创建好的VPN网关的状态是准备中，约两分钟左右会变成正常状态。正常状态表明VPN网关完成了初始化，可以正常使用了。

**步骤二：创建用户网关** 

完成以下操作，创建用户网关。

1. 在左侧导航栏，单击 **VPN** **\>** **用户网关** 。

2. 选择用户网关的地域。

   

3. 在 **用户网关** 页面，单击 **创建用户网关** 。

4. 在 **创建用户网关** 页面，根据以下信息配置用户网关，然后单击 **确定** 。






**步骤三：创建IPsec连接** 

完成以下操作，创建IPsec连接。

1. 在左侧导航栏，单击 **VPN** **\>** **IPsec连接** 。

2. 选择创建IPsec连接的地域。

   

3. 在 **IPsec连接** 页面，单击 **创建IPsec连接** 。

4. 在 **创建IPsec连接** 页面，根据以下信息配置IPsec连接，然后单击 **确定** 。






<!-- -->



<!-- -->



<!-- -->



<!-- -->



<!-- -->



<!-- -->





**步骤四：在本地网关设备中加载VPN配置** 

完成以下操作，在本地网关设备中加载VPN配置。

1. 在左侧导航栏，单击 **VPN** **\>** **IPsec连接** 。

2. 选择IPsec连接的地域。

   

3. 在 **IPsec连接** 页面，找到目标IPsec连接，然后单击 **操作** 列下的 **下载对端配置** 。

4. 根据本地网关设备的配置要求，将下载的配置添加到本地网关设备中。具体参考：

   [本地网关配置](https://www.alibabacloud.com/help/zh/doc-detail/65372.html) 。
   

5. 本示例采用的是Strongswan搭建IPsec-VPN服务，具体部署过程如下：

   




<!-- -->



(1).\[centos \~\]# vim /etc/strongswan/ipsec.conf

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
            keyexchange=ikev1   #ike版本
            authby=psk
    
    conn toMyIdc
          left=%defaultroute
          leftid=x.x.x.44    #本地IDC网关公网IP
          leftsubnet=172.28.0.0/16    #本地IDC私有网络地址，如果要确保VPC网段都能通，需要添加整段VPC地址
          right=x.x.x.152      #阿里云VPN网关公网IP
          rightid=x.x.x.152    #阿里云VPN网关公网IP
          rightsubnet=172.17.0.0/16     #阿里云VPN网关关联VPC私有网络地址
          auto=start   #进程主动时立即建立 IPsec 安全连接
          type=tunnel
          ike=3des-md5-modp1024
          esp=3des-md5



(2).运行以下命令打开ipsec.secrets配置文件。本示例配置仅供参考。

    [centos ~]# vi /etc/strongswan/ipsec.secrets
    # ipsec.secrets - strongSwan IPsec secrets file
    x.x.x.44 x.x.x.152 : PSK 1234567



(3)./etc/sysctl.conf系统配置。本示例配置仅供参考。

    [centos ~]# vim /etc/sysctl.conf
    
    #配置转发，默认是0
    net.ipv4.ip_forward = 1
    #关闭重定向，防止恶意用户可以使用IP重定向来修改远程主机中的路由表
    net.ipv4.conf.all.accept_redirects = 0
    net.ipv4.conf.all.send_redirects = 0
    
    #使配置生效
    [centos ~]# sysctl -p



c.启动Strongswan服务

\[centos \~\]# systemctl start strongswan.service



d.添加路由，本示例直接在界面化添加。

在IDC核心网关上添加到对端172.17.0.0/16的路由，下一跳指向strongswan的IP 172.28.0.7。

![image.png](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139980.png "image.png")

**步骤五：配置VPN网关路由** 

完成以下操作，配置VPN网关路由。

1. 在左侧导航栏，单击 **VPN** **\>** **VPN网关** 。

2. 选择VPN网关的地域。

   

3. 在 **VPN网关** 页面，找到目标VPN网关，单击 **实例ID/名称** 列下的实例ID。

4. 在 **目的路由表** 页签，单击 **添加路由条目** 。

5. 在 **添加路由条目** 页面，根据以下信息配置目的路由，然后单击 **确定** 。








**步骤六：测试网络访问** 

登录到阿里云VPC内一台无公网IP的ECS实例，并通过 **ping** 命令 **ping** 本地数据中心内一台服务器的私网IP地址，验证通信是否正常。

**步骤七：搭建自建DNS服务** 

1.安装Bind：\[centos \~\]# yum install -y \*bind

2.配置named.conf：\[centos \~\]# vim /etc/named.conf。本示例配置仅供参考。

    zone "alidns-example.com" IN {
            type master;
            file "alidns-example.com.zone";
            allow-update {127.0.0.1; };
    };



3.配置alidns-example.com.zone：\[centos \~\]# vim /var/named/alidns-example.com.zone。本示例配置仅供参考。

    $TTL 3600
    @       IN SOA  172.28.0.7. admin.alidns-example.com. (
                                            8       ; serial
                                            1D      ; refresh
                                            1H      ; retry
                                            1W      ; expire
                                            3H )    ; minimum
    @       IN      NS      172.28.0.7.
    @       IN      A       15.15.15.15



4.启动Bind：\[centos \~\]# systemctl start named.service。



**步骤八：解析器（Resolver）配置** 

具体配置链接可以参考：[解析器（Resolver）](https://www.alibabacloud.com/help/zh/doc-detail/177601.html)



一.创建出站终端节点

完成以下操作，配置出站终端节点。

1.[登录云解析控制台](https://dns.console.aliyun.com/)\> **PrivateZone** \>解析器\>出站终端节点\>创建出站终端节点。

![image.png](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139981.png "image.png")

2.在创建出站终端节点页面，根据以下信息进行配置，然后点击确定。

* 终端节点名称：输入终端节点名称。本示例采用Test。

  

* 出站VPC：解析器所有出站的DNS查询流量都将由此VPC进行流量转发。本示例选取北京Region下的vpc。

  

* 选择安全组：安全组里面的规则将应用于出站VPC。本示例进行了TCP/UDP 53端口入站/出站开放。

  **说明**

  目前仅支持选择非托管安全组。
  

* 出站流量源IP地址：选择并填入可用区内子网下的IP地址（非ECS已占用IP地址）。

  




![image.png](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139982.png "image.png")

二、创建转发规则

1.切换到转发规则页面，并根据以下信息进行配置转发规则，然后点击确定。

* 规则名称：输入规则名称。本示例采用Test。

  

* 规则类型：目前仅可选择"转发至外部DNS系统"。

  

* 转发Zone：填入您需要转发查询的Zone名称。本示例为：alidns-example.com。

  

* 出站终端节点：选择已经创建好的出站终端节点。本示例为上一步创建的出站终端节点Test。

  

* 外部DNS系统的IP地址和端口：线下IDC中自建DNS服务器的IP地址与端口号。本示例为：172.28.0.7:53

  **注意**

  

  若您填写的自建DNS服务器为公网IP，且您出站终端节点VPC内ECS无公网IP，请开通 [NAT网关](https://www.alibabacloud.com/help/zh/doc-detail/32322.htm) 并配置 [SNAT功能](https://www.alibabacloud.com/help/zh/doc-detail/65202.htm)。
  




![image.png](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139983.png "image.png")

三、关联VPC

1.选择要进行VPC关联的转发规则，点击关联VPC，进行VPC绑定。（需要与出站终端节点的VPC一致）。支持 [跨账号关联VPC](https://www.alibabacloud.com/help/zh/doc-detail/146483.htm?spm=a2c63.p38356.b99.25.5d2a1832sAqfEQ)

![image.png](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139984.png "image.png")

**步骤九：解析测试** 

1.登录关联VPC内的任一Ecs进行以下命令测试：

\[centos \~\]# dig alidns-example.com

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/9486909951/p139986.png)

