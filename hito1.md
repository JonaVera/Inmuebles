# PROYECTO - INMUEBLE
## HITO 1
1. Iniciar Proyecto
2. Implementar postgres SQL 
3. Crear los modelos 
4. Crear 4 servicios en nuestro services.py

# Levantando un Proyecto

- Creamos el entorno, conectamos, instalamos Djando, instalamos psycopg2 para el uso de postgres.
- Intalamos dotenv para trabajar con variables de entorno, Creamos requirement para saber las dependencias que tenemos instaladas.

--> virtualenv venv
--> source venv/Scripts/activate
--> pip install django
--> pip install psycopg2
--> pip install python-dotenv
--> pip freeze > requirements.txt

- Creamos el proyecto (mysite) y creamos la aplicacion(m7_python).

--> django-admin startproject mysite .
--> python manage.py startapp m7_python 

- Añadimos la App (m7_python) a setting.py 
- Modificamos la Databases de setting.py para trabajar con postgres sql.
- Creamos services.py en nuestra app (m7_python), este nos permite realizar funciones.

####################################################################################

- Inicializamos el proyecto
--> source venv/Scripts/activate

- Creamos un archivo temp.py en nuestra app (m7_python), para realizar pruebas (testing).

- En la aplicación creamos archivos que usaremos más adelante:
- templates
    - base.html
- static
    - css
        - style.css
    - js
        - temp_scrip.js
    - img

- Junto al Readme creamos dos archivos más:
- .env
- .gitignore

- Modificamos la Databases de setting.py para trabajar con postgres sql.
- Configuramos e importamos el dotenv en setting.py
- Modificamos el .env para el uso de postgres

- Creamos la base de datos desafio en postgres sql, conectamos, verificamos tablas.
--> CREATE DATABASE mysite;
--> \c mysite;
--> \dt

- Realizamos la marca de migracion y la migracion, para cargar los modelos o aplicaciones 
que subieron por defecto. 
--> python manage.py makemigrations
--> python manage.py migrate
--> \dt

- Creamos el admin para más adelante.
--> python manage.py createsuperuser
- User = admin
- email = jv@gmail.com
- password = 1234

- Probamos el servidor:
--> python manage.py runserver

# Creamos Modelos y Relaciones
- Realizamos la marca de migracion y la migracion, para cargar los modelos
--> python manage.py makemigrations
--> python manage.py migrate

- Observamos las tablas que se crearon debido a los modelos.
--> \dt
 public  | m7_python_comuna           | tabla | postgres
 public  | m7_python_inmueble         | tabla | postgres
 public  | m7_python_region           | tabla | postgres
 public  | m7_python_solicitud        | tabla | postgres
 public  | m7_python_userprofile      | tabla | postgres
(15 filas)

- Podemos ver que contiene cada una y su relación:
--> select * from m7_python_comuna;
--> select * from m7_python_inmueble;
--> select * from m7_python_userprofile;

####################################################################################

- Inicializamos el proyecto
--> source venv/Scripts/activate
- Abrimos postgresql, conectamos el proyecto y revisamos tablas.
--> \c mysite;
--> \dt

# Creamos los Services
# Probamos la shell

- Creamos un nuevo usario:
Probamos con la shell para crear un nuevo usuario:
--> python manage.py shell
--> from m7_python.services import create_user
- Creamos un diccionario para pasar los datos del nuevo usuario:
--> new_user = create_user({
    "username": "Jack",
    "email": "jack@gmail.com",
    "first_name": "Jack",
    "last_name": "Vera",
    "password": "1234"
})
- Probamos shell:
--> new_user
<!-- <User: Jack> -->
--> exit()
- Probamos postgresql:
--> select * from auth_user;

- Probamos la region y comuna;
--> python manage.py shell
--> from m7_python.services import create_region, create_comuna
--> region = create_region("01", "Valparaiso")
- Probamos shell:
--> region
<!-- <Region: Valparaiso (01)> -->
--> comuna = create_comuna("0101", "Viña del Mar", "01")
--> comuna
<!-- <Comuna: Viña del Mar (0101)> -->
--> exit()
- Probamos postgresql:
--> select * from m7_python_region;
--> select * from m7_python_comuna;

- Probamos get all inmuebles y insertar inmueble:
--> python manage.py shell
--> from m7_python.services import get_all_inmuebles, insertar_inmueble
--> inmuebles = get_all_inmuebles()
--> inmuebles
<!-- <QuerySet []> # Lista Vacia -->

- Creamos un inmueble:
--> new_inmueble = insertar_inmueble({
    'id_user': 1,
    'tipo_inmueble':'Departamento',
    'comuna_cod': '0101',
    'nombre': 'Departamento privado',
    'descripcion': 'Economico y privado',
    'm2_construidos': 100,
    'm2_totales': 150,
    'num_baños': 2,
    'num_habitaciones': 3,
    'num_estacionamientos': 1,
    'direccion': 'Avenida Pajaritos',
    'precio': 120000000,
    'precio_ufs': 2500.0
})
--> new_inmueble
<!-- <Inmueble: Inmueble object (1)> -->
--> exit 
- Probamos postgresql:
--> select * from m7_python_inmueble;

- Probamos eliminar inmueble y actualizar disponibilidad inmueble:

--> python manage.py shell
--> from m7_python.services import eliminar_inmueble, actualizar_disponibilidad_inmueble
--> from m7_python.services import get_all_inmuebles
--> inmuebles = get_all_inmuebles()
--> inmuebles_list = list(inmuebles)
--> for inmueble in inmuebles_list:
        print(f'{inmueble.id}, {inmueble.nombre}, {inmueble.disponible}')
<!-- 1, Departamento privado, True -->

--> actualizar_disponibilidad_inmueble(23, False)
<!-- {'success': False, 'message': 'Inmueble no encontrado'} -->

- Elimanamos inmueble:
--> eliminar_inmueble(23)
<!-- {'success': False, 'message': 'Inmueble no encontrado'} -->
--> eliminar_inmueble(1)
<!-- {'success': True, 'message': 'Inmueble eliminado con éxito'} -->
exit()

- Probamos postgresql para ver si se elimino
select * from m7_python_inmueble;

# Limpiar datos:
- Limpiar data de las tablas de nuestra db
```bash
python manage.py flush
```