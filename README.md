<h1>EDR with LimaCharlie</h1>

<h2>Lab Objective</h2>
Build a victim machine by disabling Microsoft Defender to make the system vulnerable. Then compromised the victim machine with a C2 exploitation framework “SLIVER”. Set up LimaCharlie, an EDR (Endpoint Detection Response) and configure Sysmon on the victim machine. See victim get compromised in LimaCharlie and then write a detection & response rule to detectand BLOCK attack.<br />

<h2>Environments Used </h2>

- <b>Windows VM</b>
- <b>Linux (Ubuntu)</b>
- <b>LimaCharlie</b>
- <b>Crate detections rule</b>
- <b>Trigger YARA scans with a detection rule</b>
- <b>Blocking an attack</b>

<h2>Project Overview </h2>

- <b>Setting Up Virtual Environment</b>

1. Download and installed VMWare workstation ISO.<br/>
2. Downloaded Windows VM and Ubuntu Server ISO.<br/>
3. Deploy Windows VM and Ubuntu Server on VMWare.<br/>
 
<img src="https://i.imgur.com/RL488LP.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/UU0fo2L.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/fUzrk4j.png"/>

-----------------------------------------------

A. Set up static IP for VM Workstation so that it doesn’t change throughout the lab or beyond it by copying down Subnet IP and Gateway IP.<br/>
 
<img src="https://i.imgur.com/MS9u42c.png"/>

-----------------------------------------------

4. In the Ubuntu installer change the interface from DHCPv4 to Manual and paste subnet IP and Gateway IP.<br/>

<img src="https://i.imgur.com/3qmrxHh.png"/>

-----------------------------------------------

<img src="https://i.imgur.com/UJI8rMh.png"/>

-----------------------------------------------


<img src="https://i.imgur.com/BZXR2GI.png"/>

-----------------------------------------------

5. Confirm connection after installation is complete.<br/>

<img src="https://i.imgur.com/hpQPz8b.png"/>

----------------------------------------------

<img src="https://i.imgur.com/xXYvEVR.png"/>

----------------------------------------------


- <b>Set Up Windows VM</b>

1. Turn on Windows VM and disable Microsoft Defender in “Manager Settings” Under “Virus & threat protection settings” (this will avoid interference from defender during scans).<br/>
2. Permanently Disable Defender via Group Policy Editor in cmd prompt as administrator.<br>
3. Disable some services via the “Registry Editor”.<br/>

<img src="https://i.imgur.com/aAw83rZ.png"/>

----------------------------------------------

<img src="https://i.imgur.com/ryOojEx.png"/>

----------------------------------------------

<img src="https://i.imgur.com/uZNCHxw.png"/>

----------------------------------------------

<img src="https://i.imgur.com/zlO6kBt.png"/>

-----------------------------------------------

- <b>Prevent VM From Going Into Standby</b>

1.	From an administrative command prompt, let’s prevent the VM from going into sleep/standby mode during lab.<br/>

<img src="https://i.imgur.com/wqkhrIq.png"/>

----------------------------------------------

- <b>Install Sysmon in Windows VM<b/>

1.	Launch administrative PowerShell console.<br/>
2.	Download Sysmon and SwiftOnSecurity’s Sysmon config.<br/>
3.	Install Sysmon with Swift’s config.<br/>
4.	Validate Sysmon64 service is installed and running.<br/>
5.	Check for the presence of Sysmon Event Logs.<br/>

<img src="https://i.imgur.com/2JY0ay3.png"/>

----------------------------------------------

<img src="https://i.imgur.com/vEnZwQL.png"/>

----------------------------------------------


- <b>Install LimaCharlie EDR on Windows VM<b/>

1.	Create a free LimaCharlie account and org after account is created.<br/>
2. Once the org is created Add Sensor windows VM.<br/>
3. Install sensor from the windows VM cmd propmt.<br/>


<img src="https://i.imgur.com/adCdqWG.png"/>

----------------------------------------------

<img src="https://i.imgur.com/yVaKEcD.png"/>

----------------------------------------------

<img src="https://i.imgur.com/rbK8mng.png"/>

----------------------------------------------

<img src="https://i.imgur.com/xmpkwGh.png"/>


4. Configure LimaCharlie to send the Sysmon event logs alongside its own EDR telemetry.<br/>


<img src="https://i.imgur.com/6rXTtco.png"/>

----------------------------------------------

<img src="https://i.imgur.com/gBmaHoE.png"/>

----------------------------------------------

- <b>Setup Attack System<b/>

1.	Use host system to SSH into Linux VM.<br/>
2.	Downlaod and set up Sliver (a C2 framework).<br/>

<img src="https://i.imgur.com/OwdtVh4.png"/>

----------------------------------------------

- <b>Generate C2 payload<b/>

1.	Log into SSH from host machine.<br/>
a.	Log in as root and launch Sliver server.<br/>
c.	Generate our first C2 session payload (within the Sliver shell above). Be sure to use your Linux VM’s IP address we statically set in Part 1.<br/>
d.	Confirm implant configuration.<br/>
e.	Download the C2 payload from Linux VM to the Windows VM with python code to spin up web server.<br/>
f.	Launch Adminstrator PowerShell console on Windows VM to download C2 payload from the Linux Vm to the Windows VM. WITH FOLLOWING COMMAND.<br/>
g.	SNAPSHOT Windows VM before VM is infected by MALWARE.<br/>

<img src="https://i.imgur.com/bgQYeTg.png"/>

----------------------------------------------

<img src="https://i.imgur.com/BSpq1E8.png"/>

----------------------------------------------

<img src="https://i.imgur.com/1xu6iRK.png"/>

----------------------------------------------

<img src="https://i.imgur.com/DtM69qB.png"/>

----------------------------------------------


- <b>Start Command and Control Session<b/>

1. Start SSH session on LINUX VM and enable the Sliver HTTP server to catch the callback.<br/>
2. On Windows VM, use PowerShell as Administrator to execute the C2 payload from download location.<br/>
3. Within a few moments, you should see your session check in on the Sliver server.<br/>
4. Verify your session in Sliver.<br/>
5. To connect to running session with C2 session use following command.<br/>
6. You are now interacting directly with the C2 session on the Windows VM. Let’s run a few basic commands to get our bearing on the victim host.<br/> 
7. Get basic info about the session<br/>

<img src="https://i.imgur.com/IOPUoTy.png"/>

----------------------------------------------

<img src="https://i.imgur.com/jACWKqL.png"/>

----------------------------------------------

<img src="https://i.imgur.com/iSC5mGa.png"/>

----------------------------------------------

8. Get basic info about the session.<br/>
a. Find out what user your implant is running as, and learn it’s privileges.<br/>
If your implant was properly run with Admin rights, you’ll notice we have a few privileges that make further attack activity much easier, such as “SeDebugPrivilege”.<br/>
b. Identify our implant’s working directory.<br/>
c. Examine network connections occurring on the remote system.<br/>
d. Identify running processes on the remote system.<br/>
Notice that Sliver cleverly highlights its own process in green and any detected countermeasures (defensive tools) in red.<br/>
E. This is how attackers become aware of what security products a victim system may be using.<br/>

<img src="https://i.imgur.com/Z2hOhct.png"/>

----------------------------------------------

<img src="https://i.imgur.com/ACeprbI.png"/>

----------------------------------------------

<img src="https://i.imgur.com/TEa9n0x.png"/>

----------------------------------------------

<img src="https://i.imgur.com/AWVFi1w.png"/>

----------------------------------------------

- <b>Observe EDR Telemetry<b/>

1. Switch to LimaCharlie UI and check out some basic features.<br/>
  a. “Sensors”,  “Processes”, and NOT signed and ACTIVE on network.<br/>
2.Browse to the location to find implant (C:\Users\User\Downloads).<br/>
3. Inspect the hash of the suspicious executable by scanning it with VirusTotal.<br/>
4. Check “Timeline” on the left-side menu of our sensor to show real-time view of EDR telemetry + event logs streaming from this system.<br/>
 a. Practice filtering timeline with known IOCs (indicators of compromise) such as the name of your implant.<br/>

<img src="https://i.imgur.com/oBGcJEh.png"/>

----------------------------------------------

<img src="https://i.imgur.com/gjHxyPk.png"/>

----------------------------------------------

<img src="https://i.imgur.com/eIWVCVu.png"/>

----------------------------------------------

<img src="https://i.imgur.com/gVtSBgk.png"/>

----------------------------------------------

- <b>Let’s Get Adversarial<b/>

1. Get back onto an SSH session on the Linux VM, and drop into a C2 session on your victim.<br/>
2. Adversaries love to steal credentials on a system using dump the lsass.exe process from memory.<br/>
(This will dump the remote process from memory, and save it locally on your Sliver C2 server).<br/>

<img src="https://i.imgur.com/ygGM30D.png"/>

----------------------------------------------

<img src="https://i.imgur.com/navUFfe.png"/>

----------------------------------------------

<img src="https://i.imgur.com/HWsaWcL.png"/>

----------------------------------------------

- <b>Detect Adversarial Telemetry<b/>

1. Switch over to LimaCharlie to find the relevant telemetry.<br/>
   a. Look for “SENSITIVE_PROCESS_ACCESS” to see how events look like when credential access occurred. This will
      help me build a detection & response rule that will alert me whenever the activity occurs.<br/>
   b. This rule will tell LimaCharlie to generate a detection report that will only look at SENSITIVE_PROCESS_ACCESS
      events where the victim or target process ends with lsass.exe.<br/>
   c. In the “Respond” section, I removed all content and replace with the following content.
      Test rule against event built for it.<br/>

<img src="https://i.imgur.com/f9imYcq.png"/>

----------------------------------------------

<img src="https://i.imgur.com/BY1RiCP.png"/>

----------------------------------------------

<img src="https://i.imgur.com/r1Ygp8k.png"/>

----------------------------------------------

- <b>Test Detection with Procdump<b/>

1. Go back to Sliver server console in C2 session and rerun “procdump”.<br/>
2. Back to LimaCharlie and click “detection” tab.<br/>
   a. Detection Signature will detect the raw event.<br/>

<img src="https://i.imgur.com/UUGlj70.png"/>

----------------------------------------------

<img src="https://i.imgur.com/HIZ4pOM.png"/>

----------------------------------------------

- <b>Detect and Prevent Threat on Windows System<b/>

1. Back onto SSH session on the Linux VM and drop into a C2 session on victim machine.<br/>
2. Browse over to LimaCharlie’s detection tab to see if default Sigma rules picked up on our shenanigans.<br/>
3. From this D&R rule template, I created a response action that will take place when this activity takes place.<br/>
   The “action: report” section simply fires off a Detection report to the “Detections” tab<br/>
   The “action: task” section is what is responsible for killing the parent process.<br/>
   responsible with deny_tree for the vssadmin delete shadows /all command.<br/>


<img src="https://i.imgur.com/lWmJFgb.png"/>

----------------------------------------------

<img src="https://i.imgur.com/01jBP2y.png"/>

----------------------------------------------

<img src="https://i.imgur.com/98oj949.png"/>

----------------------------------------------

- <b>BLOCK ATTACK!!<b/>

1. Return to Sliver C2 session, and rerun the command to delete volume shadows.<br/>
2. Action of running the command is what will trigger our D&R rule.<br/>
3. Test if D&R rule properly terminated the parent process, check to see if you still have an active system shell by rerunning the following "whoami" command.<br/>
4. If our D&R rule worked successfully, the system shell will hang and fail to return anything from the whomai command, because the parent process was terminated.<br/>

<img src="https://i.imgur.com/b0bUY7q.png"/>

----------------------------------------------

<img src="https://i.imgur.com/LoHNbsu.png"/>

----------------------------------------------

<img src="https://i.imgur.com/TEpgK5r.png"/>


!!!!!This is effective because in a real ransomware scenario, the parent process is likely the ransomware payload or lateral movement tool that would be terminated in this case!!!!<br/>

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
