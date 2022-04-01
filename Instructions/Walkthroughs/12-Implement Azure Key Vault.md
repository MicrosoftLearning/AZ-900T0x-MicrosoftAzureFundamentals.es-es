---
wts:
  title: '12: Implementar Azure Key Vault (5 minutos)'
  module: 'Module 04: Describe general security and network security features'
ms.openlocfilehash: 1381900fc934ddbc092faf42f0b0a366364a9872
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908237"
---
# <a name="12---implement-azure-key-vault-5-min"></a>12: Implementar Azure Key Vault (5 minutos)

En este tutorial, crearemos una instancia de Azure Key Vault y luego crearemos un secreto de contraseña en el almacén de claves, lo que le dará una contraseña almacenada de forma segura y administrada de manera centralizada para su uso con aplicaciones.

# <a name="task-1-create-an-azure-key-vault"></a>Tarea 1: Crear una instancia de Azure Key Vault 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Almacenes de claves** y, luego, seleccione **+Agregar, +Nuevo o +Crear **.

3. Configure el almacén de claves (reemplace **xxxx** en el nombre del almacén de claves con letras y dígitos de manera que el nombre sea único a nivel global). Deje los valores predeterminados para todo lo demás.

    | Configuración | Value | 
    | --- | --- |
    | Subscription | **Usar los valores predeterminados** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre del almacén de claves | **keyvaulttestxxx** |
    | Location | **Este de EE. UU.** |
    | Plan de tarifa | **Estándar** |
    
    **Nota**: Reemplace **xxxx** para idear un nombre único.
4. Haga clic en **Revisar y crear** y después en **Crear**. 

5. Una vez que se aprovisione el nuevo almacén de claves, haga clic en **Ir al recurso**. O puede localizar su nuevo almacén de claves buscándolo. 

6. Haga clic en la pestaña **Información general** del almacén de claves y tome nota del **URI del almacén**. Las aplicaciones que usan su almacén a través de la API de REST necesitarán este URI.

7. Tómese un momento para examinar algunas de las otras opciones del almacén de claves. En **Configuración**, revise **Claves**, **Secretos**, **Certificados**, **Directivas de acceso**, **Firewall y redes virtuales**.

    **Nota**: Su cuenta de Azure es la única autorizada para realizar operaciones en este nuevo almacén. Puede modificar esto si lo desea en **Configuración** y, luego, en la sección **Directivas de acceso**.

# <a name="task-2-add-a-secret-to-the-key-vault"></a>Tarea 2: Agregar un secreto al almacén de claves
        
En esta tarea agregaremos una contraseña al almacén de claves. 

1. En **Configuración**, haga clic en **Secretos**, luego haga clic **+ Generar/Importar**.

2. Configure el secreto. Deje los otros valores en sus valores predeterminados. Tenga en cuenta que puede establecer una fecha de expiración y activación. Tenga en cuenta que también puede deshabilitar el secreto.

    | Configuración | Value | 
    | --- | --- |
    | Opciones de carga | **Manual** |
    | Nombre | **Contraseña de ejemplo** |
    | Value | **hVFkk96** |

3. Haga clic en **Crear**.

4. Una vez que el secreto se haya creado con éxito, haga clic en el **Contraseña de ejemplo** y tenga en cuenta que tiene el estado de **Habilitado**

5. Seleccione el secreto que acaba de crear y anote el **Identificador secreto**. Este es el valor de URL que puede usar a partir de ahora con las aplicaciones. Proporciona una contraseña centralmente administrada y almacenada de forma segura. 

6. Haga clic en el botón **Mostrar valor secreto**, para mostrar la contraseña que especificó anteriormente.


¡Enhorabuena! Ha creado un Azure Key Vault y, luego, un secreto de contraseña en ese almacén de claves, lo que le proporciona una contraseña almacenada de forma segura y administrada centralmente para su uso con aplicaciones.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
