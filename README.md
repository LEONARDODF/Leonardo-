enable
configure terminal
hostname R4
banner motd "ACESSO PARA PESSOAS AUTORIZADAS”
enable secret SenhaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
line vty 0 15
password SenhadaVTY
login
transport input ssh
exec-timeout 10
exit
username Leonardo privilege 15 secret leozin
username Estagiario privilege 1 secret leozinho
line console 0
password SenhadaConsole
login
exit
service password-encryption
interface gigabitEthernet 0/1
ip address 172.16.0.1 255.240.0.0
description REDE 172.16.0.0/12
no shutdown
exit
interface gigabitEthernet 0/1.88
encapsulation dot1Q 88
ip address 172.16.0.1 255.240.0.0
description REDE 172.16.0.0/12
no shutdown
exit
interface gigabitEthernet 0/1.88
encapsulation dot1Q 88
ip address 172.32.0.1 255.254.0.0
description REDE 172.32.0.0/15
no shutdown
exit
interface gigabitEthernet 0/1.200
encapsulation dot1Q 200
ip address 172.34.0.1 255.255.192.0
description REDE 172.34.0.0/18
no shutdown
exit
interface gigabitEthernet 0/1.90
encapsulation dot1Q 90
ip address 172.34.64.1
description REDE 172.34.64.0/23
no shutdown
exit
interface serial 0/0/1
ip address 201.187.89.14 255.255.255.252
description REDE 201.187.89.12/30
no shutdown
interface serial 0/1/1
ip address 201.187.89.18 255.255.255.252
description REDE 201.187.89.16/30
no shutdown
interface serial 0/0/0
ip address 201.187.89.2 255.255.255.252
description REDE 201.187.89.0/30
no shutdown
exit
ip route 192.168.0.0 255.255.224.0 201.187.89.1
ip route 192.168.0.0 255.255.224.0 201.187.89.13
ip route 192.168.0.0 255.255.224.0 201.187.89.17
ip route 192.168.32.0 255.255.248.0 201.187.89.1
ip route 192.168.32.0 255.255.248.0 201.187.89.13
ip route 192.168.32.0 255.255.248.0 201.187.89.17
ip route 10.0.0.0 255.0.0.0 201.187.89.1
ip route 10.0.0.0 255.0.0.0 201.187.89.13
ip route 10.0.0.0 255.0.0.0 201.187.89.17
ip route 201.187.89.4 255.255.255.252 201.187.89.1
ip route 201.187.89.4 255.255.255.252 201.187.89.13
ip route 201.187.89.4 255.255.255.252 201.187.89.17
ip route 201.187.89.8 255.255.255.252 201.187.89.1
ip route 201.187.89.8 255.255.255.252 201.187.89.13
ip route 201.187.89.8 255.255.255.252 201.187.89.17
ip route 201.187.89.20 255.255.255.252 201.187.89.1
ip route 201.187.89.20 255.255.255.252 201.187.89.13
ip route 201.187.89.20 255.255.255.252 201.187.89.17
do wr
