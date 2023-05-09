## LEVEL 01

---

The first thing I do is check whether the user `flag01` has created a file.

```shell
$ find / -user flag01 2>/dev/null
$ ...
```

We don't have any file, so I will check if we can find the password in `/etc/passwd` or `/etc/shadow`.

```shell
$ cat /etc/shadow
$ cat: /etc/shadow: Permission denied
$ cat /etc/passwd
$ [...]
$ flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
$ [...]
```

I tried to use `42hDRfypTqqnw`, but it didn't work. So I searched on the internet and found that this is an encrypted password. However, I couldn't find any online tool to encrypt it, so I downloaded `John the Ripper` to crack the password.

```shell
$ brew install john
$ [...]
$ echo "42hDRfypTqqnw" > pass; john pass
$ Loaded 1 password hash (descrypt, traditional crypt(3) [DES 64/64])
$ Will run 4 OpenMP threads
$ Press 'q' or Ctrl-C to abort, almost any other key for status
$ abcdefg          (?)
$ 1g 0:00:00:00 100% 2/3 100.0g/s 819200p/s 819200c/s 819200C/s 123456..nutmegs
$ Use the "--show" option to display all of the cracked passwords reliably
$ Session completed
```

---

*Source:*

*https://www.varonis.com/blog/john-the-ripper*

*https://www.cyberciti.biz/faq/where-are-the-passwords-of-the-users-located-in-linux/*