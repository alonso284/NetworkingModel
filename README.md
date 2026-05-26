# NetworkingModel

`NetworkingModel` es un paquete de documentacion para una topologia de Cisco Packet Tracer. El modelo representa una integracion de red entre ARC y Shell, con Fort St. John, BC como punto principal de referencia. El repositorio contiene el archivo de topologia de Packet Tracer y tablas CSV que describen los dispositivos, direccionamiento, conexiones, protocolos y organizacion visual del modelo.

## Archivo de Topologia

`NetworkingModel.pkt` es el archivo principal de Cisco Packet Tracer. Representa la topologia fisica y logica documentada por las tablas CSV de este repositorio.

## Tablas de Documentacion

Las tablas CSV separan la informacion de la topologia por tema. Cada tabla cumple una funcion especifica dentro de la documentacion del proyecto.

### Inventario de Equipos

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Inventario_Equipos).csv`

Define los dispositivos incluidos en la topologia. Cada fila representa un equipo e incluye hostname, organizacion, rol, ubicacion, plataforma, modelo, referencia de direccionamiento de administracion y notas.

Esta tabla cubre routers, switches, firewalls, servidores, controladoras wireless, access points y dispositivos finales.

### Conexiones Fisicas

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Conexiones_Fisicas).csv`

Define la conectividad entre dispositivos. Cada fila identifica ambos extremos del enlace, sus interfaces, la direccion IP o modo de puerto usado en cada lado, el tipo de enlace y una descripcion corta.

Esta tabla incluye cableado fisico, enlaces punto a punto ruteados, enlaces trunk, enlaces access, enlaces WAN hacia ISP y referencias a tuneles VPN logicos.

### Esquema IP

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Esquema_IP).csv`

Define los bloques principales de direccionamiento usados por la topologia. Documenta redes de administracion, rangos de transito interno, rangos WAN publicos simulados, rangos de backbone ISP y subredes VLAN.

### Interfaces Logicas

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Interfaces_Logicas).csv`

Define las interfaces logicas de routers. El modelo actual usa `Loopback99` como identidad de administracion para dispositivos ruteados.

Las direcciones de administracion en loopback se documentan como direcciones host `/32`. El bloque `/24` relacionado se conserva como referencia a la red de administracion indicada en el esquema IP.

### VLANs y HRSP

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(VLANs_y_HRSP).csv`

Define la estructura de Capa 2 y gateway por defecto para los dominios de switching en Fort St. John. Incluye ID de VLAN, nombre de VLAN, subred, IP virtual HRSP, IPs reales de los switches core, comportamiento DHCP de clientes y proposito del servicio.

La documentacion del proyecto usa la etiqueta `HRSP` para el diseno de gateway redundante. En configuracion Cisco IOS, la implementacion correspondiente se expresa con comandos `standby`.

### Spanning Tree

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Spanning_Tree).csv`

Define el diseno de roles de Spanning Tree para los dominios de switching. Identifica la variante de Spanning Tree, el switch root primary, el switch root secondary y las VLANs cubiertas por sitio.

### Indice de Protocolos

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Protocolos).csv`

Resume los protocolos requeridos por el modelo y relaciona cada protocolo con las tablas que lo documentan. Los protocolos cubiertos son:

- Spanning Tree
- DHCP
- HRSP
- OSPF
- BGP
- VPNv4
- WLC
- ACL

### ACLs Inter-VLAN

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(ACLs_Inter_VLAN).csv`

Define las listas de acceso aplicadas en los core switches para segmentacion entre departamentos. Cada fila representa una entrada de ACL e incluye sitio, nombre de ACL, interfaz SVI donde se aplica, direccion, accion, protocolo, origen, destino, puerto destino y observacion.

La politica segmenta OT de Enterprise, protege la VLAN de administracion y permite acceso controlado a servicios DNS/DHCP desde todas las VLANs que lo requieran.

### Zonas de Color

`Plan_Integracion_ARC_Shell_Inventario_y_Conexiones-PT(Zonas_Color).csv`

Define zonas visuales para el lienzo de Packet Tracer. Cada fila describe el nombre de la zona, color, valor hexadecimal, dispositivos incluidos, ubicacion sugerida y proposito.

Las zonas de color sirven como apoyo visual para distinguir areas como core ARC, servicios ARC, core Shell, servicios Shell, ISP-A, ISP-B, sitios remotos, OT y areas wireless/servicios.

## Areas de Red

La topologia esta organizada en las siguientes areas principales:

- Hub ARC Fort St. John
- Sitios remotos ARC
- Oficina Shell Fort St. John
- Sitio DR Shell Dawson Creek
- Red simulada del proveedor ISP-A
- Red simulada del proveedor ISP-B
- Conectividad VPN logica entre firewalls ARC y Shell

## Alcance de Protocolos

El alcance de protocolos documentado se limita a los protocolos requeridos para este modelo de Packet Tracer:

- Spanning Tree para prevencion de loops de Capa 2 y control de root bridge.
- DHCP para asignacion dinamica de direccionamiento a endpoints.
- HRSP para gateway redundante por VLAN.
- OSPF para ruteo interno por dominio y, si se implementa MPLS/VPNv4, para reachability de loopbacks PE dentro del backbone ISP.
- BGP para ruteo WAN entre routers edge empresariales y routers ISP simulados.
- VPNv4 como address-family MP-BGP entre routers PE del ISP cuando se simula una L3VPN. No reemplaza la VPN IPSec entre firewalls y no requiere xconnect para este diseno.
- WLC para control centralizado de WLAN y mapeo SSID/VLAN.

## Direccionamiento de Administracion

El direccionamiento de administracion se documenta en dos lugares:

- `Inventario_Equipos.csv` lista la referencia de IP de administracion para cada dispositivo.
- `Interfaces_Logicas.csv` identifica las direcciones de administracion de routers implementadas como `Loopback99`.

Para dispositivos ruteados, `Loopback99` representa la identidad estable de administracion. Para comportamiento de gateway en VLAN de administracion, la informacion se documenta en `VLANs_y_HRSP.csv`.

## Control de Archivos

El archivo de topologia de Packet Tracer y las tablas CSV forman parte de la documentacion versionada del proyecto. Archivos locales del sistema operativo, estado de editores, archivos temporales de Packet Tracer, autosaves, respaldos y capturas de paquetes son excluidos por `.gitignore`.
