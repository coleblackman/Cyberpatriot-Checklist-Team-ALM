# Cyberpatriot-Checklist-Team-ALM

LINUX/UBUNTU

1. README file

2. Read over the forensic questions

3. Update entire system- <code>sudo apt update</code>

4. Update Bash <code>sudo apt-get dist-upgrade</code>

5. Read through users on README and verify <ul>
<li>No unnecessary users</li>
<li>No users not on the system</li>
<li>All users have correct permissions</li>
   </ul>
6. Remove guest account <code>sudo vi /etc/lightdm/lightdm.conf</code> and add allow-guest = false to the end
7. Check for autologin of unauthorized accounts <code>sudo vi /etc/lightdm/lightdm.conf</code>
 
