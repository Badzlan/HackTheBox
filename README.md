# HackTheBox - Starting Point Walkthrough
Created By [Badzlan Nur Dhabith](https://www.linkedin.com/in/badzlannurdhabith/)

## Challenge : Meow
### Steps and Solutions
Pertama lakukan pengecekan apakah sudah ada tunnel ip target, dengan command :
```
ifconfi
```
jika sudah ada tun0 berarti kita sudah connect dengan target dengan openvpn

Lalu, cek apakah kita dan target sudah terhubung, dengan command :
```
ping [ip target]
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
