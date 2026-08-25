# Usuarios y Permisos
## Objetivo
Aprender a gestionar usuarios, grupos y permisos en Linux, entendiendo quién puede leer, escribir o ejecutar cada archivo o carpeta.
## Estado
- Módulo completado
## Conceptos aprendidos
- Estructura de permisos: usuarios, grupo, otros (rwx)
- Comando chmod para modificar permisos, en formato letras y formato numérico (755, 644...)
- Creación de usuarios con adduser
- Creación de grupos con groupadd
- Añadir usuarios a grupos con usermod -aG
- Cambio de grupo propietario de una carpeta con chgrp
- Diagnóstico de problemas de acceso por permisos de carpeta padre
## Lo que he comprendido
En este módulo he aprendido que todo archivo y carpeta en Linux tiene un propietario y un grupo, y que los permisos determinan qué puede hacer cada uno de ellos (leer, escribir, ejecutar). También he practicado cómo compartir acceso a una carpeta entre varios usuarios de forma segura, usando un grupo dedicado en vez de abrir permisos a todo el mundo, y he diagnosticado un problema real de acceso causado por permisos de una carpeta padre.
## Próximo objetivo
Continuar con el Módulo 03 del portafolio.
