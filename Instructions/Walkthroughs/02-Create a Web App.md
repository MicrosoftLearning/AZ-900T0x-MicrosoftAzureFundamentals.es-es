---
wts:
    title: '02 - Crear una aplicación web (10 minutos)'
    module: 'Módulo 2 - Servicios principales de Azure (Cargas de trabajo)'
---
# 02: Crear una aplicación web (10 min)

En este tutorial, crearemos una aplicación web que ejecuta un contenedor de Docker. El contenedor de Docker contiene un mensaje de bienvenida. 

Azure App Service es en realidad una colección de cuatro servicios, todos ellos diseñados para ayudarle a hospedar y ejecutar aplicaciones web. Los cuatro servicios (Web Apps, Mobile Apps, API Apps y Logic Apps) tienen aspectos diferentes, pero, al final, todos funcionan de manera muy similar. De los cuatro servicios, las Web Apps son las que se usan con mayor frecuencia y es el servicio que utilizaremos en este laboratorio.

# Tarea 1: Crear una aplicación web 

En esta tarea, creará una aplicación web de Azure App Service. 

1. Inicie sesión en [Azure Portal](http://portal.azure.com/). 

2. En la hoja **Todos los servicios**, busque y seleccione **App Services** y luego haga clic en **+ Agregar, + Crear, + Nuevo**.

3. En la pestaña **Datos básicos** de la hoja **Aplicación web**, especifique la siguiente configuración (reemplace **xxxx** en el nombre de la aplicación web por letras y dígitos para que el nombre sea único a nivel mundial). Deje los valores predeterminados para todo lo demás, incluido el plan de App Service. 

    | Configuración | Valor |
    | -- | -- |
    | Suscripción | **Utilice la suscripción predeterminada suministrada** |
    | Grupo de recursos | **Crear un nuevo grupo de recursos**|
    | Nombre | **myDockerWebAppxxxx** |
    | Publicar | **Contenedor de Docker** |
    | Sistema operativo | **Linux** |
    | Región | **Este de EE. UU.** |
    
    **Nota:** Recuerde cambiar las **xxxx** para que el nombre de su aplicación web sea único.

4. Haga clic en **Siguiente > Docker** y configure la información del contenedor.  

    | Configuración | Valor |
    | -- | -- |
    | Opciones | **Contenedor individual** |
    | Origen de la imagen | **Docker Hub** |
    | Tipo de acceso | **Pública** |
    | Imagen y etiqueta | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **Nota:** El comando de inicio es opcional y no es necesario en este ejercicio.

5. Haga clic en **Revisar y crear**, y luego haga clic en **Crear**. 

# Tarea 2: Probar la aplicación web

En esta tarea probaremos la aplicación web.

1. Espere a que se implemente la aplicación web.

2. Desde **Notificaciones**, haga clic en **Ir al recurso**. 

3. Localice la **URL** en la hoja **Información general**. Copie la URL al portapapeles.

    ![Captura de pantalla de la hoja de propiedades de la aplicación web. La URL está resaltada.](../images/0801.png)

4. Pegue el URI en una nueva ventana del explorador y presione Entrar. Se mostrará el mensaje "¡Le damos la bienvenida a Azure Container Instances!".

    ![Captura de pantalla de la página Le damos la bienvenida a Azure Container Instance.](../images/0802.png)

5. Vuelva a la hoja **Información general** de su aplicación web y desplácese hacia abajo. Verá varios gráficos que realizan un seguimiento de los datos entrantes y salientes y las solicitudes. Si repite el paso 4 unas cuantas veces, debería poder ver la telemetría correspondiente en estos gráficos. Esto incluye el número de solicitudes y el tiempo de respuesta promedio. 

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.

¡Enhorabuena! Ha creado correctamente un Servicio de aplicaciones de Azure.
