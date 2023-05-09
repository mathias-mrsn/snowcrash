## LEVEL 02

---

```shell
$ ls
$ level02.pcap
```

We have a .pcap file. This file extension is used for network recording, so we can use `wireshark` to view its contents.

When I opened the file with Wireshark, I saw a list of TCP requests. Going through them one by one, I noticed that on line 42 there was a request with the data `Password:`.

Then on line 91, a message appeared: `Log in incorrect ww wbugs login:`.

So I examined every request from `59.233.235.218` and concatenated their data.

Here is the result: `ft_wandr\7f\7f\7fNDRel\7fL0L\0d`

`\7f` represents `DEL` in ASCII, so if I remove these characters, we have this result: `ft_waNDReL0L`.

---

*Source:*

*https://www.reviversoft.com/en/file-extensions/pcap#:~:text=Since%20Wireshark%20can%20be%20accessed,Packet%20Square%20%2D%20Capedit%20and%20Ethereal.*