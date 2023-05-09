## LEVEL 00

---

Firstly, we need to display all the files created by the user `flag00`.

```shell
$ find / -user flag00
$ [...]
$ /usr/sbin/john
$ [...]
```

```shell
cat /usr/sbin/john
cdiiddwpgswtgt
```

This key does not work, so I searched for it on Google. The first website that appears is 

`Caesar Cipher - Decrypt, Encode, Decode online`

So I used this website to decrypt the string, and here are the results.

```
[...]
(11)|(15) : nottoohardhere
[...]
```

We can now use this key to log in as the `flag00` user."\