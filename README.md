# Lapres Modul 5 Jarkom 2020 - T1  
`"Repository dibuat untuk memenuhi tugas praktikum mata kuliah komunikasi data dan jaringan komputer tahun 2020."`  
  
Anggota:  
**Adeela Nurul Fadhila** `[05311840000001]` [@Rinnabel](https://github.com/Rinnabel)  
**Muhammad Ilya Asha Soegondo** `[05311840000010]` [@ilyaasha24](https://github.com/ilyaasha24/)  

Asisten:  
**Arino Jenynof** `[05111740000096]`  

Penguji:  
**Nur Muhammad Husnul Habib Yahya** `[05111740000094]`  

SOAL

NO 1

iptables -t nat -A POSTROUTING -o eth0 -s 192.160.0.0/16 -j SNAT --to-source 10.151.72.69

NO 2

iptables -A FORWARD -d DMZ/29 -p tcp --dport 22 -s IP TUNTAP -j DROP

NO 3

iptables -A INPUT -p ICMP -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP

NO 4

iptables -A INPUT -s 192.168.0.0/24 -m time --timestart 07:00 --timestop 17:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
iptables -A INPUT -s 192.168.0.0/24 -m time --timestart 17:01 --timestop 07:59 -j REJECT

NO 5

iptables -A INPUT -s 192.168.1.0/24 -m time --timestart 17:00 --timestop 07:00 --weekdays Mon,Tue,Wed,Thu,Fri,Sat,Sun -j ACCEPT
iptables -A INPUT -s 192.168.1.0/24 -m time --timestart 07:01 --timestop 16:59 -j REJECT

NO 7

iptables -N LOGGING 
iptables -A LOGGING -j LOG --log-prefix "IPTables-Dropped: " --log-level 6 
iptables -A LOGGING -j DROP

MOJO

subnet 10.151.83.160 netmask 255.255.255.248 {
}
subnet 192.168.2.0 netmask 255.255.255.252 {
}
subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.10 192.168.0.254;
    option routers 10.151.83.163;
    option broadcast-address 192.168.0.255;
    option domain-name-servers 10.151.83.162;
    Default-lease-time 600;
    max-lease-time 7200;
}
subnet 192.168.3.0 netmask 255.255.255.252 {
}
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.10 192.168.1.254;
    option routers 10.151.83.163
    option broadcast-address 192.168.1.255;
    option domain-name-servers  10.151.83.162;
    Default-lease-time 600;
    max-lease-time 7200;
}
