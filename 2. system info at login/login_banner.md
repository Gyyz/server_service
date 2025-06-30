# 1. Customize the Pre-login Banner (/etc/issue.net)

## 1.1 Edit the /etc/issue.net

```bash
sudo vi /etc/issue.net
```

## 1.2 add message

```
Add your desired message and/or escape codes. For example:

*********************************************************
* Welcome to My Awesome Ubuntu Server!                  *
* *
* This system is for authorized users only.             *
* Unauthorized access is strictly prohibited.           *
* *
* Server Hostname: \h                                   *
* Current Time: \t                                      *
*********************************************************
```
## 1.3 Enable the banner in SSH:

```bash
sudo vi /etc/ssh/sshd_config
```
Find the line that starts with #Banner and uncomment it (remove the #) and ensure it points to /etc/issue.net:
```
Banner /etc/issue.net
```

## start the service
```bash
sudo systemctl restart ssh.service
```



# 2 Customize the Post-login MOTD (/etc/update-motd.d/)

## 2.1 Explore existing scripts:
```bash
ls -l /etc/update-motd.d/
```
## 2.2 Create your own custom MOTD script:
```bash
sudo nano /etc/update-motd.d/99-my-custom-info
```

## 2.3 add script content
```bash
#!/bin/bash

echo "------------------------------------------------------"
echo "  Server: $(hostname)"
echo "  OS: $(lsb_release -ds)"
echo "  Kernel: $(uname -r)"
echo "  Uptime: $(uptime -p)"
echo "------------------------------------------------------"
echo "  Disk Usage: $(df -h / | awk 'NR==2 {print $5 " of " $2 " used"}')"
echo "  Memory Usage: $(free -h | awk 'NR==2 {print $3 " / " $2 " (" sprintf("%.1f", $3/$2*100) "%)"}')"
echo "  Logged in users: $(who | awk '{print $1}' | sort | uniq | tr '\n' ' ')"
echo "------------------------------------------------------"
```



## 2.4 using open-source package `neofetch`
```
sudo apt update
sudo apt install neofetch
```

In your `.bashrc` or `.zshrc`
```
#!/bin/bash
/usr/bin/neofetch
```

## 2.5 make the script executable
```
sudo chmod +x /etc/update-motd.d/99-my-custom-info
```

## 2.6 test the MOTD scripts

```
sudo run-parts /etc/update-motd.d/
```

