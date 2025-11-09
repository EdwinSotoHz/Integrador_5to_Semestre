<details> 
    <summary>
        Switch S1
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
        Switch S2
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
        Switch S3
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
        Router R1
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
        Router R2
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
        Configuraciones Router RA
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
```<details> 
    <summary>
        Switch S4
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

hostname S4
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S4 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 10
 name Estudiantes
 exit
vlan 20
 name Docentes
 exit
vlan 30
 name Admin
 exit
vlan 40
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::4/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo on para agregación de enlaces
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

EtherChannel 2 modo desirable para agregación de enlaces
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

Interfaz gigabit troncal hacia router
```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
        Switch S5
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

hostname S5
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S5 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 10
 name Estudiantes
 exit
vlan 20
 name Docentes
 exit
vlan 30
 name Admin
 exit
vlan 40
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 30
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:3c4d:30::5/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo passive para LACP
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

EtherChannel 2 modo on para agregación de enlaces
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

Interfaz gigabit troncal hacia router
```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
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
        Switch S6
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

hostname S6
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado S6 #
service password-encryption
```

Creación de VLANs para diferentes grupos
```ini
vlan 10
 name Estudiantes
 exit
vlan 20
 name Docentes
 exit
vlan 30
 name Admin
 exit
vlan 40
 name Native
 exit
```

Configuración de interfaz de administración IPv6
```ini
interface vlan 30
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:3c4d:30::6/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa
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

Puertos de acceso para estudiantes con seguridad de puerto
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

Puertos de acceso para docentes con seguridad de puerto
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

Puerto de administración con seguridad
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

EtherChannel 1 modo on para agregación de enlaces
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

EtherChannel 2 modo desirable para agregación de enlaces
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
        Router R3
    </summary>

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname R3
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R3 #
service password-encryption
```

Habilitación de interfaz física
```ini
interface g 0/1
 no shutdown
 exit
```

Activación de routing IPv6 y pools DHCP stateful
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

Subinterfaz VLAN 10 con HSRP y configuración stateful
```ini
interface g 0/1.10
 encapsulation dot1Q 10
 no ip address
 ipv6 address 2001:db8:3c4d:10::/64 eui-64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 10 ipv6 autoconfig
 standby 10 priority 100
 exit
```

Subinterfaz VLAN 20 con HSRP y configuración stateful
```ini
interface g 0/1.20
 encapsulation dot1Q 20
 no ip address
 ipv6 address 2001:db8:3c4d:20::/64 eui-64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 20 ipv6 autoconfig
 standby 20 priority 100
 exit
```

Subinterfaz VLAN 30 con HSRP y configuración stateful
```ini
interface g 0/1.30
 encapsulation dot1Q 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::/64 eui-64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 30 ipv6 autoconfig
 standby 30 priority 100
 exit
```

Subinterfaz VLAN nativa 40 con HSRP y configuración stateful
```ini
interface g 0/1.40
 encapsulation dot1Q 40 native
 no ip address
 ipv6 address 2001:db8:3c4d:40::/64 eui-64
 ipv6 enable
 ipv6 nd managed-config-flag
 ipv6 nd prefix default no-advertise
 no shutdown
 standby version 2
 standby 40 priority 100
 standby 40 ipv6 autoconfig
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
        Router R4
    </summary>

Configuración básica de consola y seguridad
```ini
enable
configure terminal

line console 0
 logging synchronous
 exit

hostname R4
enable password cisco
enable secret tics
banner motd # Solo acceso autorizado R4 #
service password-encryption
```

Habilitación de interfaz física
```ini
interface g 0/1
 no shutdown
 exit
```

Activación de routing IPv6 y pools DHCP stateful
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

Subinterfaz VLAN 10 con HSRP activo y servidor DHCP
```ini
interface g 0/1.10
 encapsulation dot1Q 10
 no ip address
 ipv6 address 2001:db8:3c4d:10::/64 eui-64
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

Subinterfaz VLAN 20 con HSRP activo y servidor DHCP
```ini
interface g 0/1.20
 encapsulation dot1Q 20
 no ip address
 ipv6 address 2001:db8:3c4d:20::/64 eui-64
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

Subinterfaz VLAN 30 con HSRP activo y servidor DHCP
```ini
interface g 0/1.30
 encapsulation dot1Q 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::/64 eui-64
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

Subinterfaz VLAN nativa 40 con HSRP activo y servidor DHCP
```ini
interface g 0/1.40
 encapsulation dot1Q 40 native
 no ip address
 ipv6 address 2001:db8:3c4d:40::/64 eui-64
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
        Configuraciones Router RA
    </summary>

```diff
- Pendiente
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