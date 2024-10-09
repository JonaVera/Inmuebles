## HITO 5
# DAY 19
- Inicializamos el Entorno
--> source venv/Scripts/activate

# Vista view_list_solicitudes (arrendador)
- Creamos la vista (view_list_solicitudes) en views.py.
- Creamos el html (list_solicitudes.html) en la carpeta arrendador con su codigo.
- Agregamos el path (url view_list_solicitudes) e importamos la url.
- Agregamos la ({% url 'view_list_solicitudes' inmueble_id=inmueble.id %}) en el html (detail_inmueble) en (Ver Solicitudes)
- Vamos a forms.py creamos el formulario (Solicitudes) e importamos.

# Vista edit_status_solicitud (arrendador)
- Creamos la vista (edit_status_solicitud) en views.py.
- Agregamos el path (url edit_status_solicitud) e importamos la url.

- Ejecutamos el servidor
--> python manage.py runserver
<!-- - Entramos como toto ingresamos una solicitud del (apartament chic), ahora ingresamos como bruce y vemos las solicitudes que tiene y podemos aprobarla o rechazarla. -->

- Creamos las carpetas filtros dentro de templates con 3 archivos html.
- En views.py creamos Filtros - Services - Search,
definimos (buscar_por_nombre). Estos estara conectado a los archivos de la carpeta filtros, modificamos el index_arrendatario en la views.py.

-----------------------------------------------------------------------------------------------------
# DAY 20
## FILTROS


- Inicializamos el Entorno
--> source venv/Scripts/activate
- Ejecutamos el servidor
--> python manage.py runserver

Para subir al github ya inicializado:
- git add .
- git commit -m "Hito5 views arrendador"
- git push origin master