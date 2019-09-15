enable
configure terminal
hostname S1
banner motd "ACESSO AUTORIZADO PARA O TI"
enable secret SenhaEnable
ip domain-name peachanddaisy.local
crypto key generate rsa general-keys modulus 1024
username Leonardo privilege 15 secret leozin
username estagiario privilege 1 secret leozin
line console 0
password SenhadaConsole
login
exit
service password-encryption
line vty 0 15
password SenhadaVTY
transport input ssh
exec-timeout 10
login local
exit
vlan 10
name TESTES
exit
vlan 20
name TELEMARKETING
exit
vlan 30
name CONSULTORES
exit 
vlan 40 
name RH
exit
interface F0/1
switchport mode access
switchport access vlan 10
exit
interface vlan 10
ip address 192.168.0.3 255.255.248.0
description REDE 1
no shutdown
exit
interface F0/10
switchport mode access
switchport access vlan 20
exit
interface vlan 20
ip address 192.168.8.3 255.255.252.0
description REDE 1
no shutdown 
exit
interface F0/18
switchport mode access
switchport access vlan 30
exit
interface vlan 30
ip address 192.168.12.3 255.255.254.0
description REDE 1
no shutdown 
exit
interface F0/23
switchport mode access
switchport access vlan 40
exit
interface vlan 40
ip address 192.168.14.3 255.255.255.128
description REDE 1
no shutdown 
exit
interface G0/1
switchport mode trunk
switchport trunk native vlan 88
switchport trunk allowed vlan 10,20,30,40
no shutdown
exit
ip default-gateway 192.168.0.1
do wr
