# Caso Práctico 02: Escaneo Avanzado y Auditoría de Vulnerabilidades SMB con Nmap (NSE)
## 1. Descripción del Entorno de Laboratorio
* **Atacante / Auditor (Kali Linux):** `192.168.236.128`
* **Servidor Objetivo (Windows 7 - CPHE):** `192.168.236.131` (Hostname: `THUNDERCATS`)
* **Servicio Auditado:** SMB (Server Message Block) / NetBIOS (Puertos `139/TCP` y `445/TCP`)
## 2. Metodología de Escaneo Avanzado (Nmap Scripting Engine - NSE)
Para auditar el estado real de los servicios expuestos, se ejecutó un escaneo especializado combinando la detección de versiones y la ejecución de scripts NSE enfocados en la búsqueda de fallos de seguridad en SMB.

```bash
sudo nmap -sV --script=smb-vuln* -p 139,445 192.168.236.131
```
## 3. Resultados y Hallazgos Técnicos

| Puerto | Estado | Servicio | Vulnerabilidad Detectada | CVE / Referencia |
| :--- | :--- | :--- | :--- | :--- |
| 139/TCP | Open | netbios-ssn | Service Activo | N/A |
| 445/TCP | Open | microsoft-ds | Remote Code Execution en SMBv1 | **MS17-010 (CVE-2017-0143)** |

> **Evidencia del Script NSE:** El análisis confirmó que el servidor es **VULNERABLE** a la ejecución remota de código (RCE) en servidores SMBv1 (EternalBlue), con un factor de riesgo alto.
## 4. Conclusiones y Medidas de Remediación
1. **Mitigación Crítica:** Deshabilitar el protocolo obsoleto **SMBv1** en el sistema operativo objetivo para evitar la explotación de la vulnerabilidad MS17-010.
2. **Hardening de Red:** Aplicar los parches de seguridad oficiales de Microsoft (KB4012212) y restringir el tráfico de los puertos `139` y `445` mediante reglas estrictas de Firewall.
