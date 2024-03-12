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

<p align="center">
1. Download and installed VMWare workstation ISO <br/>
3. Downloaded Windows VM and Ubuntu Server installer ISO<br/>
3. Deploy Windows VM and Ubuntu Server <br/>
 
<img src="https://i.imgur.com/RL488LP.png"/>

-----------------------------------------------
<img src="https://i.imgur.com/UU0fo2L.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/fUzrk4j.png"/>

<br />

-----------------------------------------------

<p align="center">
A. Set up static IP for VM Workstation so that it doesn’t change throughout the lab or beyond it by copying down Subnet IP and Gateway IP.<br />
 
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
Wait for process to complete (may take some time):  <br/>
<img src=""/>
<br />
<br />
Sanitization complete:  <br/>
<img src=""/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src=""/>
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
