# PRÁCTICA FINAL RIPOLL FELIPE FRANCISCO GERARDO

##


## ¿QUÉ ES AHORRAKART?
### - Ahorrakart es una aplicación diseñada para que los usuarios lleven una gestión de los gastos fijo, variables e inesperados que puedan tener sus vehículos así como llevar una lista de los mismo con sus características principales
### - Con esta aplicación el usuario podrá:
- Registrarse y tras ello iniciar sesión donde tendrá un perfil propio con varias funcionalidades
- Añadir coches con sus características principales y ver una lista completa
- Añadir copropietarios de ese vehículo
- Editar y eliminar un vehículo ya creado
- Llevar un control de gastos apuntando motivos, pagos, etc.
- Filtrar los tipos de gastos para llevar un control más preciso

## INSTRUCCIONES

- ### PREPARACIÓN
 Para poder ejecutar correctamente esta aplicación hay que tener:
 - IDE Eclipse (recomendable la versión profesional)
 - Tener instalado un descompresor de archivos como Winrar
 - Tener JDK (en este proyecto se está usando el JDK 22) instalado en el ordenador para poder desarrollar la aplicación
 - Tener las librerías de MySQL Connectors para que pueda utilizarse la base de datos sin problema ([enlace aquí](https://dev.mysql.com/downloads/connector/j/)). Para este proyecto se está usando la versión 9.3 
 - Tener instalada alguna herramienta de diseño de bases de datos como **MySQL Workbench**  por si se quiere comprobar que el script ``PracticaFinalRFFG.sql`` que crea la base de datos, funciona correctamente 

 - El archivo ``.env`` se usa para gestionar las credenciales y configuración de la base de datos. Este archivo viene con las credenciales vacías para que se rellenen con la información de la Base de Datos que se vaya a utilizar. Así también se evitan problemas de seguridad.
 
    El archivo se encuentra en dentro de las carpetas: _PracticaFinalRFFG\PracticaFinalRFFG\\.env_

    Los datos son:

    ````
    DB_HOST= enlace a la ubicación de la BBDD
    DB_PORT= Puerto utilizado por la BBDD
    DB_USERNAME= usuario de la BBDD
    DB_PASSWORD= contraseña 
    DB_DATABASE= nombre de la BBDD
    ````
    En la clase ```Configurations``` ya está programado para que .env pueda abrirse desde cualquier ordenaddor sin tener que cambiar la ruta gracias a la siguiente línea de código:
    ````
    List<String> configLines = FileUtils.readLines(envPath.toString());
    ````
    Así que solo sería necesario añadir los datos de la BBDD al archivo .env 


- ### INICIALIZACIÓN DE LA APLICACIÓN
- Tras descargar el archivo y descomprimir la carpeta principal ``PracticaFinalRFFG``, aparecerá otra carpeta comprimida con el nombre ``PracticaFinalRFFG`` y este ``Readme``. Esa carpeta comprimida es la que hay que descomprimir e importar en Eclipse como un proyecto Java

 - Crear la base de datos ejecutando el script ``PracticaFinalRFFG.sql`` que se encuentra dentro de la carpeta PracticaFinalRFFG en:
 _PracticaFinalRFFG\src\base_de_datos\PracticaFinalRFFG.sql_
 
 - Asegurarse de que el archivo .env contenga todos estos campos y estén rellenos con tus datos:

    ````
    DB_HOST= enlace a la ubicación de la BBDD
    DB_PORT= Puerto utilizado por la BBDD
    DB_USERNAME= usuario de la BBDD
    DB_PASSWORD= contraseña 
    DB_DATABASE= nombre de la BBDD

    ````
- Añadir el .jar del conector MySQL al classpath
 - Ejecutar ``Main.java`` _dentro del paquete main que está dentro de la carpeta src_

 - Aparecerá una pantalla de Bienvenida con 2 opciones: **Registrarse** e **Iniciar Sesión**
    - Al registrarte simplemente te pedirán un nombre de usuario y una contraseña, tras esto la app te notificará que guardes el _UUID_ que te dan y volverá a la pantalla de Bienvenida
    - Al iniciar sesión el usuario irá a su perfil personal donde podrá ver varias opciones

- Desde aquí el usuario puede hacer diversas funciones. Pondré un ejemplo para hablar de ellas entrando desde el perfil de un usuario guardado en la BBDD:

    ```
    - Usuario: Chopper
    - Contrasña: contraseña123
     ```
    **VER LISTA**  
    
    -Al entrar en su cuenta, Chopper puede ver su lista de coches al hacer click en ella.
        - Si hace click en el coche _Brachio Tank V_ y pulsa en el botón Ver detalles verá que tiene como copropietario a su amigo _Usopp_

    **CREAR COCHE**  
    
    -Al pulsar en crear coche se abrirá un formulario para añadir datos como marca, modelo, color y el código UUID por si quiere añadir a algún copropietario

    **EDITAR COCHE**  
    
    -Al pulsar en editar coche se abrirá la lista de coches disponibles, seleccionará uno de ellos y podrá editar algún dato

    **ELIMINAR COCHE**  
    
    -Al pulsar en eliminar coche se abrirá un listado de los coches y si seleccionas un coche y pulsas en el botón de eliminar, se borrará de la lista

    **AÑADIR GASTO DE UN COCHE**  
    
    -Al pulsar en añadir Gasto de un coche se abrirá un desplegable que te permitirá seleccionar el coche y añadir el gasto junto a campos como la fecha, importe, seleccionar el tipo, etc.

    **VER GASTOS**  
    
    -En esta tabla se pueden ver los gastos producidos por  un coche y filtrarlos por año y Km. Siguiendo el ejemplo si se pone el año 2020 para el coche _Brachio Tank V_ saldrá un gasto de 20€ en gasolina




## DESARROLLO DE LA IDEA: ANÁLISIS DEL TEXTO

- ### NECESIDAD DEL CLIENTE

    Aplicación que gestione los gastos producidos por los coches de los usuarios de una manera sencilla y segura


- ### PAUTAS A SEGUIR
    - Debe seguir el modelo MVC
    - Vista por consola con Swing o JSP
    - Datos almacenados en BBDD (usando JDBC)
    - Control de errores con Try y catch y otros procedimientos
    - Gestionar la relación entre usuarios y coches

- ### INFORMACIÓN

    - Existe una clase Usuario que tiene las propiedades ``nombre`` (único), una clave ``UUID`` (asignado automáticamente) y

    - Existe una clase Coche que estará vinculada a uno o varios propietarios y tendrán las propiedades de ``marca``, ``modelo``, ``matrícula``, ``color`` y ``año``

    - Existe una clase Gastos que tiene con una lista predefinida donde venga el tipo de gasto: ``echarGasolina``, ``revision``, ``cambioDeAceite``, ``itv``, ``otros``, (ruedas, limpiaparabrisas, anticongelante, limpieza, etc.). También las propiedades de ``Kilometraje`` (en el momento que se hizo el gasto), ``fechaGasto``, ``importe`` y ``descripcion`` (opcional)

-  ### ACCIÓN

    - Lo usuarios pueden registrarse en el sistema. AL registrarse se les asigna una clave ``UUID`` única
    - Una vez registrados, los usuarios pueden acceder a su cuenta iniciando sesión con sus datos
    - Los usuarios pueden crear coches
    - Los usuarios pueden darse de alta como propietarios de ese coche y registrar a sus familiares, amigos, etc. como co-propietarios del vehículo si conocen la clave  ``UUID`` de los mismos. Tendrán que introducirlo los propietarios por pantalla
    - Habrá una interfaz donde el propietario pueda:
        - Ver el listado de coches
        - Editar el coche 
        - Eliminar coche 
        - Añadir los gastos del coche

         _Todos los usuarios que sean propietarios del mismo coche pueden realizar todas estas acciones_

    - El usuario puede ver un total de todos los gastos de su coche en formato tabla.
        - Esta tabla tendrá un filtro que le permitirá ver resultados por año, fecha y kilómetros

    - Debe haber un sistema de control de errores que notifique al usuario del error que ha cometido y como solventarlo

 -  ### FLUJO DEL PROGRAMA
```
 [Menu de inicio]
       ↓        ↓
   [Register] [Login]
                    ↓
                [Dashboard]
                     ↓
                [Coches] <→ [Crear coche] → [Detalles del coche]
                    ↓                       ↓
                  [Editar coche]       [Gastos] ←→ [Nuevo gasto]
                       ↓                       ↓
                 [Eliminar coche]     [Tabla resumen con filtros]
                             ↓
                     [Agregar co-propietario]
                     
```

- Una vez registrado, el usuario volverá a la pantalla de inicio para iniciar sesión con sus datos y tras eso poder entrar al dashboard para crear y editar los coches
