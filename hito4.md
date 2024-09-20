## HITO 4 
# DAY 16
- Inicializamos el Entorno
--> source venv/Scripts/activate

# Proteccion para no Autorizados (accesos)
- Creamos un no_autorizado.html con extension al base.html para accesos no autorizados.
- En views.py definimos una vista para el manejo de no autorizados.
- Agregamos path (url) de la vista en urls.py con su importacion.

# Formulario Inmueble (crear)
- Creamos en forms.py el formulario (InmuebleForm) e importamos Inmueble.
- Creamos el formulario o funcion de (create_inmueble_for_arrendador) en services.py
- Antes debemos crear un archivo llamado  decorators.py (archivo de seguridad) en la app, que sirvira para el arrendador y arrendatario, debemos importarlo en la vista.
- Importamos el (create_inmueble_for_arrendador y InmuebleForm) en views.py
- En views.py creamos la vista _Arrendador
- Creamos en templates en la carpeta arrendadador un archivo (create_inmueble.html)
- creamos el path (url) para el arrendador (create).

- Comentamos en views.py los @login_required, @rol_requerido('arrendador') en la vista de arrendaor para probar.

- Ejecutamos el servidor
--> python manage.py runserver

Entramos con bruce y realizamos /create.
<!-- Debemos tener cuidado reestructar el codigo con ctrl+alt+f en los html porque aveces mueve algun codigo y despues me tira error al correr la app -->

- Ahora vamos al navbar y en Crear Inmueble ponemos el redireccionamiento (url 'create_inmueble'), que nos sirve para acceder desde el boton.
- Probamos con los decoradores activados y creamos un inmueble.
<!-- Podemos observar que al completar y crear el inmbueble este nos redirige al home y podemos ver el inmueble creado. -->

# Formulario Inmueble (editar)
- Creamos la vista edit_inmueble en views.py y la importamos.
- Agregamos su path (url) y la importamos.
- Creamos el templates de edit_inmbueble.html en arrendador.
- En el dashboard_arrendador.html agregamos la url "{% url 'edit_inmueble' inmueble_id=i.id %}

- Ejecutamos el servidor
--> python manage.py runserver
<!-- - Probamos el boton editar inmueble en la app corremos el servidor. -->

#___________________________________________________________________________________________________________________
# DAY 17
- Inicializamos el Entorno
--> source venv/Scripts/activate

# Vista del Arrendador(detail_inmueble)
- Creamos un archivo detail_inmueble.html en los templates.
- Creamos el path (url) detail_inmueble y la importamos.
- Creamos la vista detail_inmbueble
- En el dashboard_arrendador.html pasamos la url 
"{% url 'detail_inmueble' inmueble_id=i.id %}"

- Probamos el detail con bruce:
- Ejecutamos el servidor
--> python manage.py runserver
<!-- Podemos observar que al ejecutar la app y seleccioanr una imagen nos redirecciona a /detail, segun el arrendador -->

- Lo probamos con arrendatario toto:
- Debemos poner la url "{% url 'detail_inmueble' inmueble_id=i.id %}" en el archivo index_arrendatario.html de la carpeta arrendatario.

# Vista del Arrendador(eliminar_inmueble)
- Creamos el delete_inmueble.html en la carpeta arrendador con su formulario.
- En dashboard_arrendador ponemos la url {% url 'delete_inmueble' inmueble_id=i.id %} para eliminar.
- Creamos el path (url) delete_inmueble
- Creamos la vista delete_inmueble

<!-- Pobramos el eliminar en la app, corremos el servidor.
Al Eliminar nos redirige a /dashboard/inmueble/delete/21/ y nos preguntas si estamos seguro. -->

#___________________________________________________________________________________________________________________
# DAY 18
- Inicializamos el Entorno
--> source venv/Scripts/activate

# Vista (Cambiar Disponibilidad)
- Creamos la vista (edit_disponibilidad_inmueble) en views.py
- Creamos el path (url: edit_disponibilidad_inmueble) en urls.py e importamos su vista.
- Vamos a templates (detail_inmbueble.html), añadimos el path (url) en Cambiar Disponibilidad.
- Creamos el formulario (EditDisponibilidadForm) en forms.py y lo importamos en views.py
- Completamos el codigo en views.py con el formulario que creamos y el services. Recordar importar el services.
- Creamos un archivo templates en la carpeta arrendador llamado (edit_disponibilidad con su codigo) 

- Probamos la app.
- Ejecutamos el servidor
--> python manage.py runserver

<!-- - Al ejecutar el servidor podemos ingresar como bruce, seleccionamos una vivienda y podemos cambiar su disponibilidad, este nos redirigira a otra ruta /dashboard/detail/14/ y podremos modifacar su estado de disponible o no. Al hacerlo esto nos llevara al home y podremos ver el estado en su vivienda. -->

# Vista Arrendatarios
# Vista (send_solicitud)
- vamos a (datail_inmueble.html) pegamos la url (send_solicitud) del boton (Solicitar)
- Creamos el path (url send_solicitud) y lo importamos.
- Creamos un html en la carpeta arrendatario llamado (send_solicitud.html) con su codigo.
- Creamos la vista (send_solicitud) en views.py e importamos el modelod (Solicitud).

<!-- - Probamos la app.
Ingresamos como arrendatario (toto), ingresamos a una vivienda y nos saldra (solicitar), este nos dara un mensaje a la base de datos y nos redirigira al home. -->

# Vista (view_list_user_solicitudes)
- Creamos un html en la carpeta arrendatario llamado (list_user_solicitudes.html) con su codigo.
- Creamos el path (url view_list_user_solicitudes) y la importamos.
- Creamos la vista (view_list_user_solicitudes) en views.py e importamos sus modelos.
- Vamos al navbar y ponemos la {% url 'solicitudes' %} en (Ver Lista de Solicitudes).

<!-- - Probamos la solicitud:
Podemos ver en el home (ver lista de solicitudes) las soilicitudes que han hecho los arrendatarios. -->



