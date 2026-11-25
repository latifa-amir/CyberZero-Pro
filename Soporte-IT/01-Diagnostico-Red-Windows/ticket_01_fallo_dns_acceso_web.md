# Ticket #001: Incidencia de Acceso Web por Configuracion Erronea de DNS
## 1. Reporte del Usuario
- Sintoma: El equipo dispone de conectividad en red local y servicios internos, pero las consultas a dominios web sufren tiempos de espera agotados o fallos de carga.
- Equipo / Entorno: thundercats (Windows 7 Enterprise - Laboratorio VMware)
- Direccion IPv4 del cliente: 192.168.236.131 (DHCP)
- Prioridad: Media-Alta
## 2. Diagnostico por Capas
### Paso A: Verificacion de Red Local (IP y Puerta de Enlace)
Se revisa la configuracion del adaptador con ipconfig /all.
- Resultado: IP privada valida (192.168.236.131) y puerta de enlace correcta (192.168.236.2). Se descarta fallo fisico o error de asignacion DHCP (APIPA).
### Paso B: Prueba de Conectividad Externa
Se comprueba salida a internet con ping 8.8.8.8.
- Resultado: 4 paquetes enviados, 4 recibidos (0% perdidos). Conectividad externa confirmada.
### Paso C: Prueba de Resolucion de Nombres (DNS)
Se limpia la cache con ipconfig /flushdns y se prueba nslookup google.com.
- Resultado: DNS request timed out intentando consultar al servidor 10.99.99.99. Causa raiz: configuracion manual incorrecta del servidor DNS en TCP/IPv4.
## 3. Resolucion Aplicada
1. Se abre Conexiones de red con ncpa.cpl.
2. En Propiedades de Conexion de area local -> Protocolo de Internet version 4 (TCP/IPv4), se vuelve a marcar Obtener la direccion del servidor DNS automaticamente.
3. Se limpia la cache con ipconfig /flushdns y se verifica con nslookup google.com.
4. Verificacion final: nslookup utiliza el servidor DNS 192.168.236.2 y resuelve la IP 216.58.205.78. Incidencia cerrada.
