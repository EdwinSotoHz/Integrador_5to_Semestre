# Integrador_5to_Semestre

---
## DHCP Stateless
<details> 
    <summary>
        Configuraciones Switch S1
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################


    </pre>
</details>

<details> 
    <summary>
        Configuraciones Switch S2
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################

    </pre>
</details>

<details> 
    <summary>
        Configuraciones Switch S3
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################

    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router R1
    </summary>
    <pre>

    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router R3
    </summary>
    <pre>

    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router RA
    </summary>
    <pre>

    </pre>
</details>

---

## DHCP Stateful
# `Correjir SSH y verificar Gateway`
<details> 
    <summary>
        Configuraciones Switch S4
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################
S4(config)# hostname S4
S4(config)# enable password cisco
S4(config)# enable secret tics
S4(config)# vlan 10
S4(config-vlan)# name Docentes
S4(config-vlan)# exit
S4(config)# vlan 20
S4(config-vlan)# name Estudiantes
S4(config-vlan)# exit
S4(config)# vlan 30
S4(config-vlan)# name Admin
S4(config-vlan)# exit
S4(config)# vlan 40
S4(config-vlan)# name Native
S4(config-vlan)# exit
S4(config)# interface vlan 30
S4(config-if)# no ip address
S4(config-if)# ipv6 address 2001:db8:3c4d:55::4/64
S4(config-if)# no shutdown
S4(config-if)# exit
S4(config)# interface range f 0/1-24
S4(config-if-range)# switchport mode access
S4(config-if-range)# switchport access vlan 40
S4(config-if-range)# exit
S4(config)# interface range g 0/1-2
S4(config-if-range)# switchport mode access
S4(config-if-range)# switchport access vlan 40
S4(config-if-range)# exit
S4(config)# interface range f 0/7,f 0/8
S4(config-if-range)# switchport mode access
S4(config-if-range)# switchport access vlan 10
S4(config-if-range)# switchport port-security
S4(config-if-range)# switchport port-security maximum 1
S4(config-if-range)# switchport port-security mac-address sticky
S4(config-if-range)# switchport port-security violation shutdown
S4(config-if-range)# no shutdown
S4(config-if-range)# exit
S4(config)# interface range f 0/9,f 0/12
S4(config-if-range)# switchport mode access
S4(config-if-range)# switchport access vlan 20
S4(config-if-range)# switchport port-security
S4(config-if-range)# switchport port-security maximum 1
S4(config-if-range)# switchport port-security mac-address sticky
S4(config-if-range)# switchport port-security violation shutdown
S4(config-if-range)# no shutdown
S4(config-if-range)# exit
S4(config)# interface f 0/24
S4(config-if)# switchport mode access
S4(config-if)# switchport access vlan 40
S4(config-if)# switchport port-security
S4(config-if)# switchport port-security maximum 1
S4(config-if)# switchport port-security mac-address sticky
S4(config-if)# switchport port-security violation shutdown
S4(config-if)# no shutdown
S4(config-if)# exit
S4(config)# interface range f 0/1-3
S4(config-if-range)# channel-group 1 mode on
S4(config-if-range)# no shutdown
S4(config-if-range)# exit
S4(config)# interface port-channel 1
S4(config-if)# switchport mode trunk
S4(config-if)# switchport trunk allowed vlan 10,20,30,40
S4(config-if)# switchport trunk native vlan 40
S4(config-if)# no shutdown
S4(config-if)# exit
S4(config)# interface range f 0/4-6
S4(config-if-range)# channel-group 2 mode desirable
S4(config-if-range)# no shutdown
S4(config-if-range)# exit
S4(config)# interface port-channel 2
S4(config-if)# switchport mode trunk
S4(config-if)# switchport trunk allowed vlan 10,20,30,40
S4(config-if)# switchport trunk native vlan 40
S4(config-if)# no shutdown
S4(config-if)# exit
S4(config)# interface g 0/1
S4(config-if)# switchport mode trunk
S4(config-if)# switchport trunk allowed vlan 10,20,30,40
S4(config-if)# switchport trunk native vlan 40
S4(config-if)# no shutdown
S4(config-if)# exit
S4(config)# username admin password admin
S4(config)# ip domain-name itsoeh.edu
S4(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
S4(config)# line vty 0 15
S4(config-line)# transport input all
S4(config-line)# login local
S4(config-line)# exit
    </pre>
</details>

<details> 
    <summary>
        Configuraciones Switch S5
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################
S5(config)# hostname S5
S5(config)# enable password cisco
S5(config)# enable secret tics
S5(config)# vlan 10
S5(config-vlan)# name Docentes
S5(config-vlan)# exit
S5(config)# vlan 20
S5(config-vlan)# name Estudiantes
S5(config-vlan)# exit
S5(config)# vlan 30
S5(config-vlan)# name Admin
S5(config-vlan)# exit
S5(config)# vlan 40
S5(config-vlan)# name Native
S5(config-vlan)# exit
S5(config)# interface vlan 30
S5(config-if)# no ip address
S5(config-if)# ipv6 enable
S5(config-if)# ipv6 address 2001:db8:3c4d:55::5/64
S5(config-if)# no shutdown
S5(config-if)# exit
S5(config)# interface range f 0/1-24
S5(config-if-range)# switchport mode access
S5(config-if-range)# switchport access vlan 40
S5(config-if-range)# exit
S5(config)# interface range g 0/1-2
S5(config-if-range)# switchport mode access
S5(config-if-range)# switchport access vlan 40
S5(config-if-range)# exit
S5(config)# interface range f 0/7,f 0/8
S5(config-if-range)# switchport mode access
S5(config-if-range)# switchport access vlan 10
S5(config-if-range)# switchport port-security
S5(config-if-range)# switchport port-security maximum 1
S5(config-if-range)# switchport port-security mac-address sticky
S5(config-if-range)# switchport port-security violation shutdown
S5(config-if-range)# no shutdown
S5(config-if-range)# exit
S5(config)# interface range f 0/9,f 0/12
S5(config-if-range)# switchport mode access
S5(config-if-range)# switchport access vlan 20
S5(config-if-range)# switchport port-security
S5(config-if-range)# switchport port-security maximum 1
S5(config-if-range)# switchport port-security mac-address sticky
S5(config-if-range)# switchport port-security violation shutdown
S5(config-if-range)# no shutdown
S5(config-if-range)# exit
S5(config)# interface f 0/24
S5(config-if)# switchport mode access
S5(config-if)# switchport access vlan 40
S5(config-if)# switchport port-security
S5(config-if)# switchport port-security maximum 1
S5(config-if)# switchport port-security mac-address sticky
S5(config-if)# switchport port-security violation shutdown
S5(config-if)# no shutdown
S5(config-if)# exit
S5(config)# interface range f 0/1-3
S5(config-if-range)# channel-group 1 mode passive
S5(config-if-range)# no shutdown
S5(config-if-range)# exit
S5(config)# interface port-channel 1
S5(config-if)# switchport mode trunk
S5(config-if)# switchport trunk allowed vlan 10,20,30,40
S5(config-if)# switchport trunk native vlan 40
S5(config-if)# no shutdown
S5(config-if)# exit
S5(config)# interface range f 0/4-6
S5(config-if-range)# channel-group 2 mode on
S5(config-if-range)# no shutdown
S5(config-if-range)# exit
S5(config)# interface port-channel 2
S5(config-if)# switchport mode trunk
S5(config-if)# switchport trunk allowed vlan 10,20,30,40
S5(config-if)# switchport trunk native vlan 40
S5(config-if)# no shutdown
S5(config-if)# exit
S5(config)# interface g 0/1
S5(config-if)# switchport mode trunk
S5(config-if)# switchport trunk allowed vlan 10,20,30,40
S5(config-if)# switchport trunk native vlan 40
S5(config-if)# no shutdown
S5(config-if)# exit
S5(config)# username admin password admin
S5(config)# ip domain-name itsoeh.edu
S5(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
S5(config)# line vty 0 15
S5(config-line)# transport input all
S5(config-line)# login local
S5(config-line)# exit
    </pre>
</details>

<details> 
    <summary>
        Configuraciones Switch S6
    </summary>
    <pre>
Switch(config)# sdm prefer dual-ipv4-and-ipv6 default
Switch# reload
System configuration has been modified. Save? [yes/no]:yes
######################################################################################################
S6(config)# hostname S6
S6(config)# enable password cisco
S6(config)# enable secret tics
S6(config)# vlan 10
S6(config-vlan)# name Docentes
S6(config-vlan)# exit
S6(config)# vlan 20
S6(config-vlan)# name Estudiantes
S6(config-vlan)# exit
S6(config)# vlan 30
S6(config-vlan)# name Admin
S6(config-vlan)# exit
S6(config)# vlan 40
S6(config-vlan)# name Native
S6(config-vlan)# exit
S6(config)# interface vlan 30
S6(config-if)# no ip address
S6(config-if)# ipv6 enable
S6(config-if)# ipv6 address 2001:db8:3c4d:55::6/64
S6(config-if)# no shutdown
S6(config-if)# exit
S6(config)# interface range f 0/1-24
S6(config-if-range)# switchport mode access
S6(config-if-range)# switchport access vlan 40
S6(config-if-range)# exit
S6(config)# interface range g 0/1-2
S6(config-if-range)# switchport mode access
S6(config-if-range)# switchport access vlan 40
S6(config-if-range)# exit
S6(config)# interface range f 0/7,f 0/8
S6(config-if-range)# switchport mode access
S6(config-if-range)# switchport access vlan 10
S6(config-if-range)# switchport port-security
S6(config-if-range)# switchport port-security maximum 1
S6(config-if-range)# switchport port-security mac-address sticky
S6(config-if-range)# switchport port-security violation shutdown
S6(config-if-range)# no shutdown
S6(config-if-range)# exit
S6(config)# interface range f 0/9,f 0/12
S6(config-if-range)# switchport mode access
S6(config-if-range)# switchport access vlan 20
S6(config-if-range)# switchport port-security
S6(config-if-range)# switchport port-security maximum 1
S6(config-if-range)# switchport port-security mac-address sticky
S6(config-if-range)# switchport port-security violation shutdown
S6(config-if-range)# no shutdown
S6(config-if-range)# exit
S6(config)# interface f 0/24
S6(config-if)# switchport mode access
S6(config-if)# switchport access vlan 40
S6(config-if)# switchport port-security
S6(config-if)# switchport port-security maximum 1
S6(config-if)# switchport port-security mac-address sticky
S6(config-if)# switchport port-security violation shutdown
S6(config-if)# no shutdown
S6(config-if)# exit
S6(config)# interface range f 0/1-3
S6(config-if-range)# channel-group 1 mode active
S6(config-if-range)# no shutdown
S6(config-if-range)# exit
S6(config)# interface port-channel 1
S6(config-if)# switchport mode trunk
S6(config-if)# switchport trunk allowed vlan 10,20,30,40
S6(config-if)# switchport trunk native vlan 40
S6(config-if)# no shutdown
S6(config-if)# exit
S6(config)# interface range f 0/4-6
S6(config-if-range)# channel-group 2 mode auto
S6(config-if-range)# no shutdown
S6(config-if-range)# exit
S6(config)# interface port-channel 2
S6(config-if)# switchport mode trunk
S6(config-if)# switchport trunk allowed vlan 10,20,30,40
S6(config-if)# switchport trunk native vlan 40
S6(config-if)# no shutdown
S6(config-if)# exit
S6(config)# username admin password admin
S6(config)# ip domain-name itsoeh.edu
S6(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
S6(config)# line vty 0 15
S6(config-line)# transport input all
S6(config-line)# login local
S6(config-line)# exit
    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router R3
    </summary>
    <pre>
R3(config)# hostname R3
R3(config)# enable password cisco
R3(config)# enable secret tics
R3(config)# interface g 0/1
R3(config-if)# no shutdown
R3(config-if)# exit
R3(config)# ipv6 unicast-routing
R3(config)# ipv6 dhcp pool DHCP-STATEFUL-10
R3(dhcpv6-pool)# address prefix 2001:db8:3c4d:10::/64
R3(dhcpv6-pool)# domain-name tics.edu.mx
R3(dhcpv6-pool)# exit
R3(config)# ipv6 dhcp pool DHCP-STATEFUL-20
R3(dhcpv6-pool)# address prefix 2001:db8:3c4d:20::/64
R3(dhcpv6-pool)# domain-name tics.edu.mx
R3(dhcpv6-pool)# exit
R3(config)# ipv6 dhcp pool DHCP-STATEFUL-30
R3(dhcpv6-pool)# address prefix 2001:db8:3c4d:30::/64
R3(dhcpv6-pool)# domain-name tics.edu.mx
R3(dhcpv6-pool)# exit
R3(config)# ipv6 dhcp pool DHCP-STATEFUL-40
R3(dhcpv6-pool)# address prefix 2001:db8:3c4d:40::/64
R3(dhcpv6-pool)# domain-name tics.edu.mx
R3(dhcpv6-pool)# exit
R3(config)# interface g 0/1.10
R3(config-subif)# encapsulation dot1Q 10
R3(config-subif)# no ip address
R3(config-subif)# ipv6 address 2001:db8:3c4d:10::/64 eui-64
R3(config-subif)# ipv6 enable
R3(config-subif)# ipv6 nd managed-config-flag
R3(config-subif)# ipv6 dhcp server DHCP-STATEFUL-10
R3(config-subif)# standby version 2
R3(config-subif)# standby 10 ipv6 autoconfig
R3(config-subif)# exit
R3(config)# interface g 0/1.20
R3(config-subif)# encapsulation dot1Q 20
R3(config-subif)# no ip address
R3(config-subif)# ipv6 address 2001:db8:3c4d:20::/64 eui-64
R3(config-subif)# ipv6 enable
R3(config-subif)# ipv6 nd managed-config-flag
R3(config-subif)# ipv6 dhcp server DHCP-STATEFUL-20
R3(config-subif)# standby version 2
R3(config-subif)# standby 20 ipv6 autoconfig
R3(config-subif)# exit
R3(config)# interface g 0/1.30
R3(config-subif)# encapsulation dot1Q 30
R3(config-subif)# no ip address
R3(config-subif)# ipv6 address 2001:db8:3c4d:30::/64 eui-64
R3(config-subif)# ipv6 enable
R3(config-subif)# ipv6 nd managed-config-flag
R3(config-subif)# ipv6 dhcp server DHCP-STATEFUL-30
R3(config-subif)# standby version 2
R3(config-subif)# standby 30 ipv6 autoconfig
R3(config-subif)# exit
R3(config)# interface g 0/1.40
R3(config-subif)# encapsulation dot1Q 40 native
R3(config-subif)# no ip address
R3(config-subif)# ipv6 address 2001:db8:3c4d:40::/64 eui-64
R3(config-subif)# ipv6 enable
R3(config-subif)# ipv6 nd managed-config-flag
R3(config-subif)# ipv6 dhcp server DHCP-STATEFUL-40
R3(config-subif)# standby version 2
R3(config-subif)# standby 40 ipv6 autoconfig
R3(config-subif)# exit
R3(config)# username admin password admin
R3(config)# ip domain-name itsoeh.edu
R3(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
R3(config)# line vty 0 15
R3(config-line)# transport input all
R3(config-line)# login local
R3(config-line)# exit
    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router R4
    </summary>
    <pre>
R4(config)# hostname R4
R4(config)# enable password cisco
R4(config)# enable secret tics
R4(config)# configure terminal
R4(config)# interface g 0/1
R4(config-if)# no shutdown
R4(config-if)# exit
R4(config)# ipv6 unicast-routing
R4(config)# ipv6 dhcp pool DHCP-STATEFUL-10
R4(dhcpv6-pool)# address prefix 2001:db8:3c4d:10::/64
R4(dhcpv6-pool)# domain-name tics.edu.mx
R4(dhcpv6-pool)# exit
R4(config)# ipv6 dhcp pool DHCP-STATEFUL-20
R4(dhcpv6-pool)# address prefix 2001:db8:3c4d:20::/64
R4(dhcpv6-pool)# domain-name tics.edu.mx
R4(dhcpv6-pool)# exit
R4(config)# ipv6 dhcp pool DHCP-STATEFUL-30
R4(dhcpv6-pool)# address prefix 2001:db8:3c4d:30::/64
R4(dhcpv6-pool)# domain-name tics.edu.mx
R4(dhcpv6-pool)# exit
R4(config)# ipv6 dhcp pool DHCP-STATEFUL-40
R4(dhcpv6-pool)# address prefix 2001:db8:3c4d:40::/64
R4(dhcpv6-pool)# domain-name tics.edu.mx
R4(dhcpv6-pool)# exit
R4(config)# interface g 0/1.10
R4(config-subif)# encapsulation dot1Q 10
R4(config-subif)# no ip address
R4(config-subif)# ipv6 nd managed-config-flag
R4(config-subif)# ipv6 address 2001:db8:3c4d:10::/64 eui-64
R4(config-subif)# ipv6 enable
R4(config-subif)# ipv6 dhcp server DHCP-STATEFUL-10
R4(config-subif)# standby version 2
R4(config-subif)# standby 10 priority 150
R4(config-subif)# standby 10 preempt
R4(config-subif)# standby 10 ipv6 autoconfig
R4(config-subif)# exit
R4(config)# interface g 0/1.20
R4(config-subif)# encapsulation dot1Q 20
R4(config-subif)# no ip address
R4(config-subif)# ipv6 address 2001:db8:3c4d:20::/64 eui-64
R4(config-subif)# ipv6 enable
R4(config-subif)# ipv6 nd managed-config-flag
R4(config-subif)# ipv6 dhcp server DHCP-STATEFUL-20
R4(config-subif)# standby version 2
R4(config-subif)# standby 20 priority 150
R4(config-subif)# standby 20 preempt
R4(config-subif)# standby 20 ipv6 autoconfig
R4(config-subif)# exit
R4(config)# interface g 0/1.30
R4(config-subif)# encapsulation dot1Q 30
R4(config-subif)# no ip address
R4(config-subif)# ipv6 address 2001:db8:3c4d:30::/64 eui-64
R4(config-subif)# ipv6 enable
R4(config-subif)# ipv6 nd managed-config-flag
R4(config-subif)# ipv6 dhcp server DHCP-STATEFUL-30
R4(config-subif)# standby version 2
R4(config-subif)# standby 30 priority 150
R4(config-subif)# standby 30 preempt
R4(config-subif)# standby 30 ipv6 autoconfig
R4(config-subif)# exit
R4(config)# interface g 0/1.40
R4(config-subif)# encapsulation dot1Q 40 native
R4(config-subif)# no ip address
R4(config-subif)# ipv6 address 2001:db8:3c4d:40::/64 eui-64
R4(config-subif)# ipv6 enable
R4(config-subif)# ipv6 nd managed-config-flag
R4(config-subif)# ipv6 dhcp server DHCP-STATEFUL-40
R4(config-subif)# standby version 2
R4(config-subif)# standby 40 priority 150
R4(config-subif)# standby 40 preempt
R4(config-subif)# standby 40 ipv6 autoconfig
R4(config-subif)# exit
R4(config)# username admin password admin
R4(config)# ip domain-name itsoeh.edu
R4(config)# crypto key generate rsa
How many bits in the modulus [512]: 1024
R4(config)# line vty 0 15
R4(config-line)# transport input all
R4(config-line)# login local
R4(config-line)# exit
    </pre>
</details>

<details> 
    <summary>
        Configuraciones Router RB
    </summary>
    <pre>

    </pre>
</details>

---