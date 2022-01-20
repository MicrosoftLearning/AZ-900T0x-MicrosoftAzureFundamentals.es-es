---
wts:
    title: '16: Implementar el etiquetado de recursos (5 min)'
    module: 'Módulo 05: Descripción de las características de identidad, gobernanza, privacidad y cumplimiento'
---
# 16: Implementar el etiquetado de recursos (5 min)

En este tutorial, crearemos una asignación de directiva que requiera etiquetado, crearemos una cuenta de almacenamiento y probaremos el etiquetado; veremos recursos con una etiqueta específica, y quitaremos la directiva de etiquetado.

# Tarea 1: Crear una asignación de directiva 

En esta tarea, configuraremos la directiva **Requerir una etiqueta en los recursos** y la asignaremos a nuestra suscripción. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Directiva**.

3. Desplácese hacia abajo hasta la sección **Creación**, haga clic en **Asignaciones** y luego haga clic en **Asignar directiva** desde la parte superior de la página.

4. Tenga en cuenta que el **Ámbito** para nuestra directiva será toda la suscripción. 

5. Bajo **Datos básicos**, seleccione el botón de puntos suspensivos **Definición de directiva** (al lado derecho del cuadro de texto). En el cuadro **Buscar**, escriba el valor **etiqueta**. Aparecerá una lista de directivas relacionadas con la palabra **etiqueta**. Desplácese hacia abajo hasta que encuentre la definición **Requerir una etiqueta en los recursos**, haga clic en ella y en **Seleccionar**.

   ![Captura de pantalla del panel Definiciones disponibles con la opción Requerir una etiqueta en los recursos seleccionada.](../images/1701.png)
   
6.  En la pestaña **Parámetros**, escriba **Empresa: Contoso** en la etiqueta de nombre del par clave-valor. Haga clic en **Revisar y crear** y, luego, en **Crear**.

    ![Captura de pantalla del panel Asignar directiva con el nombre de etiqueta completado.](../images/1702.png)

7. La asignación de la directiva **Requerir una etiqueta en los recursos** ahora está implementada. Cuando se crea un recurso, debe incluir una etiqueta con la clave Empresa: Contoso.
   **Nota: Debe esperar un máximo de 30 minutos hasta que se aplique la directiva.** 

   ![Captura de pantalla del panel Directiva: Asignaciones con la asignación de ubicaciones permitidas resaltada.](../images/1703.png)

# Tarea 2: Crear una cuenta de almacenamiento para probar el etiquetado requerido

En esta tarea crearemos cuentas de almacenamiento para probar el etiquetado requerido. 

1. En Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ Agregar, + Crear, o + Nuevo**.

2. En la pestaña **Datos básicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente información (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea único a nivel global). Deje los valores predeterminados para todo lo demás.

    | Configuración | Valor | 
    | --- | --- |
    | Suscripción | **Usar los valores predeterminados** |
    | Grupo de recursos | **Crear nuevo grupo de recursos** |
    | Nombre de la cuenta de almacenamiento | **cuentadealmacenamientoxxxx** |
    | Ubicación | **Este de EE. UU. (US)** |

3. Haga clic en **Revisar y crear**. 

    **Nota:** Estamos probando para ver qué sucede cuando no se suministra la etiqueta. Tenga en cuenta que las directivas pueden tardar hasta 30 minutos en surtir efecto.

4. Recibirá un mensaje de error de validación. Haga clic en el mensaje **Haga clic aquí para ver los detalles**. En la hoja **Errores**, en la pestaña **Resumen**, observe el mensaje de error que indica que la directiva no permite el recurso.

    **Nota:** Si ve la pestaña Error sin procesar, verá el nombre de etiqueta específico que se necesita. 

    ![Captura de pantalla de rechazado debido a un error de directiva.](../images/1704.png)


5. Cierre el panel de **Error** y haga clic en **Anterior** (parte inferior de la pantalla). Proporcione la información de etiquetado. 

    | Configuración | Valor | 
    | --- | --- |
    | Nombre de etiqueta | **Empresa: Contoso** (puede no estar en la lista desplegable) |

6. Haga clic en **Revisar y crear** y compruebe que la validación haya sido exitosa. Haga clic en **Crear** para implementar la cuenta de almacenamiento. 

# Tarea 3: Ver todos los recursos con una etiqueta específica

1. En Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Etiquetas**.

2. Tenga en cuenta todas las etiquetas y sus valores. Haga clic en la **Compañía:** Par clave/valor **Contoso**. Esto mostrará una hoja que muestra la cuenta de almacenamiento recién creada, siempre que haya incluido la etiqueta durante su implementación. 

   ![Captura de pantalla de las etiquetas con compañía y contoso seleccionados.](../images/1705.png)

3. En el Portal, muestre la hoja **Todos los recursos**.

4. Haga clic en **Agregar filtro** y agregue la clave de etiqueta de la **Compañía** como la categoría de filtro. Con el filtro aplicado, solo se mostrará su cuenta de almacenamiento.

    ![Captura de pantalla del filtro Todos los recursos con la compañía seleccionada.](../images/1706.png)

# Tarea 4: Eliminar la asignación de directiva

En esta tarea eliminaremos la directiva **Requerir una etiqueta en los recursos** para que no afecte nuestro trabajo futuro. 

1. En el portal, desde la hoja **Todos los servicios**, busque y seleccione la **Directiva**.

2. Haga clic en la entrada de la directiva **Requerir una etiqueta en los recursos**.

3. Haga clic en **Eliminar asignación** en el menú superior.

4. Haga clic en **Sí** para confirmar que desea eliminar la asignación de directiva en el cuadro de diálogo **Eliminar asignación**

5. Si tiene tiempo, cree otro recurso sin una etiqueta para asegurarse de que la directiva ya no está vigente.

¡Enhorabuena! En este tutorial creamos una asignación de directiva que requería etiquetado, creamos un recurso (cuenta de almacenamiento) y probamos la directiva para el etiquetado, vimos recursos con una etiqueta específica y eliminamos la directiva de etiquetado.


**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuación, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
