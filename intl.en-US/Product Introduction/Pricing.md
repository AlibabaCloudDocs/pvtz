Pricing 
============================



Billing method 
-----------------------------------

Alibaba Cloud DNS PrivateZone supports the pay-as-you-go billing method. You are billed by **the number of private zones that you create and the number of back-to-origin requests in each zone** . Bills are generated and settled on a daily basis. If you delete a private zone within the same day you create the zone, you are not charged.

Billing rules 
----------------------------------



|                       Billing item                        |              Price               |                                                                                  Description                                                                                   |
|-----------------------------------------------------------|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Number of private zones                                   | USD 0.015 per zone per day       | Each zone in an account is charged USD 0.015 per day.                                                                                                                          |
| Number of back-to-origin requests in each zone            | USD 0.004 per 10,000 requests    | You are charged USD 0.004 for every 10,000 back-to-origin requests that the DNS server processes each day in an account after the specified time to live (TTL) period expires. |
| Source IP address of an outbound endpoint                 | USD 0.15 per hour per IP address | Each source IP address of an outbound endpoint in an account is charged USD 0.15 per hour.                                                                                     |
| Number of DNS requests that an outbound endpoint forwards | USD 0.004 per 10,000 requests    | You are charged USD 0.004 for every 10,000 DNS requests that an outbound endpoint forwards in an account.                                                                      |



Example 
----------------------------

* You create three private zones in Account A, namely, test.com, host01.demo.com, and inner.example.local.

  

*
  The DNS server receives 64,131 back-to-origin requests from the three private zones in Account A one day.

  

* Account A is charged USD 0.075 in total for that day, including USD 0.045 for the usage of the three private zones and USD 0.03 for resolving the back-to-origin requests. Specifically, the fee for resolving the requests is calculated in the following way: Divide 64,131 by 1,000. The result is 6.4131. Round 6.4131 to 6.41 and multiply the number by 0.004. The result is rounded to 0.03.

  





**Note**

TTL caching is used for DNS requests. In each zone, the number of billable back-to-origin requests per day is the number of requests minus the number of cache hits within the TTL period.

**Assume that the TTL for the domain name www.test.com is set to 30 seconds and 1,000 requests per second are sent to the DNS. Then, all requests within the TTL period are free of charge. The one request that is sent after the specified TTL period expires is billed. All subsequent requests that are sent within a new TTL period are free of charge.** 

**You can view the total number of back-to-origin requests on the Query Volume page in the Alibaba Cloud DNS console.** 
**Notice**



**Typically:** 

* **A longer TTL period leads to fewer back-to-origin requests and incurs lower charges. However, it takes longer for the change of an IP address for a domain name within the corresponding TTL period to take effect.**

  

* **A shorter TTL period leads to more back-to-origin requests and incurs higher charges. However, the change of an IP address for a domain name within the corresponding TTL period can take effect faster.**

  




Overdue bills 
----------------------------------

* The PrivateZone service is suspended 24 hours after you receive an overdue bill notice.

  

* The system stops billing when the PrivateZone service is suspended.
  Your PrivateZone service remains valid if you recharge your account within 24 hours after you receive an overdue bill notice.
  Your private zones are retained for seven days after you receive an overdue bill notice. After seven days, your private zones are automatically released unless you recharge your account before the seven-day grace period ends.

  

* You receive a message or an email notification one day before the private zones are released. The private zone configurations and data that have been released are permanently deleted and cannot be restored.

  

*
  If you recharge your account within seven days, the service automatically resumes.

  



