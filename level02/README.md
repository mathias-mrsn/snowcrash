## LEVEL 02

---

```shell
$ ls
$ level02.pcap
```

We have a .pcap file. This file extention is used by network record so we can use `wireshark` to see the contents.

When I opne the file with wireshark, I see a list of TCP requests. Looking request by request I see that at the line 42 there is a request with as data `Password:`

Then at line 91 a message : `Log in incorrect ww wbugs login:`.

So I looked every requests from `59.233.235.218` and concatenated their data.

Here is the result : `ft_wandr\7f\7f\7fNDRel\7fL0L\0d`

`\7f` is `DEL` in ascii so if I delete the letters we have this result : `ft_waNDReL0L`

---

*Source :*

*https://www.reviversoft.com/en/file-extensions/pcap#:~:text=Since%20Wireshark%20can%20be%20accessed,Packet%20Square%20%2D%20Capedit%20and%20Ethereal.*
