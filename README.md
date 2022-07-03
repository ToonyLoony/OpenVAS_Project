<h1>OpenVAS Vulnerability Assessment Project</h1>

<h2>Description</h2>
This project consists of performing a simple vulnerability assessment on a vagrant virtual machine (win2k8) using OpenVAS. I will be performing a basic credential scan (user:pass) on the vagrant machine, where the results will then be displayed in a report(PDF). Lastly, I will be exploiting a vulnerability found on the system to demonstrate the severity of not remediating vulnerabilities on a system/network
<br />

<h2>Utilities Used</h2>

- <b>OpenVAS</b> 
- <b>Metasploit Framework</b> 

<h2>Environments Used </h2>

- <b>Windows 2008(VM)</b>
- <b>Kali Linux(Host Machine)</b> 

<h2>Project Walk-Through</h2>

<p align="center">
  
<h3>Providing Credentials</h3>

Launching OpenVAS: <br/>
<img src="https://i.imgur.com/gvvf6x8.png" alt="OpenVAS Lab"/>
<br />
<br />
Inputting Credntials:  <br/>
<img src="https://i.imgur.com/XworRPu.png" alt="OpenVAS Lab"/>
<br />
<br />

<h3>Setting up Target information</h3>

So far we have launched OpenVAS and provided the credentials to our Windows 2008 VM. This will allow OpenVAS to SSH into the machine and provide a more thorough scan.

Next, we will set up the target information. Here we will input the IP of the target and the credentials we provided earlier

Gathering VM's IP:  <br/>
<img src="https://i.imgur.com/5eDpn2P.png" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
Inputting Credentials and IP:  <br/>
<img src="https://i.imgur.com/beTCs19.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
<h3> Creating Vulnerability Task </h3>
We have now illustrated the target IP and provided credentials. Next, we must set up a new Vulnerability task with the information we just listed
<br />
<br />

Providing new task details: <br/>
<img src="https://i.imgur.com/Aw1IscQ.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
Creation of Vulnerability Task:  <br/>
<img src="https://i.imgur.com/jtYUV0D.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
<img src="https://i.imgur.com/lGBAICg.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<h3> Results Overview</h3>
<br/>
<img src="https://i.imgur.com/rH1dvJS.png" alt="OpenVAS Lab"/>
<br />
<br />
<img src="https://i.imgur.com/ckUFrYc.png" alt="OpenVAS Lab"/>
<br />
<br />
<img src="https://i.imgur.com/Zyxa6g0.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
Looking at the results we can see an array of high-severity vulnerabilities. This is somewhat to be expected as the VM I'm scanning is windows 2008 and has had 0 updates 
performed on it. Currently, there are so many attack vectors for an attacker to choose from, ranging from RCE attacks, DOS, SSH & FTP brute force, the list goes on.
<br />
<br />
For the following section, I will be exploiting a vulnerability listed on our OpenVAS vulnerability Scan. This is to ultimately demonstrate the consequences of not fixing vulnerabilities on a system or network

<h3>Exploitation Example</h3>

Now the vulnerability I will be exploiting is the 'ElasticSearch EOL exploit | CVE-2014-3120'. I will be using a payload that exploits a remote command execution (RCE) vulnerability in ElasticSearch, exploitable by default on ElasticSearch prior to 1.2.0. The bug is found in the REST API, which does not require authentication, where the search function allows dynamic scripts execution.

<img src="https://i.imgur.com/fJYsMme.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
Starting Metasploit Framework: <br/>
<img src="https://i.imgur.com/WK970A1.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
Configuring Options: <br/>
<img src="https://i.imgur.com/op9KWd6.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
Starting Exploit: <br/>
<img src="https://i.imgur.com/jRVZiM1.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
BOOM We're IN!: <br/>
<img src="https://i.imgur.com/LLZW0uK.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
Great, we successfully managed to get into the system via RCE! 

<h4>Post Exploitation</h4>
As you can see we have now performed RCE (Remote Code Execution) on the target. For this next section, I will demonstrate what a hacker might do once inside a system. For this example, I created a file on the win2k8 machine called 'Passwords' which contains a file called 'HIDEME'. We will do some basic directory traversal and see what's inside 👀
<br />
<br />
What you may have noticed is we have root privilages and can perform quite literally anything we want from here on out. My demonstration is very tame, but can be vastly more devastating
<br />
<br />
Directory Traversal: <br/>
<img src="https://i.imgur.com/FG64bF4.png" height="80%" width="80%" alt="OpenVAS Lab"/>

Here i go down to C:\\ to view everything on the ground level.
<br />
<br />
Traversing to Users/Admin/Desktop: <br/>
<img src="https://i.imgur.com/mSOCHwA.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
Passwords Directory: <br/>
<img src="https://i.imgur.com/lsUAKql.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />
Grab the Loot!: <br/>
<img src="https://i.imgur.com/kGdo40q.png" height="80%" width="80%" alt="OpenVAS Lab"/>
<br />
<br />

<h3>Conclusion</h3>
Overall in this project, I wanted to simply demonstrate the power of OpenVAS, whilst also highlighting just how dangerous some of these vulnerabilities can be if not remediated quickly!
<br />
<br />
To remediate this specific issue, I would look to perform updates on ElasticSearch and potentially update windows as well. After which I would then perform a follow-up Vulnerability Scan on the system to make sure the vulnerability doesn't exist.

If you would like to look into the vulnerability I exploited the CVE can be found here https://nvd.nist.gov/vuln/detail/CVE-2014-3120

Thank you for Reading My Post ❤️
</p>
