######################
#------Rtr_Core------#
######################

int Loopback0
ip address 1.1.1.1 255.255.255.255
no sh

int GigabitEthernet0/0
ip address 123.13.11.9 255.255.255.252
no sh

int GigabitEthernet0/1
ip address 172.11.55.5 255.255.255.252
no sh

int GigabitEthernet0/2
ip address 200.125.12.6 255.255.255.252
no sh

router ospf 4
network 123.13.11.9 0.0.0.3 area 0
network 172.11.55.5 0.0.0.3 area 0
network 200.125.12.6 0.0.0.3 area 69
redistribute connected subnets


######################
#-------Rtr_Svc------#
######################

hostname Rtr_Svc

int Loopback0
ip address 3.3.3.3 255.255.255.255
no sh

int GigabitEthernet0/0
ip address 180.10.20.1 255.255.255.252
no sh

int GigabitEthernet0/1
ip address 125.12.25.14 255.255.255.252
no sh

int GigabitEthernet0/2
ip address 100.100.100.1 255.255.255.248
no sh

router ospf 2
network 180.10.20.1 0.0.0.3 area 0
network 125.12.25.14 0.0.0.3 area 0
network 100.100.100.1 0.0.0.7 area 23
redistribute connected subnets


######################
#-----Rtr_Arjuna-----#
######################

hostname Rtr_Arjuna

int Loopback0
ip address 4.4.4.4 255.255.255.255
no sh

int GigabitEthernet0/0
ip address 180.10.20.2 255.255.255.252
no sh

int GigabitEthernet0/1
ip address 172.11.55.6 255.255.255.252
no sh

int GigabitEthernet0/2
ip address 110.125.125.1 255.255.255.248
no sh

router ospf 3
network 180.10.20.2 0.0.0.3 area 0
network 172.11.55.6 0.0.0.3 area 0
network 110.125.125.1 0.0.0.7 area 10
redistribute connected subnets


######################
#------Rtr_Gayo------#
######################

hostname Rtr_Gayo

int GigabitEthernet0/0
ip address 125.12.25.13 255.255.255.252
no sh

int GigabitEthernet0/1
ip address 123.13.11.10 255.255.255.252
no sh

int GigabitEthernet0/2
ip address 10.10.10.1 255.255.255.252
no sh

int Loopback0
ip address 2.2.2.2 255.255.255.255
no sh

router ospf 1
network 125.12.25.13 0.0.0.3 area 0
network 123.13.11.10 0.0.0.3 area 0
network 10.10.10.1 0.0.0.3 area 23
redistribute connected subnets


######################
#----SW_Dist_Gayo----#
######################

hostname SW_Dist_Gayo

int FastEthernet0/1
ip address 10.10.10.2 255.255.255.252
no sh

int Vlan10
ip address 192.168.10.1 255.255.255.0
no sh

int Vlan11
ip address 192.168.11.1 255.255.255.0
no sh

int Vlan12
ip address 192.168.12.1 255.255.255.0
no sh

int Vlan13
ip address 192.168.13.1 255.255.255.0
no sh

int Vlan99
ip address 192.168.99.1 255.255.255.0
no sh

int Loopback0
ip address 5.5.5.5 255.255.255.255
no sh


#########################
#-------SW_Acc_SVC------#
#########################

hostname SW_Acc_SVC

router ospf 5
network 192.168.1.0 0.0.0.255 area 23
network 10.10.10.0 0.0.0.3 area 23
redistribute connected subnets


#########################
#-----SW_Acc_Gayo_1-----#
#########################

hostname SW_Acc_Gayo_1

vlan 10
name Accountant

vlan 11
name HRD

vlan 12
name Intern

vlan 13
name Guest

vlan 99
name Management


#########################
#-----SW_Acc_Gayo_2-----#
#########################

hostname SW_Acc_Gayo_2

vlan 10
name Accountant

vlan 11
name HRD

vlan 12
name Intern

vlan 13
name Guest

vlan 99
name Management


#########################
#----SW_Dist_Arjuna-----#
#########################

hostname SW_Dist_Arjuna
