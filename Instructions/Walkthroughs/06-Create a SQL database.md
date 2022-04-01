---
wts:
  title: '6: Crear una base de datos SQL (5 minutos)'
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 61a0e7c7b54ed7cd13a9eae427a5b41abc51cffe
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908620"
---
# <a name="06---create-a-sql-database-5-min"></a>6: Crear una base de datos SQL (5 minutos)

En este tutorial, crearemos una base de datos de SQL en Azure y luego consultaremos los datos de la base.

# <a name="task-1-create-the-database"></a>Tarea 1: Creación de la base de datos 

En esta tarea, crearemos una base de datos SQL basada en la base de datos de ejemplo AdventureWorksLT. 

1. Inicie sesión en Azure Portal en [ **https://portal.azure.com**](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Bases de datos SQL** y haga clic en **+ Agregar, + Crear, o + Nuevo**. 

3. En la pestaña **Aspectos básicos**, rellene esta información.  

    | Configuración | Value | 
    | --- | --- |
    | Subscription | **Usar los valores predeterminados** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre de la base de datos| **bd1** | 
    | Servidor | Seleccione **Crear nuevo** (se abrirá una nueva barra lateral a la derecha)|
    | Nombre de servidor | **sqlserverxxxx** (debe ser único) | 
    | Location | **(EE. UU.) Este de EE. UU.** |
    | Método de autenticación | **Use la autenticación de SQL.** |
    | Inicio de sesión del administrador del servidor | **sqluser** |
    | Contraseña | **Pa$$w0rd1234** |
    | Haga clic en  | **OK (CORRECTO)** |

   ![Captura de pantalla del panel Servidor y del panel Nuevo servidor con los campos rellenados según la tabla y los botones Revisar y crear y Aceptar resaltados.](../images/0501.png)

4. En la pestaña **Redes**, configure las siguientes opciones (deje las demás con los valores predeterminados): 

    | Configuración | Valor | 
    | --- | --- |
    | Método de conectividad | **Punto de conexión público** |    
    | Permitir que los servicios y recursos de Azure accedan a este servidor | **Sí** |
    | Agregar dirección IP del cliente actual | **No** |
    
   ![Captura de pantalla de la pestaña Redes de la hoja Crear base de datos SQL con la configuración seleccionada según la tabla y el botón Revisar y crear resaltado.](../images/0501b.png)

5. Seleccione la pestaña **Seguridad**. 

    | Configuración | Value | 
    | --- | --- |
    | Microsoft Defender para SQL| **Ahora no** |
    
6. Vaya a la pestaña **Configuración adicional**. Utilizaremos la base de datos de muestra AdventureWorksLT.

    | Configuración | Value | 
    | --- | --- |
    | Usar datos existentes | **Ejemplo** |

    ![Captura de pantalla de la pestaña Configuración adicional de la hoja Crear base de datos de SQL con la configuración seleccionada según la tabla y el botón Revisar y crear resaltado.](../images/0501c.png)

7. Haga clic en **Revisar y crear** y, a continuación, en **Crear** para implementar y aprovisionar el grupo de recursos, el servidor y la base de datos. La implementación puede tardar de 2 a 5 minutos.


# <a name="task-2-test-the-database"></a>Tarea 2: Probar la base de datos.

En esta tarea, configuraremos SQL Server y ejecutaremos una consulta SQL. 

1. Cuando la implementación se haya completado, haga clic en Ir al recurso desde la hoja de implementación. Como alternativa, busque y seleccione **Bases de datos** y luego **Bases de datos SQL** en la hoja **Todos los recursos** y asegúrese de que se haya creado la nueva base de datos. Es posible que tenga que **actualizar** la página.

    ![Captura de pantalla del servidor y la base de datos SQL que se acaban de implementar.](../images/0502.png)

2. Haga clic en la entrada **bd1**, que representa la base de datos SQL que ha creado. En la hoja bd1, haga clic en **Editor de Power Query (versión preliminar)** .

3. Inicie sesión como **sqluser** con la contraseña **Pa$$w0rd1234**.

4. No podrá iniciar sesión. Lea atentamente el error y tome nota de la dirección IP que debe permitirse a través del firewall. 

    ![Captura de pantalla de la página de inicio de sesión del Editor de consultas con el error de dirección IP.](../images/0503.png)

5. En la hoja **bd1**, haga clic en **Información general**. 

    ![Captura de pantalla de la página del servidor SQL.](../images/0504.png)

6. En la hoja **Información general** de bd1, haga clic en **Establecer el firewall del servidor**, que se encuentra en la parte superior central de la pantalla Información general.

7. Haga clic en **Agregar IP de cliente** (barra de menú superior) para agregar la dirección IP a la que hace referencia el error (es posible que se haya rellenado automáticamente por usted. En caso contrario, péguela en los campos de la dirección IP). Asegúrese de **Guardar** los cambios. 

    ![Captura de pantalla de la página de configuración del firewall del servidor SQL con la nueva regla de IP resaltada.](../images/0506.png)

8. Vuelva a su base de datos SQL (deslice la barra de alternancia de la parte inferior hacia la izquierda) y haga clic en **Editor de Power Query (versión preliminar)** . Intente volver a iniciar sesión como **sqluser** con la contraseña **Pa$$w0rd1234**. Esta vez debería poder hacerlo. Tenga en cuenta que la implementación de la nueva regla de firewall puede tardar un par de minutos. 

9. Una vez haya iniciado sesión correctamente, aparecerá el panel de consultas. Escriba la consulta siguiente en el panel del editor. 

    ```SQL
    SELECT TOP 20 pc.Name as CategoryName, p.name as ProductName
    FROM SalesLT.ProductCategory pc
    JOIN SalesLT.Product p
    ON pc.productcategoryid = p.productcategoryid;
    ```

    ![Captura de pantalla del Editor de consultas con el panel de consulta y los comandos ejecutándose correctamente.](../images/0507.png)

10. Haga clic en **Ejecutar** y revise los resultados de la consulta en el panel **Resultados**. La consulta debería ejecutarse correctamente.

    ![Captura de pantalla del panel del Editor de consultas de base de datos con el código SQL que se ha ejecutado correctamente y la salida visible en el panel de resultados.](../images/0508.png)

¡Enhorabuena! Ha creado una base de datos SQL en Azure y ha consultado con éxito los datos en esa base de datos.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
