# Caso 01 - Gestión de servicios con systemctl
## Objetivo
Aprender a consultar el estado de un servicio y a gestionarlo (parar y arrancar), usando systemctl.
## Acciones realizadas
- Consulta del estado de un servicio con systemctl status
- Identificación de si un servicio está activo, si arranca solo al encender el sistema, y revisión de su actividad reciente
- Parada de un servicio de prueba (cups) con systemctl stop
- Verificación del cambio de estado a inactive
- Arranque del servicio de nuevo con systemctl start
- Verificación de que volvió a estar activo, con un PID distinto al anterior
## Comandos utilizados
systemctl status NetworkManager
systemctl status cups
sudo systemctl stop cups
sudo systemctl start cups
## Resultado
Pude comprobar que al parar un servicio, su estado cambia a "inactive (dead)", y al arrancarlo de nuevo, vuelve a "active (running)" pero con un PID distinto al que tenía antes de pararlo.
## Lo que he aprendido
- Cómo leer el estado de un servicio: Active (activo/inactivo), Loaded (si arranca solo al encender), y las últimas líneas de actividad para detectar errores
- El PID de un proceso cambia cada vez que se arranca, aunque sea el mismo servicio
- La diferencia entre estar "loaded/enabled" (configurado para arrancar) y estar "active" (corriendo ahora mismo)
- Por qué es importante parar servicios de prueba en vez de servicios críticos como la conexión de red.
