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
