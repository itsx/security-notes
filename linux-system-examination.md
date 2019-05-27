# Linux initial system examination (Ubuntu 18.04 LTS):

### 1.Look at event log files at `/var/log`:

`sudo less /var/log/auth.log`

Examine any suspicious logevents deeper, wheather it is a normal even or not. For example:
`May 27 07:11:17 ci-test CRON[1783]: pam_unix(cron:session): session closed for user jenkins`

### 2.List security events:

`who`
`last`
`lastlog`

Check that there are no suspisioc users, logins.

### 3.Examine network configuration:

`arp -np`
`route print`

Check that this configuration looks ok.

### 4.List nerwork connections and related details:

`lsof -i`

Check any open connection if it is not a malware. For example:
```
trace     31646         jenkins   10u  IPv4 68791438      0t0  TCP ci-test.trigema.cz:49314->193.56.28.19:http-alt (ESTABLISHED)
-bash     31692         jenkins   11u  IPv4 68819778      0t0  TCP ci-test.trigema.cz:41716->static.27.12.130.94.clients.your-server.de:http (ESTABLISHED)
watchbog  31848         jenkins   11u  IPv4 68532581      0t0  TCP ci-test.trigema.cz:60472->ns3082757.ip-91-121-2.eu:http (ESTABLISHED)
watchbog  31848         jenkins   12u  IPv4 68831379      0t0  TCP ci-test.trigema.cz:51152->185.92.222.223.vultr.com:3333 (ESTABLISHED)

```

### 5.List users:

`more /etc/passwd`

### 6.Look at scheduled jobs:

`more /etc/crontab`


### List processes

`ps -aux`

### FInd recently modified files

``



