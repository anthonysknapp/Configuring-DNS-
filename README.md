![image](https://github.com/anthonysknapp/Configuring-DNS-/assets/148372256/3956af6c-d39e-463d-af4d-3123cdb28b57)<h1> Configuring DNS</h1>

<h2>Objective</h2>
Understand how to work with a Windows DNS Server 


<h2>Description</h2>
Configure DNS as a primary DNS server and add records 


<h2>Utilities Used</h2>

- <b>Service Manager - DNS </b>
- <b>DNS Manager  </b> 

<h2>Environments Used </h2>

-VirtualBox
-   <b>Windows Server 2022</b>
-   <b>Windows 10</b> (Client)
     
<h2>Program walk-through:</h2>

<p align="left">
Lab Task 1: Configure DNS: add and resolve A and CNAME records. <br/>   

<p align="center">
On SERVER1, in Server Manager, Click Tools and select DNS: <br/>
<img src="https://imgur.com/IgeOcgW.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Expand SERVER1 > Foward Lookup Zones > cyber.local: <br/>
<img src="https://imgur.com/DMPtBwL.png" height="80%" width="80%" alt="Configure DNS steps"/>
<br />
<br />
Right-click cyber.local and choose New Host (A or AAAA)...: <br/>
<img src="https://imgur.com/MciZPQT.png" height="80%" width="80%" alt="Configure DNS steps"/>
<br />
<br />
For Name, enter test-client; for IP Address, enter 10.0.0.10; and click Add Host. Click OK when prompted:  <br/>
<img src="https://imgur.com/v4rZ5UN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log into the Windows 10 client VM:  <br/>
<br />
<br />
Open the Command Prompt (CMD) and run the command nslookup test-client.cyber.local:  <br/>
<img src="https://imgur.com/2KOI6dn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On SERVER1, in Server Manager, click Tools and select DNS:  <br/>
<br />
<br />
Expand SERVER1 > Foward Lookup Zones > cyber.local
<br />
<br />  
Right Click cyber.local and choose New Alias (CNAME)...    
<img src="https://imgur.com/gr4F0IT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Under Alias name, enter MY-FAVORITE-CLIENT
<img src="https://imgur.com/fIWq4aO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click Browse… on the right, double-click SERVER1, double-click Forward Lookup Zones, then double-click cyber.local, and choose test-client. Enter test-client.cyber.local in the Fully qualified domain name field, then click OK.
<img src="https://imgur.com/6YP5HVw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/n8TeMEj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/ceVh5Dv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/UGg78OV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log into the Windows 10 client VM
<br />
<br />
Open CMD and run the command nslookup my-favorite-client.cyber.local
<img src="https://imgur.com/O6OTQEN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Why do we need CNAME records?
<br />
<br />
One answer: 
"CNAME records are ideal for simplifying DNS record management for a domain, instead of having to update multiple A records whenever an IP address changes, you can easily update a single CNAME record and point to a new domain". 
Source: https://constellix.com/news/cname-records-common-use-cases-and benefits#:~:text=CNAME%20records%20are%20ideal%20for,point%20to%20a%20new%20domain.
<br />
<br />
<p align="left">
Lab Task 2: Bonus: Configure a PTR record on Server 1. <br/>   
<p align="center">
On SERVER1, navigate to the DNS Servers section, right-click SERVER1 on the server panel as shown, and select DNS Manager.: <br/>
<img src="https://imgur.com/Sx41N4C.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Right-click Reverse Lookup Zones and select New Zone...
<img src="https://imgur.com/Qga7Syr.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Click Next and select Primary zone.
<img src="https://imgur.com/U85pNw0.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Under Reverse Lookup Zone Name, select IPv4 Reverse Lookup Zone, and click Next.
<img src="https://imgur.com/8oesljS.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
For the network ID, enter 10.0.0, leave the rest empty, and click Next.
<img src="https://imgur.com/oJla10I.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
On the Dynamic Update window, select Allow both nonsecure and secure dynamic updates, and click Next.
<img src="https://imgur.com/FArNl4v.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Click Finish....................................................................                                                                                  
<img src="https://imgur.com/o4LLxBu.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Expand Forward Lookup Zones and select cyber.local. Double-click test-client.
<img src="https://imgur.com/dlHNjAI.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
Select Update associated pointer (PTR) record and click OK.
<img src="https://imgur.com/j20ZSP5.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />
From the client machine, resolve the 10.0.0.10 IP using the nslookup command. What are the results?
<img src="https://imgur.com/SOzR6Oy.png" height="80%" width="80%" alt="Configure DNS Steps"/>
<br />
<br />

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
