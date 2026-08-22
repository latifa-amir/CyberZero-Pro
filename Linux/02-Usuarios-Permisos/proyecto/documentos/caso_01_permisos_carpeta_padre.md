# Caso 01 - Permission denied por permisos de carpeta padre
## Objetivo
Comprobar si un usuario distinto al propietario puede acceder a un archivo con permiso de lectura abierta (644)
## Acciones realizadas
- Creación de un usuario de prueba con 'adduser practicas'
- Cambio de sesión al usuario 'practicas' con 'sudo su practicas'
- Intento de lectura de un archivo con permisos 644 (rw-r--r--)
## Comandos utilizados
sudo adduser practicas
sudo su practicas
cat /home/ubuntu/CyberZero-Pro/Linux/02-Usuarios-Permisos/README.md
## Resultado
Permission denied, a pesar de que el archivo tenía permisos de lectura para "otros" (644).
## Diagnóstico
El archivo en sí tenía permisos correctos, pero la carpeta padre /home/ubuntu tenía permisos rwxr-x--- (750), sin acceso para "otros".
Sin permiso de ejecución (x) en una carpeta intermedia de la ruta,no se puede llegar al archivo final, aunque este tenga permisos abiertos.
## Lo que he aprendido
- Los permisos de las carpetas "padre" de una ruta pueden bloquear el acceso a un archivo, incluso si el archivo en sí tenía permisos abiertos.
- La diferencia entre "usuario" (dueño concreto del archivo) y "otros" (cualquier otra cuenta del sistema, aunque sea válida).
- Cómo diagnosticar un problema de acceso revisando toda la ruta, no solo el archivo final.
