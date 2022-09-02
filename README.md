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

Lalu, cek apakah kita dan target sudah terhubung, dengan command :
```
ping [ip target]
```

```
┌──(root㉿localhost)-[~]
└─# ping 10.129.49.229
PING 10.129.49.229 (10.129.49.229) 56(84) bytes of data.
64 bytes from 10.129.49.229: icmp_seq=1 ttl=63 time=253 ms
64 bytes from 10.129.49.229: icmp_seq=3 ttl=63 time=268 ms
64 bytes from 10.129.49.229: icmp_seq=4 ttl=63 time=257 ms
64 bytes from 10.129.49.229: icmp_seq=5 ttl=63 time=255 ms
--- 10.129.49.229 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4021ms
rtt min/avg/max/mdev = 253.414/258.182/267.999/5.776 ms
```
Selanjutnya, lakukan scanning port target untuk melihat port dan service yang open, dengan command :
```
nmap -sV [ip target]
```
dari hasil scanning terlihat bahwa port yang open adalah port 23 dengan service telnet

Kemudian, kita coba telnet target untuk melihat file dan direktori target menggunakan command :
```
telnet [ip target]
```
login sebagai root agar bisa masuk tanpa password

Selanjutnya, kita coba lihat list file dan direktori target dengan command :
```
ls
```
ternyata ada file bernama flag.txt, lalu open file tersebut dengan command :
``
`cat [nama file]
```
