# 19CS545-Ex2 - Configure SElinux in GitHub

# AIM:
To create a Repository

# Procedure:
1. Checking SELinux ports 
The first command semanage port -l | grep h p checks the Security-Enhanced Linux (SELinux) 
policy for ports associated with the h p service. SELinux is a security feature in Linux that restricts 
what programs can access. The semanage port -l command lists all defined SELinux ports and the 
grep h p command filters the output to show only ports related to h p. 
The output shows several ports including 80 (standard web traffic), 8080, 8118, 8123 and a range 
from 10001 to 10010. 
2. Adding a new port 
The second command semanage port -a http_port_t tcp 82 adds a new port 
number (82) to the http_port_t port defini on. This allows h p traffic on port 82 in addi on to 
the standard ports. 
3. Verifying the change 
The third command semanage port -l | grep http again checks the h p ports. The 
output now shows port 82 included along with the previously listed ports. 
4. Opening the firewall 
The next command firewall-cmd --permanent --add-port=82/tcp opens port 82 in 
the firewall. A firewall is a soware program that controls traffic in and out of a computer. By 
default, most firewalls block all incoming traffic and this command adds an excep on to allow 
traffic on port 82. The --permanent flag tells the firewall to make the change permanent across 
reboots. 
5. Reloading the firewall 
The command firewall-cmd --reload reloads the firewall configura on to accept the 
changes. 
6. Installing the Apache web server 
The next command dnf install httpd -y installs the Apache web server using the dnf 
package manager. Apache is a popular open-source web server that can be used to host websites. 
The -y flag tells dnf to assume yes to all prompts, which is useful for una ended installa ons. 
7. Star ng the Apache service 
3
The command systemctl start httpd starts the Apache web server. 
8. Enabling Apache at boot 
The command systemctl enable httpd tells the system to start Apache automa cally 
whenever the system boots. 
9. Restar ng Apache 
The command systemctl restart httpd restarts the Apache web server. This is useful if 
there were any configura on changes made that require the service to be restarted. 
10. Tes ng the web server 
The final command curl http://127.0.0.1 uses the curl command to test the web server. 
The curl command is a u lity for transferring data from or to a server. In this case, it is used to 
fetch the default web page from the web server running on the local machine (localhost - 
127.0.0.1). 
The successful output shows that the web server is up and running and listening on port 82 as 
configured.
# Output:
![image](https://github.com/user-attachments/assets/c2515231-f4ee-431f-839a-bcc1679d17e4)

# Result: 
Thus the SElinux has been configured successfully. 
