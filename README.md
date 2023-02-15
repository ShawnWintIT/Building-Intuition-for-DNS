<p align="center">
<img src=https://i.imgur.com/tr98pf0.png height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will test Domain Name System (DNS). This will improve our knowlede of DNS.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Active Directory Virtual Machine
- Client Machine joined to your domain

<h2>Actions and Observations</h2>
</p>
<p>
First we are going to log back into our DC and Client VM as the admin. Once done, we are going to be testing hostname "mainframe" to get a connection. Mainframe is just a made up word used for this experiement. Without creating the DNS record, pinging the hostname "mainframe" will not be successful. The Client VM checks the DNS cache, its local host file, and the DNS server when we ping "mainframe". In order to recieve a reply from "mainframe" we must create an A record.
</p>
<br /v

<p>
<img src= https://i.imgur.com/s4ayuQu.png height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<br /v

<p>
<img src= https://i.imgur.com/Pp7JDsC.png height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>
To create an A record, we are going to go into DC VM and go into server manager, tap tools and click DNS-> Tap DC-> tap arrow down for forward lookup zones-> then tap mydomain.com. Right click to create a new host (A), name the domain mainframe and type your Domain controller ip address just to see the connection. Click apply and done  when you are finished and ping mainframe in CLient Vm to see the reply.
</p>
<br /v

<p>
<img src=https://i.imgur.com/r9we0Za.png height="80%" width="80%" alt="Disk Sanitization Steps"/>    
</p> 
<p>
Next we will go back to DC VM and change mainframe's ip adress to 8.8.8.8. Ping mainframe in Client Vm and observe the changes,now either two things could have happened, the ip address changed or it didn't. It could still show the original ip address that you had for a records, thats because it is still lingereing in your computers local cache. To make sure of the change, one must use ipconfig/ flushdns. Observe the adress of the new record is showing up, check for the new changes by pinging mainframe. Look below for further details.
</p>
<br />

<p>
<img src= https://i.imgur.com/hJe0KSe.png height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br /v
 
<p>
<img src= https://i.imgur.com/jmqrecj.png height="80%" width="80%" alt="Disk Sanitization Steps"/>  
</p>
<p>
Last but not least, we'll set up a CNAME record to direct the host "search" to "www.google.com." Ping won't be able to locate the host if we use the "search" option. To construct the CNAME record "search," we must create a CNAME for "search" in dns manager in DC VM.
</p>
<br /v

<p>
<img src= https://i.imgur.com/xnsS4sS.png height="80%" width="80%" alt="Disk Sanitization Steps"/> 
</p>
<p>
Go back to client vm.Ping "search" and nslookup "search" and observe the changes. Once you observe the changes you will see that it mapped you to google.com. 
