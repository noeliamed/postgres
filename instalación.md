# Instalación de PostgreSQL en Debian 12

A continuación se detallan los pasos necesarios para instalar PostgreSQL en Debian 12.

# 1.INSTALACIÓN
## Actualizar los repositorios, el sistema e instalar PostgreSQL:
Asegúrate de que el sistema esté actualizado:
```
sudo apt update
sudo apt upgrade
sudo apt install postgresql
```
## Verifica el estado de PostgreSQL:
Después de instalarlo debes comprobar que esté iniciado.
```
sudo systemctl status postgresql
```
# 2.CREACIÓN USUARIOS Y ACCESO
## Acceder a la consola:
Postgres crea un usuario por defecto llamado postgres, deberás acceder a este usuario para poder realizar la configuración:
```
sudo -i postgres psql
```
Puedes cambiar la contraseña de este usuario:
```
ALTER USER postgres WITH PASSWORD 'nueva_contraseña';
```
## Crea un nuevo usuario:
Para poder crear un nuevo usuario sigue el siguiente comando;
```
CREATE USER nuevo_usuario WITH PASSWORD 'tu_contraseña';
```
Donde pone nuevo_usuario escribe el nombre de usuario que quieras ponerle al igual que en tu_contraseña.

## Crea una base de datos:
A continuación, crea una base de datos asociada al usuario recién creado:
```
CREATE DATABASE nombrebd OWNER nombre_usuario;
```
En nombrebd escribe el nombre que quieras darle a la base de datos.

## Crea un usuario administrador:
Este usuario tendrá todos los privilegios en una base de datos:
```
GRANT ALL PRIVILEGES ON DATABASE nombrebd TO nombre_usuario;
```
Sal de la consola:
```
\q
```
## Conéctate con el nuevo usuario: 
Para probar la conexión, desde la terminal intenta conectarte con el usuario recién creado:
```
psql -U nombre_usuario -d nombrebd
```
# 3.CREACIÓN DE UNA TABLA
## Creación de una tabla: 
Cuando estés dentro de Postgres con el usuario creado, podrás crear una tabla de la siguiente manera: 
```
CREATE TABLE clientes (
    nif VARCHAR(9) PRIMARY KEY,
    nombre VARCHAR(20) NOT NULL,
);
```
## Inserta datos:
Inserta datos en la tabla recién creada:
```
INSERT INTO clients (nif, nombre)
VALUES ('12345678A', 'Pepe');
```
## Consulta:
Consulta que se haya creadola tabla: 
```
SELECT *
FROM clientes;
```
Tras haber hecho estos pasos habrás instalado con éxito PostgreSQL en Debian 12 además de crear un usuario, una base de datos, una tabla y haber consultado que se ha creado. 

