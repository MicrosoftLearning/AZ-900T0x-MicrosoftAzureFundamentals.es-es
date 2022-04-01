---
wts:
  title: '3: Implementar Azure Container Instances (10 minutos)'
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 0616be96840b14f7580c7d2b16cb43b211c6e3a2
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908621"
---
# <a name="03---deploy-azure-container-instances-10-min"></a>3: Implementar Azure Container Instances (10 minutos)

En este tutorial crearemos, configuramos e implementamos un contenedor mediante Azure Container Instances (ACI) en Azure Portal. El contenedor es una aplicación web Bienvenido a ACI que muestra una página HTML estática. 

# <a name="task-1-create-a-container-instance"></a>Tarea 1: Creación de una instancia de contenedor 

En esta tarea, se creará una instancia de contenedor para la aplicación web.  

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Container instances** y haga clic en **+ Agregar, + Crear, o + Nuevo**. 

3. Dé los siguientes detalles básicos para la nueva instancia de contenedor (deje los valores predeterminados para todo lo demás): 

    | Configuración| Value|
    |----|----|
    | Subscription | ***Usar los valores predeterminados*** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre del contenedor| **mycontainer**|
    | Region | **(EE. UU.) Este de EE. UU.** |
    | Origen de la imagen| **Docker Hub u otro registro**|
    | Tipo de imagen| **Public**|
    | Imagen| **mcr.microsoft.com/azuredocs/aci-helloworld**|
    | Tipo de SO| **Linux** |
    | Size| ***Deje la opción predeterminada.***|


4. Configure la pestaña Redes (reemplace **xxxx** con letras y dígitos para que el nombre sea único a nivel global). Deje todas las demás configuraciones con sus valores predeterminados.

    | Configuración| Value|
    |--|--|
    | Etiqueta de nombre DNS| **mycontainerdnsxxxxx** |

    
    **Nota**: El contenedor será accesible públicamente en dns-name-label.region.azurecontainer.io. Si recibe un mensaje de error que dice **Etiqueta de nombre DNS no disponible** después de la implementación, especifique una etiqueta de nombre DNS diferente (no use xxxx) y vuelva a implementar. 

5. Haga clic en **Revisar y crear** para iniciar el proceso de validación automática.

6. Haga clic en **Crear** para crear la instancia de contenedor. 

7. Supervise la página de implementación y la de **Notificaciones**. 


# <a name="task-2-verify-deployment-of-the-container-instance"></a>Tarea 2: Comprobación de la implementación de la instancia de contenedor

En esta tarea, se comprobará que la instancia del contenedor está en ejecución, asegurándose de que se muestre la página principal.

1. Una vez completada la implementación, haga clic en el vínculo **Ir al recurso** en la hoja de implementación o el vínculo al recurso en el área de notificación.

2. En la hoja **Visión general** de **mycontainer**, asegúrese de que el **Estado** de su contenedor esté **ejecutándose**. 

3. Localice el nombre de dominio completo (FQDN).

    ![Captura de pantalla del panel de información general para el contenedor recién creado en Azure Portal, con el FQDN resaltado. ](../images/0202.png)

2. Copie el FQDN del contenedor en una nueva pestaña del explorador web y pulse **Intro**. Debería aparecer la página principal. 

    ![Captura de pantalla del mensaje de bienvenida de ACI que se muestra en un explorador web.](../images/0203.png)


**¡Enhorabuena!** Ha usado Azure Portal para implementar con éxito una aplicación en un contenedor de Azure Container Instances.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
