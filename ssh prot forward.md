# `ssh` prot forward 

## 1.Local Forwarding

1.Local port forwarding allows you to forward traffic on a port of your local computer to the SSH server, which is forwarded to a destination server.

```
ssh  -Nf   -L 3306:127.0.0.1:3306  user@example.com
```

this is forwarding example.com port 3306 to you server 3306,

 <!---N      Do not execute a remote command-->

 <!---f  Requests ssh to go to background just before command execution.-->

2.you can forward multiple sets of ports in a single `ssh` command

```
ssh  -Nf  -L 6379:127.0.0.1:6379 -L 3306:127.0.0.1:3306 user@example.com
```



# 2.Remote port forwarding

1.A remotely forwarded port is just like a local one, but the directions are reversed. This time the TCP client is remote, its server is local, and a forwarded connection is initiated from the remote 

```
ssh -Nf -R 12181:127.0.0.1:80 user@example.com
```

the ssh server binds to the 12181 port on user@example.com, any traffic that is receives on the port is send to the ssh client on you local computer,which in turn forwards it to port 80 on 127.0.0.1 

# 3.Dynamic port forwarding

```
 ssh -Nf  -D 1980     user@exampel.com   -p 22  -o ServerAliveInterval=60 
```

The SSH client creates a SOCKS proxy   bind 127.0.0.1 port  4000 on your local computer. Any traffic sent to this port is sent to its destination through the SSH server.

web browsers allow you to use a SOCKS proxy.this is can cross the firewall!!!