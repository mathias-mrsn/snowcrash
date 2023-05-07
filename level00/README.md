## LEVEL 00

---

First we need to show every files created by the user `flag00`

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

This key does not work so I enter the string it on Google. The first website
`
Chiffre de César - Déchiffrer, Coder, Décoder en Ligne
`
so I use this website to decrypt the string and here is the results.

```
[...]
(11)|(15) : nottoohardhere
[...]
```

We can now use this key to log to the `flag00` user.