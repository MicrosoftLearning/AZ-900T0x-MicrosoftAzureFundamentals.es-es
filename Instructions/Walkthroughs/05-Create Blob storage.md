---
wts:
  title: '5: Crear un almacenamiento de blobs (5 minutos)'
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 554a3eb1c95b354e836fe22541f00fa1eb0bc2de
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908581"
---
# <a name="05---create-blob-storage-5-min"></a>5: Crear un almacenamiento de blobs (5 minutos)

En este tutorial, crearemos una cuenta de almacenamiento y luego trabajaremos con archivos de almacenamiento de blobs.

# <a name="task-1-create-a-storage-account"></a>Tarea 1: Creación de una cuenta de almacenamiento 

En esta tarea crearemos una nueva cuenta de almacenamiento. 

1. Inicie sesión en Azure Portal en <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ Agregar, + Crear, o + Nuevo**. 

3. En la pestaña **Datos básicos** de la hoja **Crear cuenta de almacenamiento**, complete la siguiente información (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea único a nivel global). Deje los valores predeterminados para todo lo demás.

    | Configuración | Value | 
    | --- | --- |
    | Subscription | **Deje el valor predeterminado** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxxx** |
    | Location | **(EE. UU.) Este de EE. UU.**  |
    | Rendimiento | **Estándar** |
    | Redundancia | **Almacenamiento con redundancia local (LRS)** |
    
    **Nota**: Recuerde cambiar **xxxx** de modo que sea un **nombre de cuenta de almacenamiento** único.

5. Haga clic en **Revisar y crear** para revisar la configuración de su cuenta de almacenamiento y permitir que Azure valide la configuración. 

6. Una vez validada, haga clic en **Crear**. Espere la notificación de que la cuenta se creó correctamente. 

7. Desde la página de inicio, busque y seleccione **Cuentas de almacenamiento** y asegúrese de que su nueva cuenta de almacenamiento aparezca en la lista.

    ![Captura de pantalla de la cuenta de almacenamiento recién creada en Azure Portal.](../images/0401.png)

# <a name="task-2-work-with-blob-storage"></a>Tarea 2: Trabaje con almacenamiento de blobs

En esta tarea, crearemos un contenedor de blobs y subiremos un archivo de blobs. 

1. Haga clic en el nombre de la nueva cuenta de almacenamiento, desplácese hasta la sección **Almacenamiento de datos** en el menú izquierdo y luego haga clic **Containers**.

2. Haga clic en **+ Contenedor** y complete la información. Use los iconos de información para obtener más información. Cuando termine, haga clic en **Crear**.


    | Configuración | Value |
    | --- | --- |
    | Nombre | **Contenedor1**  |
    | Nivel de acceso público| **Privado (sin acceso anónimo)** |
  

    ![Captura de pantalla del contenedor de blobs recién creado en la cuenta de almacenamiento en Azure Portal.](../images/0402.png)

4. Abra una nueva ventana del explorador y busque la imagen de una flor en **Bing**. Haga clic en la imagen con el botón derecho y guárdela en su VM. 

6. Una vez vuelva a Portal, haga clic en **contenedor1** y luego seleccione **Cargar**.

5. Busque el archivo de imagen que acaba de guardar en su equipo local. Selecciónelo y, luego, seleccione Cargar.

   
6. Haga clic en la flecha **Opciones avanzadas**; deje los valores predeterminados, pero revise las opciones disponibles, y luego haga clic en **Cargar**.

    **Nota**: Puede cargar tantos blobs como quiera de esta manera. Los nuevos blobs se enumerarán dentro del contenedor.

7. Una vez que se carga el archivo, haga clic con el botón derecho en el archivo y observe las opciones que incluyen Ver/editar, Descargar, Propiedades y Eliminar. 

8. Si tiene tiempo, revise las opciones para Archivos, Tablas y Colas.

# <a name="task-3-monitor-the-storage-account"></a>Tarea 3: Supervisar la cuenta de almacenamiento

1. Regrese a la hoja de la cuenta de almacenamiento y haga clic en **Diagnosticar y resolver problemas**. 

2. Explore algunos de los problemas de almacenamiento más comunes. Tenga en cuenta que existes diferentes maneras de solucionar estos problemas.

3. En la hoja de la cuenta de almacenamiento, desplácese hacia abajo hasta la sección **Supervisión** y haga clic en **Información**. Observe que hay información sobre Fallas, Rendimiento, Disponibilidad y Capacidad. Su información será diferente.

    ![Captura de pantalla de la página Insights de la cuenta de almacenamiento.](../images/0403.PNG)

¡Enhorabuena! Creó una cuenta de almacenamiento y luego trabajó con blobs de almacenamiento.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
