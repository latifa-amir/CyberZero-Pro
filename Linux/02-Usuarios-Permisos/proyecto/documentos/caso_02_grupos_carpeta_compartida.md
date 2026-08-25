# Caso 02 - Compartir acceso mediante grupos
## Objetivo
Dar acceso a un usuario distinto al propietario sobre una carpeta concreta, sin abrir el acceso a toda la carpeta personal (home).
## Acciones realizadas
- Creación de un grupo nuevo con 'groupadd colaboradores'
- Añadir del usuario practicas a ese grupo con 'usermod -aG'
- Creación de una carpeta compartida fuera de las carpetas home personales, en /home/compartido
- Cambio del grupo propietario de la carpeta con 'chgrp'
- Asignación de permisos 770 (rwxrwx---) para dar acceso total al grupo, sin abrir acceso a "otros"
- Verificación de acceso real cambiando de sesión al usuario practicas
## Comandos utilizados
sudo groupadd colaboradores
sudo usermod -aG colaboradores practicas
sudo mkdir /home/compartido
sudo chgrp colaboradores /home/compartido
sudo chmod 770 /home/compartido
sudo su practicas
cd /home/compartido
## Resultado
El usuario practicas pudo acceder correctamente a /home/compartido y a su contenido, sin necesidad de abrir el acceso a /home/ubuntu.
## Por qué no se puso la carpeta dentro de /home/ubuntu
Las carpetas personales (home) de cada usuario están cerradas para "otros" por defecto, por seguridad. Poner una carpeta compartida dentro de una carpeta personal genera el mismo problema visto en el Caso 01 (Permission denied). La solución correcta es crear la carpeta compartida fuera de las home personales, y controlar el acceso mediante un grupo dedicado.
## Lo que he aprendido
- Cómo crear grupos y añadir usuarios a ellos (groupadd, usermod -aG)
- Cómo cambiar el grupo propietario de una carpeta (chgrp)
- Por qué usar grupos es la forma correcta de compartir acceso entre varios usuarios, en vez de abrir permisos a "otros"
- Dónde ubicar carpetas compartidas para evitar problemas de acceso por permisos de carpetas padre
