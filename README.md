# Proyecto Integrador del 5° Semestre Grupo B - Ingeniería en TIC's, ITSOEH

## **Datos del Equipo**  
**Institución**: Instituto Tecnológico Superior del Occidente del Estado de Hidalgo.  
**Programa Educativo**: Ingeniería en Tecnologías de la Información y Comunicaciones.  
**Semestre y Grupo**: 5° "B".  
**Asignatura**: Redes de Computadoras.  

**Integrantes**:  
- [230110322]  Cruz Martínez Alejandro
- [230110032]  Chávez Atanacio Yael Antonio
- [230110528]  Gonzaga López Luis Fernando 
- [230110578]  Martínez Hernández Brayan 
- [230110358]  Soto Hernandez Edwin Salvador 

<details> 
    <summary>
        Topología Física 
    </summary>
<img src="assets/img/image01.png" height="500px" />
</details>

<details> 
    <summary>
        Topología Lógica 
    </summary>
<img src="assets/img/image02.png" height="500px" />
</details>

<details> 
    <summary>
        Extras
    </summary>
Borrar la configuración guardada en NVRAM.

```ini
Switch# erase startup-config
```

Test VLAN 30 Administrativa 

```ini
interface f 0/15
 switchport mode access
 switchport access vlan 30
 no shut
 exit
```

Test VLAN 55 Administrativa 

```ini
interface f 0/15
 switchport mode access
 switchport access vlan 55
 no shut
 exit
```

</details>

- [Stateless](docs/stateful.md)
- [ful](docs/stateless.md)
- [show](docs/show.md)