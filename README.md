El flujo de trabajo se ejecuta cada vez que haya un push en la rama main.
    
El job Deploy se ejecuta en un entorno Ubuntu (versión más reciente disponible: ubuntu-latest).

Pasos del flujo de trabajo (steps):

Checkout: Se utiliza la acción actions/checkout@v2 para clonar el repositorio en el entorno de ejecución.

Despliegue con SSH:

    Se definen varias variables de entorno a partir de los secretos configurados en el repositorio, como las claves SSH, el nombre de usuario, el nombre del host y la ruta del proyecto.

    Se crea un directorio .ssh en el entorno de ejecución y se configura la clave privada para la autenticación SSH, las claves privadas se configuran en el secrets de el repositorio github

    Se agrega el host remoto a los hosts conocidos utilizando ssh-keyscan.

    

Conexión SSH y despliegue:

   Se establece una conexión SSH con el servidor remoto.

   Si el directorio del proyecto no existe, se clona el repositorio desde GitHub en la ruta especificada.

   El script hace un git pull para actualizar el repositorio con los últimos cambios de la rama main.

Docker:

los ultimos comandos de docker permiten asegurarte de que estás trabajando con un entorno limpio y actualizado, reconstruyendo las imágenes y volviendo a levantar los contenedores de manera eficiente.
