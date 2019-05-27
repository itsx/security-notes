# Linux initial system examination:

### 1.Look at event log files `/var/log`:

`sudo less /var/log/auth.log`

Examine any suspicious logevents deeper,wheather it is a normal even or not. For example:
`May 27 07:11:17 ci-test CRON[1783]: pam_unix(cron:session): session closed for user jenkins`

### 2.List security events:

`who`
`last`
`lastlog`

### 3.Examine network configuration:

`arp -np`
`route print`



