## Comando show
<details> 
    <summary> 
        🔀Switches
    </summary>
    <table>
        <tr>
            <td>
                Mostrar puertos EtherChannel:
                <pre><code>do sh et su</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_s01.png" alt="Imagen puertos EtherChannel" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar STP (Spanning Tree Protocol):
                <pre><code>do sh sp</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_s02.png" alt="Imagen STP" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar seguridad de los puertos:
                <pre><code>do sh po se</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_s03.png" alt="Imagen seguridad puertos" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar VLANs configuradas:
                <pre><code>do sh vlan br</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_s04.png" alt="Imagen VLANs configuradas" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar interfaces configuradas (puertos físicos, port-channel y vlans administrativas):
                <pre><code>do sh ipv6 int br</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_s05.png" alt="Imagen interfaces configuradas" width="600">
            </td>
        </tr>
    </table>
</details> 

<details> 
    <summary> 
        🌐Routers
    </summary>
    <table>
        <tr>
            <td>
                Mostrar HSRPv2 (Información del Router virtual, y si este es active o standby):
                <pre><code>do sh standby br</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_r01.png" alt="Imagen HSRPv2" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar los pools DHCPv6 (prefijo, numero de hosts y dominio):
                <pre><code>do sh ipv6 dh po</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_r02.png" alt="Imagen DHCPv6 pools" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar interfaces configuradas:
                <pre><code>do sh ip int br</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_r03.png" alt="Imagen interfaces configuradas" width="600">
            </td>
        </tr>
        <tr>
            <td>
                Mostrar estado del DHCPv6:
                <pre><code>do sh ipv6 dhcp bind</code></pre>
            </td>
            <td>
                <img src="assets/img/sh_r04.png" alt="Imagen DHCPv6 estado" width="600">
            </td>
        </tr>
    </table>
</details> 

<details> 
    <summary>
        💻Computadoras
    </summary>
    <table>
        <tr>
            <td>
                Mostrar información de la red:
                <pre><code>ipconfig</code></pre>
            </td>
        </tr>
        <tr>
            <td>
                Liberar dirección IP actual del Adaptador de Red:
                <pre><code>ipconfig /release</code></pre>
            </td>
        </tr>
        <tr>
            <td>
                Renovar dirección IP (Forzar DHCPv6):
                <pre><code>ipconfig /renew</code></pre>
            </td>
        </tr>
    </table>
</details>