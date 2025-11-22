<details> 
    <summary>
        Switch S1
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S1
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S1 #
service password-encryption
```

```ini
vlan 15
 name AdminStaff
 exit
vlan 45
 name Users
 exit
vlan 55
 name Adminstrative
 exit
vlan 65
 name Native
 exit
```

```ini
interface vlan 55
 no ip address
 ipv6 address 2001:db8:cafe:55::11/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 65
 shutdown
 exit

interface range g 0/1-2
 switchport mode access
 switchport access vlan 65
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 15
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/9,f 0/12
 switchport mode access
 switchport access vlan 45
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface f 0/24
 switchport mode access
 switchport access vlan 65
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/1-3
 channel-group 1 mode on
 no shutdown
 exit
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
interface range f 0/4-6
 channel-group 2 mode desirable
 no shutdown
 exit
interface port-channel 2
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```
</details>

<details> 
    <summary>
        Switch S2
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S2
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S2 #
service password-encryption
```

```ini
vlan 15
 name AdminStaff
 exit
vlan 45
 name Users
 exit
vlan 55
 name Adminstrative
 exit
vlan 65
 name Native
 exit
```

```ini
interface vlan 55
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:cafe:55::12/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 65
 shutdown
 exit

interface range g 0/1-2
 switchport mode access
 switchport access vlan 65
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 15
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/9,f 0/12
 switchport mode access
 switchport access vlan 45
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface f 0/24
 switchport mode access
 switchport access vlan 65
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/1-3
 channel-group 1 mode passive
 no shutdown
 exit
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
interface range f 0/4-6
 channel-group 2 mode on
 no shutdown
 exit
interface port-channel 2
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```

</details>

<details> 
    <summary>
        Switch S3
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S3
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S3 #
service password-encryption
```

```ini
vlan 15
 name AdminStaff
 exit
vlan 45
 name Users
 exit
vlan 55
 name Adminstrative
 exit
vlan 65
 name Native
 exit
```

```ini
interface vlan 55
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:cafe:55::13/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 65
 shutdown
 exit
interface range g 0/1-2
 switchport mode access
 switchport access vlan 65
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 15
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/9,f 0/12
 switchport mode access
 switchport access vlan 45
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface f 0/24
 switchport mode access
 switchport access vlan 65
 switchport port-security 
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
 no shutdown
 exit
```

```ini
interface range f 0/1-3
 channel-group 1 mode on
 no shutdown
 exit
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
interface range f 0/4-6
 channel-group 2 mode desirable
 no shutdown
 exit
interface port-channel 2
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```

</details>

<details> 
    <summary>
        Router R1
    </summary>

```ini
enable
configure terminal

no logging console

hostname R1
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R1 #
service password-encryption
```

```ini
interface g 0/1
 no shutdown
 exit
```

```ini
ipv6 unicast-routing
ipv6 dhcp pool DHCP-STATELESS-15
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-45
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-55
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-65
 domain-name tics.edu.mx
 exit
```

```ini
interface g 0/1.15
 encapsulation dot1Q 15
 no ip address
 ipv6 address 2001:db8:cafe:15::1/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-15
 no shutdown
 standby version 2
 standby 15 ipv6 autoconfig
 standby 15 priority 150
 standby 15 preempt
 exit
```

```ini
interface g 0/1.45
 encapsulation dot1Q 45
 no ip address
 ipv6 address 2001:db8:cafe:45::1/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-45
 no shutdown
 standby version 2
 standby 45 priority 150
 standby 45 preempt
 standby 45 ipv6 autoconfig
 exit
```

```ini
interface g 0/1.55
 encapsulation dot1Q 55
 no ip address
 ipv6 address 2001:db8:cafe:55::1/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-55
 no shutdown
 standby version 2
 standby 55 ipv6 autoconfig
 standby 55 priority 150
 standby 55 preempt
 exit
```

```ini
interface g 0/1.65
 encapsulation dot1Q 65 native
 no ip address
 ipv6 address 2001:db8:cafe:65::1/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-65
 no shutdown
 standby version 2
 standby 65 ipv6 autoconfig
 standby 65 priority 150
 standby 65 preempt
 exit
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```

```ini
interface s 0/0/1
 no ip address
 ipv6 address 2001:db8:1:1::2/64
 ipv6 enable
 no shutdown
 exit
ipv6 route ::/0 s0/0/1 2001:db8:1:1::1
```

</details>

<details> 
    <summary>
        Router R2
    </summary>

```ini
enable
configure terminal

no logging console

hostname R2
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R2 #
service password-encryption
```

```ini
interface g 0/1
 no shutdown
 exit
```

```ini
ipv6 unicast-routing
ipv6 dhcp pool DHCP-STATELESS-15
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-45
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-55
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATELESS-65
 domain-name tics.edu.mx
 exit
```

```ini
interface g 0/1.15
 encapsulation dot1Q 15
 no ip address
 ipv6 address 2001:db8:cafe:15::2/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-15
 no shutdown
 standby version 2
 standby 15 ipv6 autoconfig
 standby 15 priority 100
 exit
```

```ini
interface g 0/1.45
 encapsulation dot1Q 45
 no ip address
 ipv6 address 2001:db8:cafe:45::2/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-45
 no shutdown
 standby version 2
 standby 45 ipv6 autoconfig
 standby 45 priority 100
 exit
```

```ini
interface g 0/1.55
 encapsulation dot1Q 55
 no ip address
 ipv6 address 2001:db8:cafe:55::2/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-55
 no shutdown
 standby version 2
 standby 55 ipv6 autoconfig
 standby 55 priority 100
 exit
```

```ini
interface g 0/1.65
 encapsulation dot1Q 65 native
 no ip address
 ipv6 address 2001:db8:cafe:65::2/64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-65
 no shutdown
 standby version 2
 standby 65 priority 100
 standby 65 ipv6 autoconfig
 exit
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```

```ini
interface s 0/0/0
 no ip address
 ipv6 address 2001:db8:2:2::2/64
 ipv6 enable
 no shutdown
 exit
ipv6 route ::/0 s0/0/1 2001:db8:2:2::1
```

</details>

<details> 
    <summary>
        Router RA
    </summary>

```ini
enable
configure terminal

no logging console

hostname RA
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado RA #
service password-encryption
```

```ini
ipv6 unicast-routing
interface s 0/0/1
 no ip address
 ipv6 address 2001:db8:1:1::1/64
 ipv6 enable
 clock rate 64000
 no shutdown
 exit
interface s 0/0/0
 no ip address
 ipv6 address 2001:db8:2:2::1/64
 ipv6 enable
 clock rate 64000
 no shutdown
 exit
interface g 0/1
 no ip address
 ipv6 address 2001:db8:7:7::1/64
 ipv6 address fe80::1 link-local
 no shutdown
 exit

ipv6 route ::/0 s0/0/1 2001:db8:1:1::2
ipv6 route ::/0 s0/0/0 2001:db8:2:2::2
ipv6 route ::/0 2001:DB8:7:7::2

ipv6 route ::/0 2001:DB8:7:7::3
ipv6 route ::/0 2001:DB8:7:7::4
```

```ini
username admin password admin
ip domain-name itsoeh.edu
crypto key generate rsa
    1024
line vty 0 15 
 transport input ssh
 login local
 exit
```

</details>

Configuración de prueba para VLAN administrativa 55 (Switchs)
```ini
interface f 0/15
 switchport mode access
 switchport access vlan 55
 no shut
 exit
```

Volver a activar los logs de consola (hacerlo al final)
```ini
logging console
```