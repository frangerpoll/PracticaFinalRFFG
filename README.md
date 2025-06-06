# PRACTICA FINAL RIPOLL FELIPE FRANCISCO GERARDO

##

## ANÁLISIS DEL TEXTO

- ### NECESIDAD DEL CLIENTE

    Aplicación que gestione los gastos producidos por los coches de los usuarios de una manera sencilla y segura

   (Modificar el .env vacío para que pueda editarlo dejándolo en las instrucciones)

- ### PAUTAS A SEGUIR
    - Debe seguir el modelo MVC
    - Vista por consola con Swing o JSP
    - Datos almacenados en BBDD (usando JDBC)
    - Control de errores
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

    - Debe haber un sistema de control de eerores que notifique al usuario del error que ha cometido y como solventarlo

  ## FLUJO DEL PROGRAMA

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
                     


- Una vez registrado, el usuario volverá a la pantalla de inicio para iniciar sesión con sus datos y tras eso poder entrar al dashboard para crear y editar los coches