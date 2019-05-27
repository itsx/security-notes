# Linux initial system examination (Ubuntu 18.04 LTS):

Use these steps to examine if linux box was compromised or not. Examples are from the encountered mining attack on Jenkins server.
If attacker gets a root access, everything can be masked with a rootkit (use intuition). Also some operations affects
lots of files and can damage attacker fingerprint.


### 1. Look at event log files at `/var/log`:

`sudo less /var/log/auth.log`

Examine any suspicious logevents deeper, wheather it is a normal even or not. For example:
`May 27 07:11:17 ci-test CRON[1783]: pam_unix(cron:session): session closed for user jenkins`

### 2. List security events:
```
who
last
lastlog
```

Check that there are no suspisious users, logins ...

### 3. Examine network configuration:

`arp -np`
`route`

Check that network configuration looks ok.

### 4. List nerwork connections and related details:

`lsof -i`

Check all open connections if it is not a malware. For example:
```
trace     31646         jenkins   10u  IPv4 68791438      0t0  TCP ci-test.trigema.cz:49314->193.56.28.19:http-alt (ESTABLISHED)
-bash     31692         jenkins   11u  IPv4 68819778      0t0  TCP ci-test.trigema.cz:41716->static.27.12.130.94.clients.your-server.de:http (ESTABLISHED)
watchbog  31848         jenkins   11u  IPv4 68532581      0t0  TCP ci-test.trigema.cz:60472->ns3082757.ip-91-121-2.eu:http (ESTABLISHED)
watchbog  31848         jenkins   12u  IPv4 68831379      0t0  TCP ci-test.trigema.cz:51152->185.92.222.223.vultr.com:3333 (ESTABLISHED)

```
alternatively:
`netstat –nap`

### 5. List users:

`more /etc/passwd`

### 6. Look at scheduled jobs:

```
more /etc/crontab
ls -al /etc/cron.daily
ls -al /etc/cron.weekly
ls -al /etc/cron.monthly/
...
```

### 7. List processes

`ps -aux`

Look for weired process names, renamed processes, everything suspicious ...  

### 8. Find recently modified files (affects lots of files!)
```
ls -lat /
find / -mtime 2 -ls
```

### 9. Look for suspicious files

These paths are commonly used for hiding scripts or binaries. Look for misspelled names, hidden files/directories, directories which looks like files etc ... :
```
ls -al /tmp 
ls -al /dev/shm
```
### 10. Check root entry in /etc/shadows for possible root access attack:

```
root:*:17643:0:99999:7:::
```

Cheetsheets & resources:
https://zeltser.com/media/docs/security-incident-survey-cheat-sheet.pdf
http://www.deer-run.com/~hal/MWVLUG-detecting.pdf





