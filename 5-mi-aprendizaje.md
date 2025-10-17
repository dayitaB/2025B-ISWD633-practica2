# MI APRENDIZAJE

De esta práctica puedo rescatar en primer lugar que tengo que revisar primero las actividades dado que en el ejercico 2 necesité de la creación de una red para poder resolverlo, pero el subtema de redes estaba en la parte 3, es decir después. 
Lo que más me sirvió fue aprender y que es lo que más recuerdo, la conexión de los contenedores en función de las redes, teniendo en cuenta que hay diferentes tipos de redes. De este tema, también recuerdo los comandos para crear las variables de entorno, creación de redes, conexión de contenedores a redes específicas, listar las redes disponibles. 

Esta práctica me sirvió de mucho para consultar y aprender los comandos y las conexiones con la base de datos. Junnto con la práctica anterior me es más fácil recordar los comandos y leer los errores que se me pueden presentar. Debo repasar más los comandos para acceder al postgres.

# Docker Secrets

¿Qué son?

Los Docker Secrets gestionan información sensible (contraseñas, certificados) de forma segura en Docker Swarm

¿Qué son los secretos en Docker?

  - Un Docker Secret es un objeto seguro que almacena información sensible.
  - Se mantiene encriptado en Docker Swarm (modo clúster).
  - Solo los servicios que lo necesitan pueden acceder a él.
  - No queda expuesto en la línea de comandos ni en contenedores normales si se usa correctamente.

Ventajas sobre variables de entorno:

  - No aparecen en docker inspect
  - No se guardan en logs del sistema
  - Mayor control de acceso y rotación automática

