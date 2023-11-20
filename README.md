<h1>Active Directory Lab</h1>

<h2>Description</h2>
Add the description here
<br />


<h2>Program walk-through:</h2>

<h3>TASK 1 - Set up internal network’s IP address:</h3>

<p align="center">
On Window’s Server 2019, I clicked the network icon first, then clicked “Undefined network”, and then clicked “Change adapter options”. <br/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next, I checked each network connection by right clickinging on them>clicking on status>clicking on details. <br/>
<br />
<br />
I know which is connected to the internet based on the fact that it has an IP address that falls in the range of private addresses (1). Likewise, the network connection with the internal connection that was assigned an IP address by Virtual Box is outside of that range (2). For simplicity, I renamed the internet facing connection “_Internet_” and the internal connection “X_Internal_X”. <br/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
To assign an IP address, I right clicked on the “X_Internal_X” connection>clicked “Properties”>changed the IPv4 by double clicking “Internet Protocol Version 4 (TCP/IPv4). <br/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, I clicked on “Use the following IP address” and for the sake of this lab, inputed 172.16.0.1 for the IP address and 255.255.255.0 for the subnet mask. I then entered the loopback address of 127.0.0.1 for the Preferred DNS server. <br/>
<img src= "https://i.imgur.com/drB6zzq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 2 - Rename the PC for simplicity:</h3>

<p align="center">
I right-clicked the start menu>clicked on system>clicked “rename this pc”>renamed to “DomainController” (for this lab)>clicked “next”>then restart your system. <br/>
<img src= "https://i.imgur.com/DPoO3CO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 3 - Install Active Directory Domain Services:</h3>

<p align="center">
I went to the the Server Manger by clicking start then selecting “Server Manger” <br/>
<br />
<br />
Next, I clicked on “Add roles and features”>next>selected “Role-based or feature-based installation (next)>ensure that the server in use is selected (next)>selected Active Directory Domain Services>selected “Add Features>selected (next x3)>then selected install. It appeared as shown below.  <br/>
<img src="https://i.imgur.com/N8PFF0j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
When it was finished, I noticed it said “Configuration required…”. This is because I Installed Active Directory Domain Services software but didn’t create the domain yet. I then closed that window.  <br/>
<img src="https://i.imgur.com/ON7txFo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I clicked on the flag that is circled in the image below. Then clicked on “Promote this server to a domain controller”. <br/>
<img src="https://i.imgur.com/ON7txFo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I selected “Add a new forest” and made a domain name (I made a generic name for the sake of the lab). Then clicked next. <br/>
<img src="https://i.imgur.com/ON7txFo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now I chose a password, then clicked next (x5), and finally clicked install (computer automatically restarted). <br/>
<img src="https://i.imgur.com/ON7txFo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 4 - Create a dedicated Domain Admin account:</h3>

<p align="center">
I clicked on start>Windows Administrative Tools>Active Directory Users and Computers <br/>
<br />
<br />
Now I created an Organizational Unit to put my Admin account in. I did this by right clicking “my domain.com”>clicking New>clicking Organizational Unit>naming it “_ADMINS”. <br/>
<img src="https://i.imgur.com/EzlnEgB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now I created a new user under the “_ADMINS” folder by right clicking the folder, selecting “New” then selecting “User”. <br/>
<img src="https://i.imgur.com/82GR7k9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I filled out the identification information and password as I desired then clicked finish. <br/>
<br />
<br />
I then right-clicked the new user and selected “Properties”. <br/>
<img src="https://i.imgur.com/5S4JTLW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now I selected “Member of”>Add. Then I typed in “domain admins” in the text box and selected “Check Names”. After which I selected “OK”(on the right window) then “Apply” and “OK” on the left window. I now have a domain admin account. <br/>
<img src="https://i.imgur.com/5S4JTLW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 5 - Log into domain admin account:</h3>

<p align="center">
When logging back in, I selected “other user” and then signed into the domain admin account. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 6 - Install a Remote Access Server/Network Address Translation in order to allow the Windows 10 client to access the internet through the Domain Controller:</h3>

<p align="center">
Under the Server Manager’s dashboard, I selected “Add roles and features”, clicked next (x3), then selected “remote Access”, then clicked next (x2), I then selected “Routing” and “Add features”, then I clicked next (x3) and finally a clicked “Install”. It appeared as shown below. After the installation, I closeD the window. Notice it says “Configuration required…”. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, I selected “Tools”>”Routing and Remote Access”. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then right-clicked my Data Controller Server and selected “Configure and Enable Routing and Remote Access”. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now that the Wizard came up, I selected next, then selected NAT in order to let internal clients connect to the internet using one public IP address. After that I selected next and then selected the internet facing interface (as shown below) then clicked next and finish. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 7 - Set up a DHCP server on the Domain Controller. This will automatically give the Windows 10 clients on the network an IP address that will allow them access the internet:</h3>

<p align="center">
I clicked on “Add roles and features” in the Server Manager. I then clicked next (x3) then selected “DHCP Server” and “Add Features” then clicked next (x3) and “Install”. It should appear as shown below. When the installation finished, I closed the window. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now, I selected Tools>DHCP to set up the scope. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I selected domaincontroller.mydomain.com, right-clicked Ipv4 and selected “New Scope”. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now that the New Scope Wizard popped up, I clicked next, then personally I named the scope what the IP address range was. Then I clicked next. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then filled out the next page as shown below, then clicked next (x4). <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then filled out the next page as shown below, then clicked “add” and next. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then made sure 172.16.0.1 was included in the list below, then I clicked next (x3) and finish. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I right-clicked domaincontroller.mydomain.com and selected authorize. Then I right-clicked domaincontroller.mydomain.com and selected refresh. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
It looked as follows: <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then I right-clicked “Server Options”, selected configure options, checked off “003 Router”, and inputed the IP address “172.16.0.1” belonging to the domain controller. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then I restarted the server. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now I went back on the server manager and selected “Configure this local server”. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then switched both the Administrators and Users options off for IED Enhanced Security Configuration in order to simplify web browsing for the sake of the lab. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 8 - Use a PowerShell script to create all of the users:</h3>

<p align="center">
I clicked Start>Windows PowerShell>right-click Windows PowerShell ISE>More>Run as administrator. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then opened the PowerShell script which utilizes an existing .txt file with 1,000 randomly generated names including mine. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then enabled the execution of scripts by running the command “Set-ExecutionPolicy Unrestricted. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I switched to the directory in which the txt. file was located. Then I ran the script by clicking the button circled below. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Then I checked Active Directory to make sure the users were uploaded. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<h3>TASK 9 - Check the connectivity on the (internally connectedl) Windows 10 virtual machine:</h3>

<p align="center">
By using the ping command, I was able to see that www.google.com resolved meaning that the DNS server is functioning and the network infrastructure is properly configured. <br/>
<img src="https://i.imgur.com/igxHHYz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then joined the original domain “mydomian.com” (and renamed my system) by right-clicking start>system>Rename this PC (advanced)>change. Then I inputted the domain name and clicked “OK”. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
I then inputed my original account login information. I was prompted to restart my system. <br/>
<br />
<br />
I then checked my leases on my domain controller system and saw one. This was from the addition of the Windows 10 client computer. The client computer reached out to the DHCP server for an IP address which it provided. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Another test I carried out was to make sure the list of names on the txt. file were properly able to login with the credentials given to them on the PowerShell script. In this case it was first initial of first name and their last name as the username and Password1 for the password. <br/>
<img src="https://i.imgur.com/ArqVlJs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


 
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
