# Caso Práctico 01: Diagnóstico de Red TCP/IP y Escaneo de Servicios con Nmap
## 1. Descripción del Entorno de Laboratorio
* **Atacante / Auditor (Kali Linux):** `192.168.236.128`
* **Servidor Objetivo (Windows 7 - CPHE):** `192.168.236.131` (Hostname: `THUNDERCATS`)
* **Cliente Linux (Ubuntu):** `192.168.236.144`
* **Subred Local (VMware NAT):** `192.168.236.0/24`
## 2. Diagnóstico de Conectividad (Ubuntu)
Se ejecutó la secuencia de comprobación de la pila TCP/IP en Ubuntu:
1. `ip a` -> Identificación de interfaz `ens33` con IP `192.168.236.144`.
2. `ping -c 4 127.0.0.1` -> Loopback verificado (0% pérdida).
3. `ping -c 4 192.168.236.144` -> Interfaz propia funcional.
4. `ip route` -> Identificación de Gateway por defecto (`192.168.236.2`).
5. `ping -c 4 8.8.8.8` -> Enlace con red externa / Internet verificado.
6. `ping -c 4 google.com` -> Resolución de nombres DNS funcional.
## 3. Escaneo de Servicios y SO con Nmap (Kali Linux)
Desde Kali Linux se identificaron los hosts activos en la subred y se auditó la máquina objetivo `192.168.236.131`:
```bash
sudo nmap -sV -O 192.168.236.131```

| Puerto | Estado | Servicio | Descripción |
| :--- | :--- | :--- | :--- |
| 135/TCP | Open | msrpc | Microsoft Windows RPC |
| 139/TCP | Open | netbios-ssn | NetBIOS Session Service |
| 445/TCP | Open | microsoft-ds | SMB (Vulnerable a MS17-010) |
## 4. Conclusiones y Remediación
1. Verificación de Red: Toda la subred local comunica correctamente bajo el adaptador VMware NAT.
2. Medida de Seguridad: Deshabilitar SMBv1 o bloquear el puerto 445/TCP en el Firewall de Windows para mitigar vulnerabilidades de ejecución remota de código en sistemas legacy.
