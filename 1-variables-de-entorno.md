# Variables de Entorno
### ¿Qué son las variables de entorno?
Una variable de entorno es un valor dinámico con un nombre que reside en el sistema operativo y que influencia el comportamiento de los programas, este proporcionando información sobre el sistema o la sesión en curso. Normalmente, las variables de entorno almacenan valores predeterminado y permanecen de manera oculta configuradas en el sistema.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

```
docker run -d --name srv-weeb -e username=dayanna -e role=admin nginx:alpine
```
<img width="962" height="59" alt="imagen" src="https://github.com/user-attachments/assets/e23badbc-1903-49e6-a3ad-43586153072a" />

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
<img width="684" height="225" alt="imagen" src="https://github.com/user-attachments/assets/e75592b2-b3d9-429a-94ad-b18021834e58" />


### Crear un contenedor con la imagen de mysql, mapear todos los puertos
```
docker run -d --name mysql_db -p 3306:3306 mysql:latest
```
### ¿El contenedor se está ejecutando?
No, ya que al poner el comando de docker ps no aparece el contenedor recien creado

<img width="1117" height="426" alt="imagen" src="https://github.com/user-attachments/assets/f7158aac-f741-4a99-a28f-35c7d21b8fda" />


### Identificar el problema
El comando no contenia las variables de entorno necesarias para que la imagen de MyDQL se ejecute. Para que un contenedor con la imagen de MySQL se inicie y permanezca en ejecución, se debe proporcionar al menos la variable de entorno MYSQL_ROOT_PASSWORD

<img width="1143" height="193" alt="imagen" src="https://github.com/user-attachments/assets/429475e7-9f36-452a-819b-98ff44a8c335" />

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

### ¿Qué bases de datos existen en el contenedor creado?
Primero cree bien el contenedor añadiendo la variable de entorno 
```
docker run -d --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=dayita123* mysql:latest
```
Y una vez dentro del contenedor, usé el comando: 
```
docker exec -it mysql bash
```
<img width="293" height="203" alt="imagen" src="https://github.com/user-attachments/assets/c190ad93-3928-4ef7-a513-714238f161d3" />
