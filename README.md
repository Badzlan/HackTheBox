# HackTheBox - Starting Point Walkthrough
Created By [Badzlan Nur Dhabith](https://www.linkedin.com/in/badzlannurdhabith/){:target:_blank}

## Challenge : Meow
### Steps and Solutions
Pertama lakukan pengecekan apakah sudah ada tunnel ip target, dengan command :
```
ifconfig
```
```
┌──(root㉿localhost)-[~]
└─# ifconfig                                    
...
tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.10.14.56  netmask 255.255.254.0  destination 10.10.14.56
        inet6 dead:beef:2::1036  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::8e5c:baa2:365b:2370  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 500  (UNSPEC)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1  bytes 48 (48.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
jika sudah ada tun0 berarti kita sudah connect dengan target dengan openvpn
Lalu, cek apakah kita dan target sudah terhubung dengan command :
```
ping [ip target]
```

