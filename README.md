# Linux Server Hardening

<h2>Description</h2>
Hi there! This is an exciting project, where I explore some of the ways to secure and harden a Linux server. The distribution chosen would be Rock, as it is based on the Red Hat Enterprise Linux (RHEL) source code. RHEL is one of the most popular distributions in the enterprise world, and so working with Rocky would be a good alternative.
<br />

<h2>Hardening Measures Taken</h2>

- <b>SSH Keys for Authentication</b> 
- <b>Firewall</b>

<h2>Environments Used </h2>

- <b>Rocky 9.2</b> (21H2)

<h2>SSH Keys for Authentication:</h2>

In this step, we look into installing SSH keys for authentication on the linux server. SSH uses asymmetric encryption, generating a pair of cryptographic keys - a public key and a private key. ​The private key is kept securely on the client machine, while the public key is stored on the server. ​This eliminates the need to transmit passwords over the network, reducing the risk of password interception or brute-force attacks.​

Here are the step we take to harden the server with SSH authentication:
1. We start by doing a backup of the configuration file using this command: `cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup​`

Change port and login settings: sudo vi /etc/ssh/sshd_config​

Changing the default port number​

Disabling password-based login​

Disable SSH login using root username

Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
