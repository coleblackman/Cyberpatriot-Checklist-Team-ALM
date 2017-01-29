# Cyberpatriot-Checklist-Team-ALM

LINUX/UBUNTU

1. README file

2. Read over the forensic questions

3. Update entire system <code>sudo apt update</code>

4. Update Bash <code>sudo apt-get dist-upgrade</code>

5. Read through users on README and verify <ul>
<li>No unnecessary users</li>
<li>No users not on the system</li>
<li>All users have correct permissions</li>
   </ul>
6. <code> sudo vi /etc/passwd</code> to check for unauthorized users, or use Settings GUI.
7. Remove guest account <code>sudo vi /etc/lightdm/lightdm.conf</code> and add allow-guest = false to the end <code>sudo restart lightdm</code> may be required
8. Check for autologin of unauthorized accounts <code>sudo vi /etc/lightdm/lightdm.conf</code>
9. Install and run lynis to detect threats with https://cisofy.com/download/lynis/ <code>sudo lynis -c</code>
10. <code>sudo vi /etc/sudoers.d</code> and check for threats from unauthorized users or utilities accessing sudo
11. Lock down root to disable <code>su</code> by <code>sudo vi /etc/ssh/ssh_config</code> and <code>PermitRootLogin no</code>
12. <code>sudo vi /etc/group</code> and remove unauthorized accounts
13. Settings/Updates and enable automatic updates
14. <code>sudo netstat -lntup</code> or <code>sudo ss -lntup</code> to determine open ports. To close unauthorized ports (not on the readme) use 
15. <code>sudo ufw enable</code>
16. <code>cat /proc/sys/net/ipv4/tcp_syncookies</code> and <code>sysctl -n net.ipv4.tcp_syncookies</code>
 
