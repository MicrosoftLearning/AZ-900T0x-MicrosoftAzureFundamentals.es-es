---
wts:
  title: '2: Crear una aplicación web (10 minutos)'
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 7b7acc368eff3c653579d54a12828e02a615a672
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908636"
---
# <a name="02---create-a-web-app-10-min"></a>2: Crear una aplicación web (10 minutos)

En este tutorial, crearemos una nueva aplicación web que ejecute un contenedor de Docker. El contenedor incluye un mensaje de bienvenida. 

Azure App Service es en realidad una colección de cuatro servicios, los cuales están diseñados para hospedar y ejecutar aplicaciones web. Los cuatro servicios (Web Apps, Mobile Apps, API Apps y Logic Apps) parecen diferentes, pero, al final, todos funcionan de manera muy similar. De los cuatro servicios, las Web Apps son las que se usan con mayor frecuencia y es el servicio que utilizaremos en este laboratorio.

# <a name="task-1-create-a-web-app"></a>Tarea 1: Creación de una aplicación web 

En esta tarea, creará una aplicación web de Azure App Service. 

1. Inicie sesión en el [Portal de Azure](http://portal.azure.com/). 

2. Desde la hoja **Todos los servicios**, busque y seleccione **App Services** y haga clic en **+ Agregar, + Crear, o + Nuevo**.

3. En la pestaña **Datos básicos** de la hoja **Aplicación web**, especifique la siguiente configuración (reemplace **xxxx** en el nombre de la aplicación web por letras y dígitos para que el nombre sea único a nivel global). Deje los valores predeterminados para todo lo demás, incluido el plan de App Service. 

    | Configuración | Value |
    | -- | -- |
    | Subscription | **Usar los valores predeterminados** |
    | Grupo de recursos | **Crear un grupo de recursos**|
    | Nombre | **myDockerWebAppxxxx** |
    | Publicar | **Contenedor de Docker** |
    | Sistema operativo | **Linux** |
    | Region | **Este de EE. UU.** |
    
    **Nota:** Recuerde reemplazar **xxxx** para que el nombre de su aplicación web sea único.

4. Haga clic en **Siguiente > Docker** y configure la información del contenedor.  

    | Configuración | Valor |
    | -- | -- |
    | Opciones | **Contenedor individual** |
    | Origen de la imagen | **Docker Hub** |
    | Tipo de acceso | **Public** |
    | Image and tag (Imagen y etiqueta) | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **Nota:** El comando de inicio es opcional y no es necesario en este ejercicio.

5. Haga clic en **Revisar y crear** y después en **Crear**. 

# <a name="task-2-test-the-web-app"></a>Tarea 2: Prueba de la aplicación web

En esta tarea probaremos la aplicación web.

1. Espere a que se implemente la aplicación web.

2. Desde **Notificaciones**, haga clic en **Ir al recurso**. 

3. En la hoja **Información general**, ubique la **URL**. Copie la URL en el Portapapeles.

    ![Captura de pantalla de la hoja de propiedades de la aplicación web. La URL está resaltada.](../images/0801.png)

4. Abra una nueva pestaña del explorador, pegue la dirección URL y pulse Intro. Se mostrará el mensaje Le damos la bienvenida a Azure Container Instances.

    ![Captura de pantalla de la página Le damos la bienvenida a Azure Container Instance.](../images/0802.png)

5. Vuelva a la hoja de **Información general** de su aplicación web y desplácese hacia abajo. Observará varios gráficos que permiten realizar un seguimiento de los datos entrantes y salientes y las solicitudes. Si repite el paso 4 varias veces, debería poder ver la telemetría correspondiente en estos gráficos. Esto incluye el número de solicitudes y el promedio de tiempo de respuesta. 

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.

Enhorabuena. Acaba de crear con éxito una aplicación de Azure App Service.
