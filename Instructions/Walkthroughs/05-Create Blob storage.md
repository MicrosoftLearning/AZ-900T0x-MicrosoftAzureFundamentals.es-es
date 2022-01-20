---
wts:
    title: '05 - Crear almacenamiento de blobs (5 minutos)'
    module: 'Módulo 2 - Servicios principales de Azure (Cargas de trabajo)'
---
# 05: Crear almacenamiento de blobs (5 min)

En este tutorial, crearemos una cuenta de almacenamiento y luego trabajaremos con archivos de almacenamiento de blobs.

# Tarea 1: Crear una cuenta de almacenamiento 

En esta tarea crearemos una nueva cuenta de almacenamiento. 

1. Inicie sesión en Azure Portal en <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. En la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ Agregar, + Crear y + Nueva**. 

3. En la pestaña **Datos básicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente información (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea globalmente único). Deje los valores predeterminados para todo lo demás.

    | Configuración | Valor | 
    | --- | --- |
    | Suscripción | **Deje la suscripción predeterminada suministrada** |
    | Grupo de recursos | **Crear un nuevo grupo de recursos** |
    | Nombre de la cuenta de almacenamiento | **cuentadealmacenamientoxxxxx** |
    | Ubicación | **Este de EE. UU. (EE. UU.)**  |
    | Rendimiento | **Estándar** |
    | Redundancia | **Almacenamiento con redundancia local (LRS)** |
    
    **Nota**: -  Recuerde cambiar **xxxx** de modo que sea un **nombre de cuenta de almacenamiento** único.

5. Haga clic en **Revisar y crear** para revisar la configuración de su cuenta de almacenamiento y permitir que Azure valide la configuración. 

6. Una vez validada, haga clic en **Crear**. Espere la notificación de que la cuenta se creó correctamente. 

7. Desde la página de inicio, busque y seleccione **Cuentas de almacenamiento** y asegúrese de que su nueva cuenta de almacenamiento aparezca en la lista.

    ![Captura de pantalla de la cuenta de almacenamiento recién creada en Azure Portal.](../images/0401.png)

# Tarea 2: Trabaje con almacenamiento de blobs

En esta tarea, crearemos un contenedor de blobs y subiremos un archivo de blobs. 

1. Haga clic en el nombre de la nueva cuenta de almacenamiento, desplácese hasta la sección **Almacenamiento de datos** en el menú izquierdo y luego haga clic en **Contenedores**.

2. Haga clic en **+ Contenedor** y complete la información. Use los iconos de información para obtener más información. Cuando termine, haga clic en **Crear**.


    | Configuración | Valor |
    | --- | --- |
    | Nombre | **container1**  |
    | Nivel de acceso público| **Privado (sin acceso anónimo)** |
  

    ![Captura de pantalla del contenedor de blobs recién creado en la cuenta de almacenamiento en Azure Portal.](../images/0402.png)

4. Abra una nueva ventana del explorador y busque en **Bing** la imagen de una flor. Haga clic en la imagen con el botón derecho y guárdela en su VM. 

6. Una vez haya regresado a Portal, haga clic en **contenedor1** y luego seleccione **Cargar**.

5. Busque el archivo de la imagen que acaba de guardar en su equipo local. Selecciónelo y después seleccione Cargar.

   
6. Haga clic en la flecha **Avanzado**, deje los valores predeterminados pero revise las opciones disponibles y luego haga clic en **Cargar**.

    **Nota**: Puede cargar tantos blobs como quiera de esta manera. Los nuevos blobs se enumerarán dentro del contenedor.

7. Una vez que se carga el archivo, haga clic con el botón derecho en el archivo y observe las opciones que incluyen Ver/editar, Descargar, Propiedades y Eliminar. 

8. Si tiene tiempo, revise las opciones Archivos, Tablas y Consultas.

# Tarea 3: Supervisar la cuenta de almacenamiento

1. Vuelva a la hoja de la cuenta de almacenamiento y haga clic en **Diagnosticar y solucionar problemas**. 

2. Explore algunos de los problemas de almacenamiento más comunes. Observe que aquí hay varios solucionadores de problemas.

3. En la hoja de la cuenta de almacenamiento, desplácese hacia abajo hasta la sección **Supervisión** y haga clic en **Información**. Observe que hay información sobre Fallas, Rendimiento, Disponibilidad y Capacidad. Su información será diferente.

    ![Captura de pantalla de la página Insights de la cuenta de almacenamiento.](../images/0403.png)

¡Enhorabuena! Creó una cuenta de almacenamiento y luego trabajó con blobs de almacenamiento.

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
