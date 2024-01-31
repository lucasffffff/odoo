# odoo

## Requerimientos para utilizar Odoo:
- `Una base de datos`(En este caso usaremos *Postgres*)
- `Python` (odoo esta escrito en python y lo necesitaremos para poder hacer algunas funcionalidades)

## Docker compose
### Odoo
```yml
version: '3.1'

services:
  # odoo:
  web:
    image: odoo:16.0
    depends_on:
      - mydb
    ports:
      - "8069:8069"
    environment:
      - HOST=mydb # same name as the postgres service
      - USER=odoo
      - PASSWORD=odoo

  # postgres:
  mydb:
    image: postgres
    ports:
      - "5432:5432"
    environment:
      POSTGRES_DB: postgres
      POSTGRES_PASSWORD: odoo
      POSTGRES_USER: odoo

```
### Postgres
Para poder utilizar odoo requerimos una base de datos, por lo que en este caso usaremos postgres y crearemos otro contenedor para ello.<br>

⚠️ Evita tener el puerto de postgres ocupado ⚠️

#### Comprobar que la base funciona desde un IDE:
Estés en el IDE que estés (PyCharm en este caso), entre los botones de la barra de la derecha buscaremos el botón `Database` donde nos mostrará una ventana con las bases de datos que tenemos.
No tendremos ninguna por lo que persionaremos añadir (➕) , y `Add a Database`, nos aparecera una ventana para elegir el servicio, usaremos postgres, nos aparecera otra ventana donde tan solo hay que poner el nombre de la base de datos, el usuario y la contraseña.
Te pedirá instalar un driver para poder comprobar el funcionamiento de la base, tras descargarlo presiona el botón `Test Connection`, si la conexion es correcta presiona `Apply` y despues `OK`. Ahora en el apartado ` DATABASE` podrás ver la base creada.
<details><summary><b><i>IMAGENES</i></b></summary>
<p>

</p>
</details>

