# HackTheBox - Starting Point Walkthrough
Created By [Badzlan Nur Dhabith](https://www.linkedin.com/in/badzlannurdhabith/)

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
![]([https://github.com/Badzlan/htb/blob/main/image.png](https://carbon.now.sh/?bg=rgba%28255%2C255%2C255%2C1%29&t=3024-night&wt=sharp&l=text&width=680&ds=true&dsyoff=20px&dsblur=68px&wc=true&wa=false&pv=0px&ph=0px&ln=false&fl=1&fm=Hack&fs=14px&lh=133%25&si=false&es=2x&wm=false))
