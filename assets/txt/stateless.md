## DHCP Stateless
<details> 
    <summary>
        Switch S1
    </summary>
Configuración inicial de preferencia IPv6 S4
```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
System configuration has been modified. Save? [yes/no]:yes
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
```

Configuración básica de consola y seguridad S4
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

Creación de VLANs para diferentes grupos S4
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

Configuración de interfaz de administración IPv6 S4
```ini
interface vlan 30
 no ip address
 ipv6 address 2001:db8:3c4d:30::4/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa S4
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

Puertos de acceso para estudiantes con seguridad de puerto S4
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

Puertos de acceso para docentes con seguridad de puerto S4
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

Puerto de administración con seguridad S4
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

EtherChannel 1 modo on para agregación de enlaces S4
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

EtherChannel 2 modo desirable para agregación de enlaces S4
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

Interfaz gigabit troncal hacia router S4
```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
 no shutdown
 exit
```

Configuración de acceso SSH con autenticación local S4
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
Configuración inicial de preferencia IPv6 S5
```ini
sdm prefer dual-ipv4-and-ipv6 default
reload
System configuration has been modified. Save? [yes/no]:yes
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
```

Configuración básica de consola y seguridad S5
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

Creación de VLANs para diferentes grupos S5
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

Configuración de interfaz de administración IPv6 S5
```ini
interface vlan 30
 no ip address
 ipv6 enable
 ipv6 address 2001:db8:3c4d:30::5/64
 no shutdown
 exit
```

Configuración inicial de puertos a VLAN nativa S5
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

Puertos de acceso para estudiantes con seguridad de puerto S5
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

Puertos de acceso para docentes con seguridad de puerto S5
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

Puerto de administración con seguridad S5
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

EtherChannel 1 modo passive para LACP S5
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

EtherChannel 2 modo on para agregación de enlaces S5
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

Interfaz gigabit troncal hacia router S5
```ini
interface g 0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30,40
 switchport trunk native vlan 40
 no shutdown
 exit
```

Configuración de acceso SSH con autenticación local S5
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

</details>

<details> 
    <summary>
        Router R1
    </summary>

</details>

<details> 
    <summary>
        Router R2
    </summary>

</details>

<details> 
    <summary>
        Configuraciones Router RA
    </summary>

```diff
- Pendiente
```

</details>