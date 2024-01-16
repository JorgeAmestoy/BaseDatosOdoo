# ODOO
**Odoo** es un conjuntos de programas para ayudar a las empresas
a gestionar diferentes aspectos de su negocio. Entre sus características
destacan:
- Uso fácil
- Variación de módulos
- Buena adaptación a las necesidades 
- Versión comunitaria gratuita

El primer paso es buscar en docker hub(**PONER FORMATO ENLACE**) la imagen de odoo que queremos utilizar. Así, creamos
un fichero docker-compose.yml en el proyecto con el siguiente contenido:
```
version: '3.1'
services:
  web:    
    image: odoo:16.0
    
    depends_on:
      - db
    ports:
      - "8069:8069"
  db:
    image: postgres:15
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_PASSWORD=odoo
      - POSTGRES_USER=odoo
    ports:
      - "5432:5432"
```
`version: '3.1`: indica la versión de docker-compose que vamos a utilizar. En este caso, la 3.1.
`services`: indica los servicios que vamos a utilizar. En este caso, dos: 
- web 
- db

En **web** indicamos que la imagen a utilizar es la de odoo:16.0.
Además, indicamos que depende del servicio *db* y que el puerto 8069 de la máquina host se mapea al puerto 8069 del contenedor.<br>
En **db** indicamos que la imagen a utilizar es la de postgres:15. También
indicamos que el puerto 5432 de la máquina host se mapea al puerto 5432 del contenedor.
En environment indicamos las variables de entorno que se van a utilizar en el contenedor. En este caso, la base de datos se llama postgres, 
el usuario es odoo 
y la contraseña también es odoo.
