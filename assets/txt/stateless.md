## DHCP Stateless
<details> 
    <summary>
        ### Switch S1
    </summary>

Configuración inicial de preferencia IPv6
```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname S1
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S1 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 15
 name Estudiantes
 exit
vlan 45
 name Docentes
 exit
vlan 55
 name Admin
 exit
vlan 65
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 55
 no ip address
 ipv6 address 2001:db8:cafe:55::1/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo on para agregación de enlaces
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

EtherChannel 2 modo desirable para agregación de enlaces
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

Configuración de acceso SSH con autenticación local
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
        ### Switch S2
    </summary>

Configuración inicial de preferencia IPv6
```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname S2
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S2 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 15
 name Estudiantes
 exit
vlan 45
 name Docentes
 exit
vlan 55
 name Admin
 exit
vlan 65
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 55
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:cafe:55::2/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo passive para LACP
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

EtherChannel 2 modo on para agregación de enlaces
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

Interfaz gigabit troncal hacia router
```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

Configuración de acceso SSH con autenticación local
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
        ### Switch S3
    </summary>

Configuración inicial de preferencia IPv6
```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
```

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname S3
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S3 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 15
 name Estudiantes
 exit
vlan 45
 name Docentes
 exit
vlan 55
 name Admin
 exit
vlan 65
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 55
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:cafe:55::3/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo on para agregación de enlaces
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

EtherChannel 2 modo desirable para agregación de enlaces
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

Interfaz gigabit troncal hacia router
```ini
interface g0/1
 switchport mode trunk
 switchport trunk allowed vlan 15,45,55,65
 switchport trunk native vlan 65
 no shutdown
 exit
```

Configuración de acceso SSH con autenticación local
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
        ### Router R1
    </summary>

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname R1
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R1 #
service password-encryption
```

Habilitación de interfaz física
```ini
interface g 0/1
 no shutdown
 exit
```

Activación de routing IPv6 y pools DHCP stateless
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

Subinterfaz VLAN 15 con HSRP activo y configuración stateless
```ini
interface g 0/1.15
 encapsulation dot1Q 15
 no ip address
 ipv6 address 2001:db8:cafe:15::/64 eui-64
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

Subinterfaz VLAN 45 con HSRP activo y configuración stateless
```ini
interface g 0/1.45
 encapsulation dot1Q 45
 no ip address
 ipv6 address 2001:db8:cafe:45::/64 eui-64
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

Subinterfaz VLAN 55 con HSRP activo y configuración stateless
```ini
interface g 0/1.55
 encapsulation dot1Q 55
 no ip address
 ipv6 address 2001:db8:cafe:55::/64 eui-64
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

Subinterfaz VLAN nativa 65 con HSRP activo y configuración stateless
```ini
interface g 0/1.65
 encapsulation dot1Q 65 native
 no ip address
 ipv6 address 2001:db8:cafe:65::/64 eui-64
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

Configuración de acceso SSH con autenticación local
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
        ### Router R2
    </summary>

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname R2
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R2 #
service password-encryption
```

Habilitación de interfaz física
```ini
interface g 0/1
 no shutdown
 exit
```

Activación de routing IPv6 y pools DHCP stateless
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

Subinterfaz VLAN 15 con HSRP standby y configuración stateless
```ini
interface g 0/1.15
 encapsulation dot1Q 15
 no ip address
 ipv6 address 2001:db8:cafe:15::/64 eui-64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-15
 no shutdown
 standby version 2
 standby 15 ipv6 autoconfig
 standby 15 priority 100
 exit
```

Subinterfaz VLAN 45 con HSRP standby y configuración stateless
```ini
interface g 0/1.45
 encapsulation dot1Q 45
 no ip address
 ipv6 address 2001:db8:cafe:45::/64 eui-64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-45
 no shutdown
 standby version 2
 standby 45 ipv6 autoconfig
 standby 45 priority 100
 exit
```

Subinterfaz VLAN 55 con HSRP standby y configuración stateless
```ini
interface g 0/1.55
 encapsulation dot1Q 55
 no ip address
 ipv6 address 2001:db8:cafe:55::/64 eui-64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-55
 no shutdown
 standby version 2
 standby 55 ipv6 autoconfig
 standby 55 priority 100
 exit
```

Subinterfaz VLAN nativa 65 con HSRP standby y configuración stateless
```ini
interface g 0/1.65
 encapsulation dot1Q 65 native
 no ip address
 ipv6 address 2001:db8:cafe:65::/64 eui-64
 ipv6 enable
 ipv6 nd other-config-flag
 ipv6 dhcp server DHCP-STATELESS-65
 no shutdown
 standby version 2
 standby 65 priority 100
 standby 65 ipv6 autoconfig
 exit
```

Configuración de acceso SSH con autenticación local
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
        ### Router RA
    </summary>

```diff
- Pendiente
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