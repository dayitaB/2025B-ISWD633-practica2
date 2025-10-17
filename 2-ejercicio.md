### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:15-alpine3.21

```
docker run -d --name srv_postgres -e POSTGRES_USER=admin -e POSTGRES_PASSWORD=12345 -e POSTGRES_DB=BaseUno postgres:15-alpine3.21
```

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
```
docker run -d --name srv_pgadmin4 -e PGADMIN_DEFAULT_EMAIL=admin@admin.com -e PGADMIN_DEFAULT_PASSWORD=12345 -p 8080:80 dpage/pgadmin4
```

La figura presenta el esquema creado en donde los puertos son:
- a: 8080 (puerto externo pgAdmin)
- b: 80 (puerto interno pgAdmin)
- c: 5432 (postgres)

![Imagen](esquema-2-ejercicio.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.

<img width="1256" height="867" alt="imagen" src="https://github.com/user-attachments/assets/6c786372-4be5-4c3e-82db-da61f21456d6" />
<img width="1652" height="742" alt="imagen" src="https://github.com/user-attachments/assets/48cbf105-53b7-4027-bfd2-b373f3786b70" />


### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.
Para crear utilicé: 
```
CREATE TABLE personas (
    id SERIAL PRIMARY KEY, 
    nombre VARCHAR(100) NOT NULL 
);

INSERT INTO personas (nombre) VALUES ('Dayanna Bravo');
INSERT INTO personas (nombre) VALUES ('Miguel Guilca');

```
<img width="1122" height="710" alt="imagen" src="https://github.com/user-attachments/assets/191333f6-bcc3-422e-b311-15589fa8168c" />

## Desde el servidor postgresl
### Acceder al servidor
Se tenia que crear una red primero 

```
docker network create red_ej2
```
### Conectarse a la base de datos info

### Realizar un select *from personas
<img width="603" height="198" alt="imagen" src="https://github.com/user-attachments/assets/0e0b9de0-49e5-469e-8aa5-5bad84d1dbcf" />


