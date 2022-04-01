---
wts:
  title: '17: Crear una directiva de Azure (10 minutos)'
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
ms.openlocfilehash: 2811044ec560b0ac42f49a578666ed1694feb32a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908421"
---
# <a name="17---create-an-azure-policy-10-min"></a>17: Crear una directiva de Azure (10 minutos)

En este tutorial crearemos una directiva de Azure para restringir la implementación de los recursos de Azure a una ubicación específica.

# <a name="task-1-create-a-policy-assignment"></a>Tarea 1: Crear una asignación de directiva 

En esta tarea, configuraremos la directiva de ubicación permitida y la asignaremos a nuestra suscripción. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Directiva**, bajo la sección **Creación**, haga clic en **Definiciones**.  Tómese un momento para revisar la lista de definiciones de las directivas integradas. Por ejemplo, en el menú desplegable **Categoría** seleccione solo **Calcular**. Tenga en cuenta que la definición **SKU de máquina virtual permitidas** le permite especificar un conjunto de SKU de máquinas virtuales que su organización puede implementar.

3. Vuelva a la página **Directiva**, en la sección **Creación** y haga clic en **Asignaciones**. Una asignación es una directiva que se asignó para que se lleve a cabo dentro de un ámbito específico. Por ejemplo, una definición puede estar asignada al ámbito de suscripción. 

4. Haga clic en **Asignar directiva** en la parte superior de la página **Directiva: Asignaciones**.

5. En la página **Asignar directiva**, mantenga el ámbito predeterminado.

      | Configuración | Valor | 
    | --- | --- |
    | Ámbito| **Utilizar los valores predeterminados**|
    | Definición de directiva | Haga clic en los puntos suspensivos, después busque **Ubicaciones permitidas** y luego **Seleccionar** |
    | Nombre de asignación | **Ubicaciones permitidas** |
    
    ![Captura de pantalla del panel Ámbito con los valores de campo rellenados y el botón Seleccionar resaltado. ](../images/1402.png)
6. En la pestaña **Parámetros**, seleccione **Japón Occidental**. Haga clic en **Revisar y crear** y, luego, en **Crear**.

    **Nota**: Un ámbito determina a qué recursos o agrupación de recursos se aplica la asignación de directiva. En nuestro caso, podríamos asignar esta directiva a un grupo de recursos específico. Sin embargo, elegimos asignar la directiva en el nivel de suscripción. Tenga en cuenta que los recursos se pueden excluir en función de la configuración del ámbito. Las exclusiones son opcionales.

    **Nota**: Esta definición de directiva de **Ubicaciones permitidas** especificará una ubicación en la que se deben implementar todos los recursos. Si se elige una ubicación diferente, no se permitirá la implementación. Para obtener más información, vea la página [Ejemplos de Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index).

   ![Captura de pantalla del panel Definiciones disponibles con varios campos resaltados y la opción Auditar las máquinas virtuales que no utilizan discos administrados seleccionada.](../images/1403.png)

9. La asignación de directiva de **Ubicaciones permitidas** ahora aparece en el panel **Directiva: Asignaciones** y está implementada, por lo que aplica la directiva en el nivel de ámbito que especificamos (nivel de suscripción).

# <a name="task-2-test-allowed-location-policy"></a>Tarea 2: Probar la directiva de Ubicación permitida

En esta tarea probaremos la directiva de Ubicación permitida. 

1. En Azure Portal, desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y luego haga clic en **+ Crear**.

2. Configure la cuenta de almacenamiento (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea único a nivel global). Deje los valores predeterminados para todo lo demás. 

    | Configuración | Value | 
    | --- | --- |
    | Subscription | **Usar los valores predeterminados** |
    | Grupo de recursos | **myRGPolicy** (crear nuevo) |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Location | **(EE. UU.) Este de EE. UU.** |

3. Haga clic en **Revisar y crear** y, a continuación, en **Crear**. 

4. Recibirá el mensaje **Error en la implementación** que indica que la directiva desautorizó el recurso, incluido el nombre de la directiva **Ubicaciones permitidas**.

# <a name="task-3-delete-the-policy-assignment"></a>Tarea 3: Eliminación de la asignación de directiva

En esta tarea, quitaremos la asignación y prueba de la directiva de ubicación permitida. 

Eliminaremos la asignación de directivas para asegurarnos de que no quedemos bloqueados para ningún trabajo futuro que deseemos hacer.

1. Desde la hoja **Todos los servicios**, busque y seleccione **Directiva** y luego haga clic en la directiva **Ubicaciones permitidas**.

    **Nota**: En la hoja **Directiva** puede ver el estado de cumplimiento de las diversas directivas que ha asignado.

    **Nota**: La directiva de ubicación permitida puede mostrar recursos no compatibles. Si es así, estos son recursos creados antes de la asignación de la directiva.
 
2. Haga clic en **Ubicaciones permitidas**. Se abrirá la ventana Cumplimiento de directiva de Ubicaciones permitidas.

3. Haga clic en **Eliminar asignación** en el menú superior. Confirme que desea eliminar la asignación de directiva. Para ello, haga clic en **Sí**.

   ![Captura de pantalla del elemento de menú Eliminar asignación.](../images/1407.png)

4. Trate de crear otra cuenta de almacenamiento para asegurarse de que la directiva ya no está vigente.

    **Nota**: Entre las situaciones comunes donde la directiva de **Ubicaciones permitidas** puede ser útil se incluyen las siguientes: 
    - *Seguimiento de costes*: Podría tener diferentes suscripciones para diferentes ubicaciones regionales. La directiva garantizará que todos los recursos se implementen en la región prevista para ayudar con el seguimiento de costes. 
    - *Cumplimiento de Seguridad y residencia de datos*: También podría tener requisitos de residencia de datos, crear suscripciones por cliente o carga de trabajo específica y definir que todos los recursos deban implementarse en un centro de datos particular para garantizar los requisitos de cumplimiento de seguridad y datos.

¡Enhorabuena! Ha creado una directiva de Azure para restringir la implementación de los recursos de Azure en un centro de datos particular.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
