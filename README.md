# Linux Server Hardening

<h2>Description</h2>
Hi there! This is an exciting project, where I explore some of the ways to secure and harden a Linux server. The distribution chosen would be Rocky, as it is based on the Red Hat Enterprise Linux (RHEL) source code. RHEL is one of the most popular distributions in the enterprise world, and so working with Rocky would be a good alternative.
<br />

<h2>Hardening Measures Taken</h2>

- <b>SSH Keys for Authentication</b> 
- <b>Firewall</b>

<h2>Environments Used </h2>

- <b>Rocky 9.2</b>

<h2>SSH Keys for Authentication:</h2>

In this step, we look into installing SSH keys for authentication on the linux server. SSH uses asymmetric encryption, generating a pair of cryptographic keys - a public key and a private key. ​The private key is kept securely on the client machine, while the public key is stored on the server. ​This eliminates the need to transmit passwords over the network, reducing the risk of password interception or brute-force attacks.​ Security is improved by avoiding the need to have passwords stored in files, and eliminates the possibility of a compromised server stealing a user's password.

Here are the steps we take to harden the server with SSH authentication:
1. Generate the SSH certificate on the **client** side: `ssh-keygen -t rsa -b 4096`. -t specifies the type, rsa is the type of algorithm we choose (rsa is usually used for public key generation), -b is the number of bits and 4096 is the bit size. You will be prompted for a passphrase. Make sure you choose a strong one. The key is saved in the file `/root/.ssh`.
<img src="https://i.imgur.com/RLLBVXi.png" height="80%" width="80%">

2. We will now copy the public key we generated over to the server using: `ssh-copy-id [server username]@[server ip address]`. Remember we're still on the **client** side. Once you are done, you will be able to log into the server via `ssh [server-side username]@[server ip address]`.
<img src="https://i.imgur.com/GCrDZwa.png" height="80%" width="80%">
3. To harden the server, we can remove password authentication to ensure that only users with the SSH certificate can access the server, essentially disabling password-based login to the server. We can also disable SSH login using the root username and change the default port number. To do this, we edit a particular file **on the server** to include some extra settings.
- `cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup​` to backup the config file first
- `setenforce 0` to disable selinux, so that we can make changes to the config file without problem
- `nano /etc/ssh/sshd_config` to go into the config file and make our changes
-  Add the lines `Port 2222`, `PasswordAuthentication no` and `PermitRootLogin no`.

<img src="https://i.imgur.com/ZvQQrwQ.png" height="80%" width="80%">
<img src="https://i.imgur.com/oKSLgu1.png" height="80%" width="80%">

Now we can see that when we try to connect from the client machine via the default port, or connect using the user password, or connect directly as a root user, we are unable to.

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
