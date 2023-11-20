<h1>Active Directory Lab</h1>

<h2>Description</h2>
In this lab I created a fully-functional Active Directory home lab environment using Oracle Virtual Box. This helped me develop a stronger understanding of the functionalities and mechanisms of Active Directory and it also gave me a better understand of Windows networking.
<br />


<h2>Walk-through:</h2>

<h3>TASK 1 - Set up internal network’s IP address:</h3>

<p align="center">
On Window’s Server 2019, I clicked the network icon first, then clicked “Undefined network”, and then clicked “Change adapter options”. <br/>
<img width="639" alt="Screen Shot 2023-11-17 at 11 57 28 AM" src="https://github.com/StefanBlaszczak/Active-Directory-Lab/assets/150819772/c1c93fde-4139-4615-a007-d1575e22f28e">
<br />
<br />
Next, I checked each network connection by right clickinging on them>clicking on status>clicking on details. <br/>
<br />
<br />
I know which is connected to the internet based on the fact that it has an IP address that falls in the range of private addresses (1). Likewise, the network connection with the internal connection that was assigned an IP address by Virtual Box is outside of that range (2). For simplicity, I renamed the internet facing connection “_Internet_” and the internal connection “X_Internal_X”. <br/>
<img width="560" alt="Screen Shot 2023-11-17 at 12 12 54 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/f636da16-aa11-404d-8650-1421fc571cf7">
<img width="530" alt="Screen Shot 2023-11-17 at 12 14 40 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/77028a59-d6a7-4fe9-ad93-0ab46e1cc5fe">
<br />
<br />
To assign an IP address, I right clicked on the “X_Internal_X” connection>clicked “Properties”>changed the IPv4 by double clicking “Internet Protocol Version 4 (TCP/IPv4). <br/>
<img width="575" alt="Screen Shot 2023-11-17 at 12 25 17 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/9bd0c97c-fdfe-4abe-8364-cb9f9ed35b9c">
<br />
<br />
Now, I clicked on “Use the following IP address” and for the sake of this lab, inputed 172.16.0.1 for the IP address and 255.255.255.0 for the subnet mask. I then entered the loopback address of 127.0.0.1 for the Preferred DNS server. <br/>
<img width="526" alt="Screen Shot 2023-11-17 at 12 34 51 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/82c14bd9-4b59-44b6-ae69-abbc35bee977">
<br />
<br />

<h3>TASK 2 - Rename the PC for simplicity:</h3>

<p align="center">
I right-clicked the start menu>clicked on system>clicked “rename this pc”>renamed to “DomainController” (for this lab)>clicked “next”>then restart your system. <br/>
<img width="547" alt="Screen Shot 2023-11-17 at 12 20 38 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/cfba6fb3-bfc6-488d-85ec-14759b3b056e">
<br />
<br />

<h3>TASK 3 - Install Active Directory Domain Services:</h3>

<p align="center">
I went to the the Server Manger by clicking start then selecting “Server Manger” <br/>
<br />
<br />
Next, I clicked on “Add roles and features”>next>selected “Role-based or feature-based installation (next)>ensure that the server in use is selected (next)>selected Active Directory Domain Services>selected “Add Features>selected (next x3)>then selected install. It appeared as shown below.  <br/>
<img width="442" alt="Screen Shot 2023-11-17 at 12 44 35 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/90a40170-e3e9-4bb0-ba68-5038700f3b41">
<br />
<br />
When it was finished, I noticed it said “Configuration required…”. This is because I Installed Active Directory Domain Services software but didn’t create the domain yet. I then closed that window.  <br/>
<img width="428" alt="Screen Shot 2023-11-17 at 12 54 08 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/3055b881-0cfa-468d-aaac-2421e3a69c16">
<br />
<br />
I clicked on the flag that is circled in the image below. Then clicked on “Promote this server to a domain controller”. <br/>
<img width="570" alt="Screen Shot 2023-11-17 at 1 03 54 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/716ce710-abd8-44bf-866e-5421fa09b892">
<br />
<br />
I selected “Add a new forest” and made a domain name (I made a generic name for the sake of the lab). Then clicked next. <br/>
<img width="406" alt="Screen Shot 2023-11-17 at 1 05 50 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/355397b5-3e06-4245-a08d-49fbe2420daa">
<br />
<br />
Now I chose a password, then clicked next (x5), and finally clicked install (computer automatically restarted). <br/>
<img width="413" alt="Screen Shot 2023-11-17 at 1 12 06 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/bac776b1-d717-486e-9a3d-fad2a73bc701">
<br />
<br />

<h3>TASK 4 - Create a dedicated Domain Admin Account:</h3>

<p align="center">
I clicked on start>Windows Administrative Tools>Active Directory Users and Computers <br/>
<br />
<br />
Now I created an Organizational Unit to put my Admin account in. I did this by right clicking “my domain.com”>clicking New>clicking Organizational Unit>naming it “_ADMINS”. <br/>
<img width="576" alt="Screen Shot 2023-11-17 at 1 25 04 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/222483f5-3553-429b-a76b-cbe0db02b5d7">
<br />
<br />
Now I created a new user under the “_ADMINS” folder by right clicking the folder, selecting “New” then selecting “User”. <br/>
<img width="401" alt="Screen Shot 2023-11-17 at 1 28 49 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/469fd3cc-e0e5-4273-b923-d599a7952cc4">
<br />
<br />
I filled out the identification information and password as I desired then clicked finish. <br/>
<br />
<br />
I then right-clicked the new user and selected “Properties”. <br/>
<img width="574" alt="Screen Shot 2023-11-17 at 1 35 00 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/3664669d-a733-4d3f-9031-d73b73a813f4">
<br />
<br />
Now I selected “Member of”>Add. Then I typed in “domain admins” in the text box and selected “Check Names”. After which I selected “OK”(on the right window) then “Apply” and “OK” on the left window. I now have a domain admin account. <br/>
<img width="478" alt="Screen Shot 2023-11-17 at 1 38 32 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/b120e871-c04c-4998-becb-fdef65f5e2eb">
<br />
<br />

<h3>TASK 5 - Log into domain admin account:</h3>

<p align="center">
When logging back in, I selected “other user” and then signed into the domain admin account. <br/>
<img width="654" alt="Screen Shot 2023-11-17 at 1 43 43 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/9fa5366c-dfa9-4f94-a797-8524a7b56fc8">
<br />
<br />

<h3>TASK 6 - Install a Remote Access Server/Network Address Translation in order to allow the Windows 10 client to access the internet through the Domain Controller:</h3>

<p align="center">
Under the Server Manager’s dashboard, I selected “Add roles and features”, clicked next (x3), then selected “remote Access”, then clicked next (x2), I then selected “Routing” and “Add features”, then I clicked next (x3) and finally a clicked “Install”. It appeared as shown below. After the installation, I closed the window. Notice it says “Configuration required…”. <br/>
<img width="649" alt="Screen Shot 2023-11-17 at 2 06 33 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/7122feeb-2a75-42f5-8d64-430114005e37">
<br />
<br />
Now, I selected “Tools”>”Routing and Remote Access”. <br/>
<img width="651" alt="Screen Shot 2023-11-17 at 2 12 39 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/125c8f72-731e-45f3-b321-8765d21619e9">
<br />
<br />
I then right-clicked my Data Controller Server and selected “Configure and Enable Routing and Remote Access”. <br/>
<img width="313" alt="Screen Shot 2023-11-17 at 2 16 58 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/bf62e5dc-634a-4d93-bc74-8faa7f5d2dfb">
<br />
<br />
Now that the Wizard came up, I selected next, then selected NAT in order to let internal clients connect to the internet using one public IP address. After that I selected next and then selected the internet facing interface (as shown below) then clicked next and finish. <br/>
<img width="309" alt="Screen Shot 2023-11-17 at 2 21 51 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/58d79895-c9c3-4b6b-b551-4273bdba0719">
<br />
<br />

<h3>TASK 7 - Set up a DHCP server on the Domain Controller. This will automatically give the Windows 10 clients on the network an IP address that will allow them access the internet:</h3>

<p align="center">
I clicked on “Add roles and features” in the Server Manager. I then clicked next (x3) then selected “DHCP Server” and “Add Features” then clicked next (x3) and “Install”. It should appear as shown below. When the installation finished, I closed the window. <br/>
<img width="406" alt="Screen Shot 2023-11-17 at 2 49 44 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/eb6dd7e9-cb63-4270-be9c-7f75b510d37d">
<br />
<br />
Now, I selected Tools>DHCP to set up the scope. <br/>
<img width="651" alt="Screen Shot 2023-11-17 at 3 10 53 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/c228a8d1-e994-4776-9427-164f5dbf48da">
<br />
<br />
I selected domaincontroller.mydomain.com, right-clicked Ipv4 and selected “New Scope”. <br/>
<img width="513" alt="Screen Shot 2023-11-17 at 4 01 11 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/452090c4-98a7-47a5-901b-611e48c904c8">
<br />
<br />
Now that the New Scope Wizard popped up, I clicked next, then personally I named the scope what the IP address range was. Then I clicked next. <br/>
<img width="259" alt="Screen Shot 2023-11-17 at 4 07 14 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/7b109470-c045-4356-9e2d-37b86ff5bea2">
<br />
<br />
I then filled out the next page as shown below, then clicked next (x4). <br/>
<img width="266" alt="Screen Shot 2023-11-17 at 4 10 10 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/2bee2536-8851-49ae-a8bc-03c87c651d97">
<br />
<br />
I then filled out the next page as shown below, then clicked “add” and next. <br/>
<img width="262" alt="Screen Shot 2023-11-17 at 4 17 03 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/2a4cd7fa-87d9-4be8-91ad-57692fd69aee">
<br />
<br />
I then made sure 172.16.0.1 was included in the list below, then I clicked next (x3) and finish. <br/>
<img width="258" alt="Screen Shot 2023-11-17 at 4 21 33 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/9eee35a4-497f-42da-a7ae-e7a6d1d77575">
<br />
<br />
I right-clicked domaincontroller.mydomain.com and selected authorize. Then I right-clicked domaincontroller.mydomain.com and selected refresh. <br/>
<img width="343" alt="Screen Shot 2023-11-17 at 4 23 40 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/d97d19c5-8530-4799-bf76-219ca8c2e9cf">
<br />
<br />
It looked as follows: <br/>
<img width="511" alt="Screen Shot 2023-11-17 at 4 28 42 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/aaf659ce-890b-4cad-9216-748e8b8fa9f7">
<br />
<br />
Then I right-clicked “Server Options”, selected configure options, checked off “003 Router”, and inputed the IP address “172.16.0.1” belonging to the domain controller. <br/>
<img width="559" alt="Screen Shot 2023-11-20 at 4 38 07 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/dad04474-d4e3-4b87-8e72-b052e9e0f9a2">
<br />
<br />
Then I restarted the server. <br/>
<img width="499" alt="Screen Shot 2023-11-20 at 4 43 02 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/ba0996ba-0df2-4976-ac13-cd0fc6dbfa43">
<br />
<br />
Now I went back on the server manager and selected “Configure this local server”. <br/>
<img width="751" alt="Screen Shot 2023-11-20 at 2 32 38 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/c84d11b0-1349-44ee-a14c-a31067f68955">
<br />
<br />
I then switched both the Administrators and Users options off for IED Enhanced Security Configuration in order to simplify web browsing for the sake of the lab. <br/>
<img width="587" alt="Screen Shot 2023-11-20 at 2 36 08 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/da8f5730-3076-4d24-b0c9-5fbf304b5574">
<br />
<br />

<h3>TASK 8 - Use a PowerShell script to create all of the users:</h3>

<p align="center">
I clicked Start>Windows PowerShell>right-click Windows PowerShell ISE>More>Run as administrator. <br/>
<img width="515" alt="Screen Shot 2023-11-20 at 3 03 57 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/6e452567-d16e-4460-822d-2d0e409658cb">
<br />
<br />
I then opened the PowerShell script which utilizes an existing .txt file with 1,000 randomly generated names including mine. <br/>
<img width="669" alt="Screen Shot 2023-11-20 at 3 07 24 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/da7c87c3-c63d-4d8b-b3c9-8d4e9eaa5867">
<br />
<br />
I then enabled the execution of scripts by running the command “Set-ExecutionPolicy Unrestricted. <br/>
<img width="671" alt="Screen Shot 2023-11-20 at 3 09 51 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/e721afb8-c230-4504-a9b4-44eb4769a7e2">
<br />
<br />
I switched to the directory in which the txt. file was located. Then I ran the script by clicking the button circled below. <br/>
<img width="669" alt="Screen Shot 2023-11-20 at 3 28 14 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/1bde8b7e-df83-48b6-8bb4-48126bb0c33c">
<br />
<br />
Then I checked Active Directory to make sure the users were uploaded. <br/>
<img width="397" alt="Screen Shot 2023-11-20 at 3 56 34 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/c1be43c3-bd28-4e3f-b1d2-64161abdf1b6">
<br />
<br />

<h3>TASK 9 - Check the connectivity on the (internally connectedl) Windows 10 virtual machine:</h3>

<p align="center">
By using the ping command, I was able to see that www.google.com resolved meaning that the DNS server is functioning and the network infrastructure is properly configured. <br/>
<img width="489" alt="Screen Shot 2023-11-20 at 4 52 26 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/0a4d753d-e550-4dae-9fe2-e78c59655844">
<br />
<br />
I then joined the original domain “mydomian.com” (and renamed my system) by right-clicking start>system>Rename this PC (advanced)>change. Then I inputted the domain name and clicked “OK”. <br/>
<img width="168" alt="Screen Shot 2023-11-20 at 5 01 20 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/293749eb-6d2f-4b42-b8fb-2e0d860327b2">
<br />
<br />
I then inputed my original account login information. I was prompted to restart my system. <br/>
<br />
<br />
I then checked my leases on my domain controller system and saw one. This was from the addition of the Windows 10 client computer. The client computer reached out to the DHCP server for an IP address which it provided. <br/>
<img width="494" alt="Screen Shot 2023-11-20 at 5 09 39 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/684dfecb-fab4-4709-96ed-f57c02a40dcd">
<br />
<br />
Another test I carried out was to make sure the list of names on the txt. file were properly able to login with the credentials given to them on the PowerShell script. In this case it was first initial of first name and their last name as the username and Password1 for the password. <br/>
<img width="512" alt="Screen Shot 2023-11-20 at 5 11 24 PM" src="https://github.com/StefanBlaszczak/WiresharkLab/assets/150819772/6a876cd8-1925-4d9e-a5ca-7de65bd20e49">
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
