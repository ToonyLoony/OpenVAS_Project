<h1>OpenVAS Vulnerability Assessment Project</h1>

<h2>Description</h2>
This project consists of peformning a simple vulnerability assessment on a vagrant virtual machine (win2k8) using OpenVAS. I will be performing a very basic scan with credentials provided (user:pass) of the vagrant machine. In summary i will be simply evaluating the vulnerabilities found on this virtual machine and discussing possible remediations
<br />

<h2>Utilities Used</h2>

- <b>OpenVAS</b> 

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
<img src="https://i.imgur.com/XworRPu.png" alt="NessusLab"/>
<br />
<br />

<h3>Setting up Target information</h3>

So far we have launched OpenVAS and provided the credintials to our windows 2008 VM. This will allow OpenVAS to SSH into the machine and provide a more thorough scan.

Next, we will setting up the target information.Here we will be inputting the IP of the target and the credentials we provided earlier

Gathering VM's IP:  <br/>
<img src="https://i.imgur.com/5eDpn2P.png" width="80%" alt="NessusLab"/>
<br />
<br />
Inputting Credentials and IP:  <br/>
<img src="https://i.imgur.com/beTCs19.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
<h3> Creating Vulnerability Task </h3>
We have now convyed the target IP and provided credientials. Next we must setup a new Vulnerability task with the information we just listed
<br />
<br />

Providing new task details: <br/>
<img src="https://i.imgur.com/Aw1IscQ.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Creation of Vulnerability Task:  <br/>
<img src="https://i.imgur.com/jtYUV0D.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
<img src="https://i.imgur.com/lGBAICg.png" height="80%" width="80%" alt="NessusLab"/>
<h3> Results Overview</h3>
<br/>
<img src="https://i.imgur.com/rH1dvJS.png" alt="NessusLab"/>
<br />
<br />
<img src="https://i.imgur.com/ckUFrYc.png" alt="NessusLab"/>
<br />
<br />
<img src="https://i.imgur.com/Zyxa6g0.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />

Looking at the results we can see an array of high severity vulnerabilties. This is somewhat to be expected as the VM im scanning is win2k8 and no updates have been performed on it. There are so many attack vectors for an attacker to choose , ranging from RCE attacks, DOS , SSH & FTP brute froce, the list goes on..

For the following section i will be exploiting one of the vulnerabilties listed on OpenVAS to ultimately demonstrate the consequences of not fixing vulnerabilties

<h3>Exploitation Example</h3>

Now the vulnerability i will be exploiting is the 'ElasticSearch EOL exploit | CVE-2014-3120'. I will be using a payload that exploits a remote command execution (RCE) vulnerability in ElasticSearch, exploitable by default on ElasticSearch prior to 1.2.0. The bug is found in the REST API, which does not require authentication, where the search function allows dynamic scripts execution

<img src="https://i.imgur.com/fJYsMme.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Starting Metasploit Framework: <br/>
<img src="https://i.imgur.com/WK970A1.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Configuring Options: <br/>
<img src="https://i.imgur.com/op9KWd6.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Starting Exploit: <br/>
<img src="https://i.imgur.com/jRVZiM1.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
BOOM We're IN!: <br/>
<img src="https://i.imgur.com/LLZW0uK.png" height="80%" width="80%" alt="NessusLab"/>
<br />
Great we successfully managed to get into the system via RCE! 

<h4>Post Exploitation</h4>
As you can see we have now performed RCE (Remote Code Execution) on the target. For this next section i will demonstrate what a hacker might do once inside a system. For this exmaple i created a file on the win2k8 machine called 'Passwords' this contains a file called 'HIDEME'. We will do some basic directory travesal and see whats inside 👀
<br />
<br />
Directory Traversal: <br/>
<img src="https://i.imgur.com/FG64bF4.png" height="80%" width="80%" alt="NessusLab"/>

Here i go down to C:\\ to view everything. What you may have noticed is we have root privilages and access and can quite literally do anything
<br />
<br />
Traversing to Users/Admin/Desktop: <br/>
<img src="https://i.imgur.com/mSOCHwA.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Passwords Directory: <br/>
<img src="https://i.imgur.com/lsUAKql.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />
Grab the Loot!: <br/>
<img src="https://i.imgur.com/kGdo40q.png" height="80%" width="80%" alt="NessusLab"/>
<br />
<br />

<h4>Conclusion</h4>
Overall in this project i wanted to simply demonstrate the power of OpenVAS , whilst also highlighting just how dangerous some of this vulnerabilties can be if not remediated quickly! I hope you enjoyed :p

If you would like to look into the vulnerability i exploited the CVE can be found here https://nvd.nist.gov/vuln/detail/CVE-2014-3120

Thanks you for Reading My Post ❤️
</p>
