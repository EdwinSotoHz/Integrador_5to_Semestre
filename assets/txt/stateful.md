<details> 
    <summary>
        <h3> Switch S4 </h3>
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S4
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S4 #
service password-encryption
```

```ini
vlan 10
 name AdminStaff
 exit
vlan 20
 name Users
 exit
vlan 30
 name Adminstrative
 exit
vlan 40
 name Native
 exit
```

```ini
interface vlan 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::14/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 40
 shutdown
 exit

interface range g 0/1-2
 switchport mode access
 switchport access vlan 40
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 10
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
 switchport access vlan 20
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
 switchport access vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
 no shutdown
 exit
```

```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
        <h3> Switch S5 </h3>
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S5
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S5 #
service password-encryption
```

```ini
vlan 10
 name AdminStaff
 exit
vlan 20
 name Users
 exit
vlan 30
 name Adminstrative
 exit
vlan 40
 name Native
 exit
```

```ini
interface vlan 30
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:3c4d:30::15/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 40
 shutdown
 exit

interface range g 0/1-2
 switchport mode access
 switchport access vlan 40
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 10
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
 switchport access vlan 20
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
 switchport access vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
 no shutdown
 exit
```

```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
        <h3> Switch S6 </h3>
    </summary>

```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

```ini
enable
configure terminal

no logging console

hostname S6
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S6 #
service password-encryption
```

```ini
vlan 10
 name AdminStaff
 exit
vlan 20
 name Users
 exit
vlan 30
 name Adminstrative
 exit
vlan 40
 name Native
 exit
```

```ini
interface vlan 30
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:3c4d:30::16/64
 no shutdown
 exit
```

```ini
interface range f 0/1-24
 switchport mode access
 switchport access vlan 40
 shutdown
 exit
interface range g 0/1-2
 switchport mode access
 switchport access vlan 40
 exit
```

```ini
interface range f 0/7,f 0/8
 switchport mode access
 switchport access vlan 10
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
 switchport access vlan 20
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
 switchport access vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
        <h3> Router R3 </h3>
    </summary>

```ini
enable
configure terminal

no logging console

hostname R3
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R3 #
service password-encryption
```

```ini
interface g 0/1
 no shutdown
 exit
```

```ini
ipv6 unicast-routing
ipv6 dhcp pool DHCP-STATEFUL-10
 address prefix 2001:db8:3c4d:10::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-20
 address prefix 2001:db8:3c4d:20::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-30
 address prefix 2001:db8:3c4d:30::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-40
 address prefix 2001:db8:3c4d:40::/64
 domain-name tics.edu.mx
 exit
```

```ini
interface g 0/1.10
 encapsulation dot1Q 10
 no ip address
 ipv6 address 2001:db8:3c4d:10::1/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 10 ipv6 autoconfig
 standby 10 priority 100
 exit
```

```ini
interface g 0/1.20
 encapsulation dot1Q 20
 no ip address
 ipv6 address 2001:db8:3c4d:20::1/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 20 ipv6 autoconfig
 standby 20 priority 100
 exit
```

```ini
interface g 0/1.30
 encapsulation dot1Q 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::1/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 30 ipv6 autoconfig
 standby 30 priority 100
 exit
```

```ini
interface g 0/1.40
 encapsulation dot1Q 40 native
 no ip address
 ipv6 address 2001:db8:3c4d:40::1/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 40 priority 100
 standby 40 ipv6 autoconfig
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
 ipv6 address 2001:db8:3:3::2/64
 ipv6 enable
 no shutdown
 exit
ipv6 route ::/0 s0/0/1 2001:db8:3:3::1
```

</details>

<details> 
    <summary>
        <h3> Router R4 </h3>
    </summary>

```ini
enable
configure terminal

no logging console

hostname R4
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R4 #
service password-encryption
```

```ini
interface g 0/1
 no shutdown
 exit
```

```ini
ipv6 unicast-routing
ipv6 dhcp pool DHCP-STATEFUL-10
 address prefix 2001:db8:3c4d:10::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-20
 address prefix 2001:db8:3c4d:20::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-30
 address prefix 2001:db8:3c4d:30::/64
 domain-name tics.edu.mx
 exit
ipv6 dhcp pool DHCP-STATEFUL-40
 address prefix 2001:db8:3c4d:40::/64
 domain-name tics.edu.mx
 exit
```

```ini
interface g 0/1.10
 encapsulation dot1Q 10
 no ip address
 ipv6 address 2001:db8:3c4d:10::2/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 ipv6 dhcp server DHCP-STATEFUL-10
 no shutdown
 standby version 2
 standby 10 ipv6 autoconfig
 standby 10 priority 150
 standby 10 preempt
 exit
```

```ini
interface g 0/1.20
 encapsulation dot1Q 20
 no ip address
 ipv6 address 2001:db8:3c4d:20::2/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 ipv6 dhcp server DHCP-STATEFUL-20
 no shutdown
 standby version 2
 standby 20 priority 150
 standby 20 preempt
 standby 20 ipv6 autoconfig
 exit
```

```ini
interface g 0/1.30
 encapsulation dot1Q 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::2/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 ipv6 dhcp server DHCP-STATEFUL-30
 no shutdown
 standby version 2
 standby 30 ipv6 autoconfig
 standby 30 priority 150
 standby 30 preempt
 exit
```

```ini
interface g 0/1.40
 encapsulation dot1Q 40 native
 no ip address
 ipv6 address 2001:db8:3c4d:40::2/64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 ipv6 dhcp server DHCP-STATEFUL-40
 no shutdown
 standby version 2
 standby 40 ipv6 autoconfig
 standby 40 priority 150
 standby 40 preempt
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
 ipv6 address 2001:db8:4:4::2/64
 ipv6 enable
 no shutdown
 exit
ipv6 route ::/0 s0/0/0 2001:db8:4:4::1
```

</details>

<details> 
    <summary>
        <h3> Router RB </h3>
    </summary>

```ini
enable
configure terminal

no logging console

hostname RB
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado RB #
service password-encryption
```

```ini
ipv6 unicast-routing
interface s 0/0/1
 no ip address
 ipv6 address 2001:db8:3:3::1/64
 ipv6 enable
 no shutdown
 exit
interface s 0/0/0
 no ip address
 ipv6 address 2001:db8:4:4::1/64
 ipv6 enable
 no shutdown
 exit
interface g 0/1
 no ip address
 ipv6 address 2001:db8:7:7::2/64
 ipv6 address fe80::2 link-local
 no shutdown
 exit
 
ipv6 route ::/0 s0/0/1 2001:db8:3:3::2
ipv6 route ::/0 s0/0/0 2001:db8:4:4::2
ipv6 route 2001:db8:3c4d::/64 g0/1 fe80::1
```

</details>

Configuración de prueba para VLAN administrativa 30 (Switchs)
```ini
interface f 0/15
 switchport mode access
 switchport access vlan 30
 no shut
 exit
```

Volver a activar los logs de consola (hacerlo al final)
```ini
logging console
```