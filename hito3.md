## HITO 3 
# Implementacion del Login y Logout

- Decorador de seguridad views.py de pagina web
- En views.py de la app debemos poner un decorador ( @login_required ) como seguridad que sirve para no mostrar la vista de los inmuebles sino el login.
<!-- Cuando corremos el servidor, en la url de la pagina nos dice, que quisieron entrar a barra 
pero como no esta logeado lo redirige a login y si se logea lo mandara a barra. -->

- Agregamos un path a nuestra urls.py del sitio web
<!-- Nos permite incluir el accounts del login, logout y otras url que contiene django. -->

- En settings.py de nuestro sitio web, al final del codigo ingresamos las rutas de redireccionamiento del login y el logout.

- Modificamos el Base.html, agregamos el load static para trabajar con todo lo que sea estatico.
Añadimos el CDN de bootstrap, creamos un codigo para tener una vista del login y logout, modularizamos el logout y agragamos los script.

- Modificamos el Index.html para que extienda el base.html

- Modularizacion de(logout) en el base.html
- Desde el base.html copiamos el formulario del logout y lo borramos, lo pegamos en el archivo que creamos del logout.
- Desde el mismo base.html hacemos un include para modularizar el logout de registration.

- El archivo login es una codigo que nos brinda Django desde su documentacion para poder realizar el login y logout.

- Inicializamos el Entorno
--> source venv/Scripts/activate

- Ejecutamos el servidor
--> python manage.py runserver

Logearse:
- username: bruce
- password: 1234

django - usuario valido
Nos dirige a barra y nos saldra el boton de cerrar sesion, nuevamente el boton para logearse

# Estructura HMTL
- templates
    - base.html
    - navbar.html
    - footer.html
    - about.html
    - profile_edit.html
    - profile_detail.html

- templates
    - registration
        - login.hmtl 
        - logout.html
        - register.html
        - register_rol.html
<!-- login.html es un Formulario de Django copiado. --> 

- Opcional dentro del templates puede haber una carpeta llamada (partiels), que nos permite tener fragmentos html que pueden ser incluidos en otro html.

#############################################################################################################

# DAY 13
- Inicializamos el Entorno
--> source venv/Scripts/activate

- navbar.html, copiamos su codigo, moficamos dentro del codigo sus url en (href) ya que no tenemos algunas creadas con sus path y nos rompera.

- footer.html, modificamamos y agremos un estilo

- Modificamos el base.html, lo modularizamos para el navbar y el footer. borramos lo hay dentro del body las url home y login.

- Ejecutamos el servidor
--> python manage.py runserver
<!-- Observamos como quedo la pagina web -->
- Usuario Arrendador
Si ingresamos con el usuario (bruce) nos mostrara la url barra con los inmbuebles y en el navbar nos saldra un (crear inmueble), ya que bruce es un arrendador.

- Usuario Arrendatario
Si ingresamos con el usuario (toto) nos mostrara la url barra con los inmbuebles y en el navbar nos saldra un (ver lista de solicitudes), ya que toto es un arrendatario

# Formulario de Registro

- Creamos el archivo forms.py para los formularios dentro de nuestro sitio web.

- Agregamos un parrafo en el login.html, que sirvira como boton para logearse y nos llevara al register.html. Desde el register.html nos redirigira al register_rol.html.

- Vamos a forms.py y pegamos el codigo del formulario en (register form) e importamos el user.

- Pegamos el formulario de registro en register.html

- En views.py de la app creamos la vista para el registro.
- Desde forms y models importamos Customusercreationform, userprofile y login. Definimos el register.
- En la urls.py de la app, añadimos el path de register(url) y definimos register en import.
- En el navbar vamos añadir en un href la url register.
<!-- 
Al correr la pagina web podemos observar que al presionar registrarse nos manda a otro formulario. -->

- Ahora vamos a login.html y agregamos el href de register, para el redireccionamiento del register.
<!-- Ppdemos Observar en la web que en el formulario del login nos muestra un boton (registrarse aqui) este no redirige al formulario registrarse.  -->

- Ahora vamos al views.py de la app y añadimos al lado de import render, el redirect. para que el boton de register nos mande al home.
- Ahora registramos a un usuario (no debe estar en la base de datos creado):
    - username: juana101
    - email:    ju@gmail.com
    - password: jack2007
<!-- Al registrarse este nos dirige a home -->

# Formulario de Registro_ROL y edit_profile (UserProfile y userForm)

- Dentro de forms.py creamos en register-form la clase userprofileform con su model userprofile y sus campos. 
Tambien añadimos el edit profile
- Añadimos el formulario a register_rol.html
- Creamos en services.py desde models importamos el Userprofile
- Ahora vamos a la vista (views.py app), importamos el services que creamos, importamos el formulario UserProfileForm, definimos el register_rol.
- Vamos a la urls.py de la app y creamos el path de register_rol.
- Por ultimo modificamos en la views.py en register_rol donde nos redirige al home, la cambiamos por register_rol.

- Ejecutamos el servidor
--> python manage.py runserver

- Probamos el login iniciamos sesion con bruce y cerramos seseion.
- Si ahora nos dirigimos al formulario de registrarse y creamos un usuario este hara un get a register_rol y hara una relacion con UserProfile y user y los demas campos estaran vacios en userprofile
    - username: mimi
    - email:    mimi@gmail.com
    - password: jack2007
- Nos abrira el formulario con sus otro datos vacios que debemos completar.
    - rut: 135791234
    - direccion: España 333
    - telefono: 2211002266
    - rol: arrendador
<!-- Podemos observar en la base de datos que se crearon los datos que le falta al usuario mimi. -->

# Profile_detail (ver un perfil)
- Añadimos un codigo al profile_detail
- Vamos a views y definimos una vista para el perfil (profile_view).
- Agregamos la urls para la vista (profile_view).
- Agregamos el url profile en el navbar en el Bienvenido, nos mostrara la vista del perfil.

<!-- Si Corremos el server podemos observar que en el navbar nos aparece (Bienvenido mimi) al presionarlo nos dirige al formulario para ver el perfil del usuario con sus datos. -->

#############################################################################################################

# DAY 14
- Inicializamos el Entorno
--> source venv/Scripts/activate

# /acerca (about)
- Creamos el about.html en (templates), copiamos el codigo.
- Creamos la vista en views.py para el about.html
- Agregamos el path (about) en la urls.py
- Ahora en el navbar debemos poner la (url 'about') para que al presionar (Acerca), nos muestra /about.
<!-- Verificamos en la web si nos redirige. -->

# /contacto (contact)
- Creamos el contact.html en (templates), copiamos el codigo.
- En (models.py) creamos el modelo de ContactForm con unos campos.
- Creamos el formulario Contact en (form.py) e importamos en models.

<!-- Para que el modelo y formulario funcione debemos realizar las migraciones. -->
--> python manage.py makemigrations
--> python manage.py migrate

- Si ingresamos como admin, debemos tener registrados los modelos en admin.py
- En admin.py importamos los models y registramos los models.

<!-- Verificaremos si se creo la tabla en la base de datos -->
- Conexion a la base datos:
    --> \c hito_2;
    --> \dt
    --> select * from m7_python_contactform;

- En views.py creamos la vista para (contact), importando el modelo.
- Agregamos el path (contact) en la urls.py
- Ahora en el navbar debemos poner la (url 'contact') para que al presionar (contacto), nos muestra /contact.

- Probamos: Ingresamos con bruce y presionamos (Contacto) nos redirigira al /contact.
- Completamos los campos correspondientes
    - nombre y apellido: pepe
    - correo: de@de.com
    - mensaje: Prueba de Contacto
- Al enviar el contacto este nos redirigira a /home y el mensaje podremos verlo en la base de datos.

<!-- hito_2=# select * from m7_python_contactform;
 id | customer_email | customer_name |      message
----+----------------+---------------+--------------------
  1 | de@de.com      | Pepe          | Prueba de Contacto
(1 fila) -->

# Vista Editar Perfil
- Creamos la vista de editar perfil en views.py
- En (profile_edit.html) extendemos el base.html
- Importamos la urls de editar perfil.
- Ahora vamos a (profile_detail.html) y añadimos la url edit_profile. (redireccionamiento a edit_profile)
<!-- Ejecutamos server para pruebas de redireccionamiento en la web. -->

---------:
- Modidifamos el (profile_edit) con un codigo nuevo.
- En la vista importamos los modelos UserForm y UserEditProfileForm. Modificamos el codigo del (editar perfil.) del services edit_profile_view.

<!-- Codigo Anterior de profile_edit.html
{% extends 'base.html' %}
{% block content %}
<h2>Hola soy el espacio FORM para editar el PERFIL</h2>
{% endblock %} -->
<!-- Tenemos que tener en cuenta si comentamos en el codigo un content y creamos otro esto rompera el codigo -->

- Ejecutamos server para pruebas de redireccionamiento en la web y nuevas configuraciones del edit profile.
- Editamos el perfil del usuario

#############################################################################################################

# DAY 15
- Inicializamos el Entorno
--> source venv/Scripts/activate

# Creacion de un Services
- Abrimos el services.py y creamos la funcion:(get_inmuebles_for_arrendador)

- Ejecutamos la Shell para probar el services y la funcion que creamos.
--> python manage.py shell
--> from m7_python.services import get_inmuebles_for_arrendador
--> from m7_python.models import User
--> bruce = User.objects.get(id=1)
<!-- >>> bruce
<User: bruce> -->
--> toto = User.objects.get(id=5)

- Obtener inmuebles de Bruce:
--> inms = get_inmuebles_for_arrendador(bruce)
<!-- Trae 4 inmbuebles -->
<!-- >>> inms
<QuerySet [<Inmueble: Inmueble object (1)>, <Inmueble: Inmueble object (13)>, <Inmueble: Inmueble object (14)>, <Inmueble: Inmueble object (20)>]>
>>> -->

- Obtener inmuebles de Toto:
--> inms2 = get_inmuebles_for_arrendador(toto)
<!-- no es arrendador -->
<!-- >>> inms2
[] --> Lista Vacia
exit()

# Vistas (arrendatario y arrendador)
- Modificamos el indexView de nuestro views.py
- Creamos carpetas para las vistas del arrendatario y arrendador en templates con sus html.
- Creamos las vistas de arrendatario y arrendador
- Creamos los path (url) de arrendatario y arrendador

- Ejecutamos el servidor
--> python manage.py runserver
<!-- Podemos observar las diferentes vistas segun arrendatario o arrendador -->


