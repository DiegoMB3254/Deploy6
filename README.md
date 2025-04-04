Flujo de trabajo de despliegue automático:
Este flujo de trabajo de GitHub Actions se ejecuta cada vez que se hace un push a la rama main. A continuación, se describen los detalles del proceso paso a paso.

Job: Deploy

Sistema operativo: ubuntu-latest (la versión más reciente disponible de Ubuntu).

Pasos del flujo de trabajo

1. Checkout del repositorio
Se utiliza la acción actions/checkout@v2 para clonar el repositorio en el entorno de ejecución.

2. Configuración para despliegue por SSH
Se definen variables de entorno a partir de los secrets del repositorio, tales como:

-Claves SSH

-Nombre de usuario

-Host remoto

-Ruta del proyecto

Despues:

Se crea el directorio .ssh en el entorno de ejecución.

Se configura la clave privada SSH para la autenticación.

Se agregan los datos del host remoto a los hosts conocidos usando ssh-keyscan.

3. Conexión SSH y despliegue remoto
Se establece la conexión SSH con el servidor remoto.

Si el directorio del proyecto no existe, se clona el repositorio desde GitHub en la ruta especificada.

Se ejecuta un git pull para actualizar el repositorio con los últimos cambios de la rama main.