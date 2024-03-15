<h1>GITHUB TESTMODE!!!!IDS-IPS with LimaCharlie</h1>

<h2>Description</h2>
The objective of this lab is build a home SOC Analyst Lab. This Lab consistt of.............
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Command Promt</b> 

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Linux (Ubuntu)</b>
- <b>LimaCharlie</b>
- <b>Crate detections rule</b>
- <b>Blocking an attack</b>
- <b>Trigger YARA scans with a detection rule</b>


<h2>Project Overview </h2>

- <b>Setting Up Virtual Environment</b>

1. Download and installed VMWare workstation ISO<br/>
2. Downloaded Windows VM and Ubuntu Server installer ISO<br/>
3. Deploy Windows VM and Ubuntu Server<br/>
 
<img src="https://i.imgur.com/RL488LP.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/UU0fo2L.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/fUzrk4j.png"/>

<br />
<br />

-----------------------------------------------

A. Set up static IP for VM Workstation so that it doesn’t change throughout the lab or beyond it by copying down Subnet IP and Gateway IP.<br/>
 
<img src="https://i.imgur.com/MS9u42c.png"/>
<br />
<br />

-----------------------------------------------

4. In the Ubuntu installer change the interface from DHCPv4 to Manual and paste subnet IP and Gateway IP: <br/>
<img src="https://i.imgur.com/3qmrxHh.png"/>

-----------------------------------------------


<img src="https://i.imgur.com/UJI8rMh.png"/>

-----------------------------------------------


<img src="https://i.imgur.com/BZXR2GI.png"/>

-----------------------------------------------

<br />
<br />
5. Confirm connection after installation is complete <br/>
<img src="https://i.imgur.com/hpQPz8b.png"/>

----------------------------------------------

<img src="https://i.imgur.com/xXYvEVR.png"/>
<br />
<br />

----------------------------------------------


- <b>Set Up Windows VM</b>

1. Turn on Windows VM and disable Microsoft Defender in “Manager Settings” Under “Virus & threat protection settings” (this will avoid interference from defender during scans)<br/>
3. Permanently Disable Defender via Group Policy Editor in cmd prompt as administrator.<br>
4. Disable some services via the “Registry Editor”<br/>
<img src="https://i.imgur.com/aAw83rZ.png"/>

----------------------------------------------

<img src="https://i.imgur.com/ryOojEx.png"/>

----------------------------------------------

<img src="https://i.imgur.com/uZNCHxw.png"/>


----------------------------------------------


<img src="https://i.imgur.com/zlO6kBt.png"/>


- <b>Prevent Windows VM From Going Into Standby</b>

1.	From an administrative command prompt, let’s prevent the VM from going into sleep/standby mode during lab.


----------------------------------------------

<img src="https://i.imgur.com/wqkhrIq.png"/>

----------------------------------------------

- <b>Install Sysmon in Windows VM<b/>
1.	Launch administrative PowerShell console.<br/>
2.	Download Sysmon and SwiftOnSecurity’s Sysmon config.<br/>
4.	Downloaded and install Sysmon with Swift’s config.<br/>
5.	Validate Sysmon64 service is installed and running.<br/>
6.	Check for the presence of Sysmon Event Logs.<br/>


----------------------------------------------

<img src=""/>

----------------------------------------------

<img src=""/>


- <b>Install LimaCharlie EDR on Windows VM<b/>

1.	Create a free LimaCharlie account and org after account is created.<br/>
2. Once the org is created Add Sensor windows VM.<br/>
3. Install sensor from the windows VM cmd propmt<br/>


----------------------------------------------

<img src=""/>

----------------------------------------------

<img src=""/>



4. Configure LimaCharlie to send the Sysmon event logs alongside its own EDR telemetry.<br/>


----------------------------------------------

<img src=""/>

----------------------------------------------


- <b>Setup Attack System<b/>

1.	Use host system to SSH into Linux VM.<br/>
2.	Set up c2 server.<br/>
3.	Downlaod and set up Sliver (a C2 framework by BishopFox).<br/>
4.	Create a working directory to use in future steps.<br/>


----------------------------------------------

<img src=""/>

----------------------------------------------

<img src=""/>

----------------------------------------------

<img src=""/>

----------------------------------------------

<img src=""/>


- <b>Generate C2 payload<b/>

1.	Log into SSH from host machine.<br/>
a.	Log in as root and launch Sliver server
c.	Generate our first C2 session payload (within the Sliver shell above). Be sure to use your Linux VM’s IP address we statically set in Part 1.
d.	Confirm implant configuration
e.	Download the C2 payload from Linux VM to the Windows VM with python code to spin up web server
f.	Launch Adminstrator PowerShell console on Windows VM to download C2 payload from the Linux Vm to the Windows VM. WITH FOLLOWING COMMAND.
g.	SNAPSHOT Windows VM before VM is infected by MALWARE.



















Sanitization complete:  <br/>
<img src=""/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src=""/>
</p>

<p align="center">

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
