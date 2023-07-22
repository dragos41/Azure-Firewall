# Create a Windows virtual machine in the Azure portal
## Step 1: Firewall deployment 
##### 1. Sign into your Azure subscription from this link: https://portal.azure.com/
##### 2. On the Azure home page, select Firewalls under the Azure services bar.
##### 3. Select on Create Firewall.
##### 4. Subscription: Select your subscription.
##### 5. Resource group: Select the Firewall resource group from the dropdown, created in the earlier activity.
##### 6. Give the firewall instance the name ScoopsFirewall.
##### 7. Region: Select the same location that you have used previously.
##### 8. Firewall SKU: Select Standard from the Firewall SKU selection boxes.
##### 9. For firewall management, select Use Firewall rules (classic) to manage this firewall.
##### 10. For Choose a virtual network select Use existing and select the Firewall-Hub network for the virtual network created in a previous activity.
##### 11. IP address: For the Public IP address select Add new and give it the name FirewallScoops, select OK.
##### 12. Select Review + create. The firewall will now be deployed.
## Step 2: Firewall application rule creation
##### 1. Open the  Firewall resource group, and select the  ScoopsFirewall firewall.
##### 2. On the ScoopsFirewall page, under  Settings, select  Rules (classic).
##### 3. Select the  Application rule collection tab.
##### 4. Select  Add application rule collection.
##### 5. For  Name, type  AppRule1.
##### 6. For  Priority, type  200.
##### 7. For  Action, select  Allow.
##### 8. Under  Rules, Target FQDNs, for  Name, type  Allow-Google
##### 9. For  Source type, select  IP address.
##### 10. Type  172.16.1.0/24 for the  Source.
##### 11. For  Protocol:port, type http, https.
##### 12. For  Target FQDNS, type  www.google.com
##### 13. Select  Add and after a while the rule will be created
## Step 3: Firewall network rule creation
##### 1. Select the  Network rule collection  tab.
##### 2. Select  Add network rule collection.
##### 3. For  Name, type  Net-Rule1.
##### 4. For  Priority, type  200.
##### 5. For  Action, select  Allow.
##### 6. Under  Rules, IP addresses, for  Name, type  Allow-DNS.
##### 7. For  Protocol, select  UDP.
##### 8. For  Source type, select  IP address.
##### 9. Type  172.16.1.0/24 for the Source.
##### 10. For  Destination type  select  IP address.
##### 11. For  Destination address, type  209.244.0.3,209.244.0.4 (These are public DNS servers operated by Level 3)
##### 12. For  Destination Ports, type  53
##### 13. Select  Add.

Step 4: Firewall NAT rules creation
##### Select the  NAT rule collection  tab.

##### Select  Add NAT rule collection.

##### For  Name, type  rdp.

##### For  Priority, type  200.

##### Under  Rules, for  Name, type  rdp-nat.

##### For  Protocol, select  TCP.

##### For  Source type, select  IP address.

##### Type  *.(* = anything) for the Source.

##### For  Destination address, type the firewall public IP address.

##### For  Destination Ports, type  3389.

##### For  Translated address, type the  SamScoopsWeb  virtual machine's private IP address.

##### For  Translated port, type  3389.

##### Select  Add.

## Step 5: Advanced threat protection

##### On the  ScoopsFirewall  page, under  Settings, select  Threat Intelligence.

##### For Threat Intel mode select  Alert and deny.

##### Select Save.
