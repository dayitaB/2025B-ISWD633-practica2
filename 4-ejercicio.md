## Esquema para el ejercicio
![Imagen](esquema-4-ejercicio.PNG)

### Crear la red
```
docker network create net-wp -d bridge
```

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias
```
docker run -d --name contenedor_mysql --network net-wp -e MYSQL_ROOT_PASSWORD=rootpassword -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=wppassword mysql:8
```

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
```
docker run -d --name contenedor_wordpress --network net-wp -p 9300:80 -e WORDPRESS_DB_HOST=contenedor_mysql -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppassword wordpress
```

De acuerdo con el trabajo realizado, en el esquema del ejercicio el puerto a es **9300**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
<img width="1239" height="944" alt="imagen" src="https://github.com/user-attachments/assets/079da700-1d62-492e-b4ed-66f78db6e83c" />

<img width="1329" height="948" alt="imagen" src="https://github.com/user-attachments/assets/6ef422e3-a9a8-4299-a34b-2dda37f35017" />

Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
<img width="1567" height="766" alt="imagen" src="https://github.com/user-attachments/assets/3177b774-e449-4b13-9ad5-9b43137c829f" />

<img width="1058" height="989" alt="imagen" src="https://github.com/user-attachments/assets/725974e4-0713-4b4f-8360-b234ca9517bf" />

### Eliminar el contenedor wordpress
```
docker stop contenedor_wordpress
docker rm contenedor_wordpress
```

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress
```
docker run -d --name contenedor_wordpress --network net-wp -p 9300:80 -e WORDPRESS_DB_HOST=contenedor_mysql -e WORDPRESS_DB_NAME=wordpress -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=wppassword wordpress
```

### ¿Qué ha sucedido, qué puede observar?
Se puede observar lo que he hecho debido a que se ingreso con las mismos atributos, esto se da porque los datos se almacenaron en mysql y dado que este contenedor no fue eliminado, wordpress al volver a ser creado pudo reconectarse a la bd y recuperar la información que había. 
<img width="847" height="433" alt="imagen" src="https://github.com/user-attachments/assets/f6ce05f4-0302-4c75-a2cb-982a73fb615e" />


