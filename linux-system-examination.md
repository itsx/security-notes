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


### 5.List users:

`more etc/passwd`

### 6.Look at scheduled jobs:

`more etc/crontab`


### List processes

`ps -aux`

### FInd recently modified files

``



