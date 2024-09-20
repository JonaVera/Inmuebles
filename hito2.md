## HITO 2 

- Inicializamos el Entorno
--> source venv/Scripts/activate

# Crear nueva Base de Datos
- Crearemos una nueva base de datos en postgresql
--> create database hito_2;
--> \c hito_2;
--> \dt
- Borramos las cache que se crearon al hacer la marca de migracion y la migracion.
- En el .env debemos cambiar el nombre de la base de datos que creamos sino no migrara.
- Realizamos la marca de migracion y la migracion y migramos
--> python manage.py makemigrations
--> python manage.py migrate

# Poblar Data
- Para Poblar los modelos y sus datos:
- Copiamos los archivos (data y outputs) en nuestro sitio web, dentro de esas carpetas se encuentran datos .json que usaremos para poblar nuestras tablas.
- Debemos seguir un orden para no pisar las llaves Foraneas.

- Para cargar tabla (auth_user):
--> python manage.py loaddata m7_python/data/users.json
<!-- Installed 16 object(s) from 1 fixture(s) -->
- Se lograron migrar 16 objetos (usuarios con sus datos), podemos verlo en postgresql.
--> select * from auth_user; 

- Cargamos tablas regiones_comunas:
--> python manage.py loaddata m7_python/data/regiones_comunas.json
<!-- Installed 362 object(s) from 1 fixture(s) -->
--> select * from m7_python_region;
--> select * from m7_python_comuna;

- Cargamos tabla inmuebles:
--> python manage.py loaddata m7_python/data/inmuebles.json
<!-- Installed 20 object(s) from 1 fixture(s) -->
--> select * from m7_python_inmueble;

# Archivo Temp.py
- Configuramos e importamos para trabajar en el archivo temp.py, configuramos el .env.
- Se guardan los archivos en outputs en datos.txt

####################################################################################

# DAY 11

- Inicializamos el Entorno
--> source venv/Scripts/activate

- Probamos los el archivo temp.py, para ejecutar con orm y postgres.
# Ejecutando consultas con la ORM (Comunas)
- Probando el codigo para listado_inmuebles_comuna_orm y hacemos un print.
--> python m7_python/temp.py
- Ahora lo guardaremos en archivo datos.txt, al ejecutar:
--> python m7_python/temp.py
Este nos guardara el informe el archivo datos.txt

# Consulta SQL (Comunas)
- Escribimos el codigo con la consulta para tener listado_inmuebles_comuna_sql(comuna).
- Guardamos los datos en archivo datos.txt

# Consulta ORM (Region)
- listado_inmuebles_region_orm, se guardaran datos en archivo txt

# Consulta SQL (Region)
- listado_inmuebles_region_sql(region), se guardaran datos en archivo txt

#################################################################################

# Creamos el Admin
- Creamos el admin para más adelante.
--> python manage.py createsuperuser
- User = admin
- email = jv@gmail.com
- password = 1234

# Modularizacion de las urls 
- Modificamos la Url de nuestro sitio web, adañiendo el include y nuestra app.
- Creamos el archivo urls.py en la App, importamos y confifuramos la ruta barra.

# Configuramos la views.py
- De services importamos todos los inmuebles y definimos el index.

######################################################################

# DAY 12
# Vista de nuestro sitio web

- Inicializamos el Entorno
--> source venv/Scripts/activate

- Creamos los siguientes archivos en nuestra app.

- templates
    - Base.html
    - index.html
    - vista_choices.html

- Ejecutamos el servidor
--> python manage.py runserver

##################################################################

# Limpiar datos:
- Limpiar data de las tablas de nuestra db
```bash
python manage.py flush
```