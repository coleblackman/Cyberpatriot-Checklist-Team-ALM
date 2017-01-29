# Cyberpatriot-Checklist-Team-ALM

<strong>LINUX/UBUNTU</strong>

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
14. <code>sudo netstat -lntup</code> or <code>sudo ss -lntup</code> to determine open ports. To close unauthorized ports (not on the readme) use <code>sudo lsof -i :$port</code><code>whereis ##PROGRAM NAME##</code> and use <code>dpkg -S ##PROGRAM LOCATION##</code> now, *carefully* <code>rm ##PROGRAM LOCATION##</code> and <code>killall -9 ##PROGRAME NAME##</code> and <code>sudo apt purge ##PACKAGE LOCATION##</code> Finally, check to make sure it is gone.
15. <code>sudo ufw enable</code>
16. <code>cat /proc/sys/net/ipv4/tcp_syncookies</code> and <code>sysctl -n net.ipv4.tcp_syncookies</code> to enable syn protection
17. Insure none of the unauthorized tools are running <code>sudo apt install synaptic</code> to use a package manager. Known malicious programs:
   <code>
   wireshark netcat-bsd netcat netcat-openbsd Ophcrack john john-bsd john-openbsd john-freebsd vuze frostwire aircrack metasploit_framework nessus snort kismet nikto yersinia burp-suite THCHydra  oclhashcat  maltego oswapzed cainandabel cain angryipscanner ipscan ettercap hydra medusa
   </code> if found, <code>sudo apt purge ##PROGRAM NAME##</code>
18. Unauthorized media files can be sourced with <code>cd /home</code> and then <code>find ./ -type f \( -iname \*.jpg -o -iname \*.sh -o -iname \*.png -o -iname \*.bmp -o -iname \*.mov -o -iname \*.mp3 -o -iname \*.mp4 -o -iname \*.mp3 -o -iname \*.jpeg -o -iname \*.mng -o -iname \*.gif -o -iname \*.mpeg -o -iname \*.flv \) -r </code> as well as <code>sudo ls -Ra *</code>
19. Password/PAM. To begin, <code>sudo vi /etc/login.defs</code> and change to <code>PASS_MIN_DAYS 7
				PASS_MAX_DAYS 90
				PASS_WARN_AGE 14</code>
20. Now, <code>sudo vi /etc/pam.d/common-auth</code> and <code>auth optional pam_tally.so deny=5 unlock_time=900 onerr=fail audit even_deny_root_account silent</code> also, Now, <code>sudo vi /etc/pam.d/common-password</code> Add <code>deny=5 unlock_time=1800 </code> to the pam_tally2.so line
21. Change all passwords to the requirement in the README.
22. Execute other requirements from servers such as mySQL or APACHE2.
23. Read through the entire README to find hidden points.
