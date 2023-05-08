## LEVEL 09

---

For this level I have two files:

```shell
$ ls -l
total 12
-rwsr-sr-x 1 flag09 level09 7640 Mar  5  2016 level09
----r--r-- 1 flag09 level09   26 Mar  5  2016 token
$ cat token
f4kmm6p|=�p�n��DB�Du{��
```

I can only read token but I can execute level09. The disassemble code of level09 is long so I won't use gdb for this level09 and I will try to understand what this level09 does.

```shell
$ ./level09 "0123456789"
02468:<>@B
$ ./level09 "abcdef"
acegik
```

I understand that level09 modifies the string as below.

| Input          | a  | b  | c   | d   | e   | f   | g   | h   | i   |
|----------------|----|----|-----|-----|-----|-----|-----|-----|-----|
| Input (ascii)  | 97 | 98 | 99  | 100 | 101 | 102 | 103 | 104 | 105 |
| Output         | a  | c  | e   | g   | i   | k   | m   | o   | q   |
| Output (ascii) | 97 | 99 | 101 | 103 | 105 | 107 | 109 | 111 | 113 |
|                | 0  | 1  | 2   | 3   | 4   | 5   | 6   | 7   | 8   |

---

So to get the original string of `token` we need to take each caracter and substract the position of the caracter in the string.

```shell
$ hexdump -C token
00000000  66 34 6b 6d 6d 36 70 7c  3d 82 7f 70 82 6e 83 82  |f4kmm6p|=..p.n..|
00000010  44 42 83 44 75 7b 7f 8c  89 0a                    |DB.Du{....|
0000001a
```

So I convert each character of this output in decimal.

```
102 52 107 109 109 54 112 124 61 130 127 112 130 110 131 130 68 66 131 68 117 123 127 140 137 10
```

Then I apply the reverse transformation.

```
102 51 105 106 105 49 106 117 53 121 117 101 118 97 117 115 52 49 113 49 97 102 105 117 113
```

When I convert this string in ascii, I have this result : `f3iji1ju5yuevaus41q1afiuq`

```shell
$ su flag09
Password: f3iji1ju5yuevaus41q1afiuq
Don't forget to launch getflag !
flag09@SnowCrash:~$ getflag
Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
```




