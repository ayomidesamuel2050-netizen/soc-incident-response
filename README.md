# SOC-INCIDENT-RESPONSE
A centralized repository for SOC operations, including monitoring, incident response, and security workflows.
--
**Total alert**
<img width="1495" height="485" alt="image" src="https://github.com/user-attachments/assets/3cfcadc5-1e8c-44d1-87e1-83acd62071e0" />

## Assinged alerts
1. 8816       Access to Blacklisted External URL Blocked by Firewall     

 I choose 8816 because its the one with an high severity

** Description** 

This alert was triggered when a user attempted to access an external URL that is listed in the organization's blacklist or threat intelligence feeds. The firewall or proxy successfully blocked the outbound request, preventing the connection. Note: The blacklist only covers known threats. It does not guarantee protection against new or unknown malicious domains.

### Lets open the alert in the splunk

Note:

SourceIP = 10.20.2.17
<img width="961" height="372" alt="image" src="https://github.com/user-attachments/assets/83b6ec97-1a70-42ad-849c-767af7ed5b27" />


URL = http://bit.ly/3sHkX3da12340
  <img width="1184" height="660" alt="image" src="https://github.com/user-attachments/assets/a2c6646b-3995-4575-8c6c-89fbe6d5fde6" />

This shows that the url is malicious

Action = blocked

timestamp:  03/24/2026 12:40:00.965

### lets give our case report

<img width="691" height="467" alt="image" src="https://github.com/user-attachments/assets/5924b291-f4a4-462f-8319-fb121aa2d6ee" />           <img width="653" height="97" alt="image" src="https://github.com/user-attachments/assets/7f29ed90-43eb-4759-9302-52f2f27fb43b" />

2. 







 
 

 

 
