========
Linux initial system examination (Ubuntu 18.04 LTS):
========

Use these steps to examine if linux box was compromised or not. Examples are from the mining attack on Jenkins server.
If attacker get a root access, everything can be masked with a rootkit.



#. Look at event log files at `/var/log`::

    sudo less /var/log/auth.log

    Examine any suspicious logevents deeper, wheather it is a normal even or not. For example``May 27 07:11:17 ci-test CRON[1783]: pam_unix(cron:session): session closed for user jenkins``

#. List security events::

   who
   last
   lastlog

Check that there are no suspisious users, logins ...

#. Examine network configuration:

    `arp -np`
    `route`

Check that network configuration looks ok.

#. List nerwork connections and related details:

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

#. List users:
  
`more /etc/passwd`

#. Look at scheduled jobs:

`more /etc/crontab`


#. List processes

`ps -aux`

#.Find recently modified files (affects lots of files!)

#. Look for suspicious files

These paths are commonly used for hiding scripts or binaries. Look for misspelled names, hidden files/directories, directories with filenames etc ... :
``
ls -al /tmp
ls -al /dev/shm
``
