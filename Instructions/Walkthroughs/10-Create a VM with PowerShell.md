---
wts:
  title: '10: Crear una VM con PowerShell (10 minutos)'
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: a6c6e26b535658ebb01beac8037adcb5c15dc6e8
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908245"
---
# <a name="10---create-a-vm-with-powershell-10-min"></a>10: Crear una VM con PowerShell (10 minutos)

En este tutorial, configuraremos Cloud Shell, utilizaremos el módulo Azure PowerShell para crear un grupo de recursos y una máquina virtual, y revisaremos las recomendaciones de Azure Advisor. 

# <a name="task-1-configure-the-cloud-shell"></a>Tarea 1: Configuración de Cloud Shell 

En esta tarea, configuraremos Cloud Shell. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).** Puede encontrar sus credenciales de inicio de sesión en la pestaña Recursos (justo al lado de la pestaña Instrucciones). **
2. Desde Azure Portal, abra **Azure Cloud Shell** desde Azure Portal. Para ello, haga clic en el icono de la esquina superior derecha de Azure Portal.

    ![Captura de pantalla del icono de Azure Portal Azure Cloud Shell.](../images/1002.png)

3. Cuando se le pida que seleccione **Bash** o **PowerShell**, seleccione **PowerShell**.

4. En la pantalla **No tiene ningún almacenamiento montado**, seleccione **Mostrar la configuración avanzada** y luego complete la siguiente información.

    | Configuración | Valores |
    |  -- | -- |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Cuenta de almacenamiento (cree una cuenta nueva y use un nombre único a nivel global [p. ej., almacenamientocloudshellmialmacenamiento]). | **cloudshellxxxxxxx** |
    | Recurso compartido de archivos (Crear nuevo) | **shellstorage** |

5. Seleccione **Crear almacenamiento**.

# <a name="task-2-create-a-resource-group-and-virtual-machine"></a>Tarea 2: Crear un grupo de recursos y una máquina virtual.

En esta tarea, utilizaremos PowerShell para crear un grupo de recursos y una máquina virtual.  

1. Asegúrese de que **PowerShell** esté seleccionado en el menú desplegable superior izquierdo del panel de Cloud Shell.

2. Compruebe su nuevo grupo de recursos. Para ello, ejecute el siguiente comando en la ventana de PowerShell. Pulsar **Intro** para ejecutar el comando.

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

3. Cree una máquina virtual. Para ello, pegue el siguiente comando en la ventana del terminal. 

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS"
    ```
    
4. Cuando se le pida, dé el nombre de usuario (**azureuser**) y la contraseña (**Pa$$w0rd1234**) que se configurará como la cuenta de administrador local en esas máquinas virtuales.azureadmin

5. Una vez que se haya creado la VM, cierre el panel de Cloud Shell en la sesión de PowerShell.

6. En Azure Portal, busque **Máquinas virtuales** y compruebe que **miVMPS** se esté ejecutando. Esta operación puede tardar unos minutos.

    ![Captura de pantalla de la página de Virtual Machines con myVMPS en estado de ejecución.](../images/1001.png)

7. Acceda a la nueva máquina virtual y revise las configuraciones de Descripción general y Redes para comprobar que su información se haya implementado correctamente. 

# <a name="task-3-execute-commands-in-the-cloud-shell"></a>Tarea 3: Ejecutar comandos en Cloud Shell

En esta tarea, practicaremos la ejecución de comandos de PowerShell desde Cloud Shell. 

1. Desde Azure Portal, abra **Azure Cloud Shell** desde Azure Portal. Para ello, haga clic en el icono de la esquina superior derecha de Azure Portal.

2. Asegúrese de que **PowerShell** esté seleccionado en el menú desplegable superior izquierdo del panel de Cloud Shell.

3. Recupere información sobre su máquina virtual, incluido el nombre, el grupo de recursos, la ubicación y el estado. Observe que el PowerState se está **ejecutando**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Detenga la máquina virtual con el comando siguiente. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. Cuando se le pida, confirme (Sí) a la acción. Espere a que se muestre el estado **Completado correctamente**.

6. Compruebe el estado de su máquina virtual. Ahora PowerState debería estar **desasignado**. También puede comprobar el estado de la máquina virtual en el portal. Cierre Cloud Shell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# <a name="task-4-review-azure-advisor-recommendations"></a>Tarea 4: Revisar las recomendaciones de Azure Advisor

**Nota:** Esta misma tarea se encuentra en el laboratorio Crear una VM con la CLI de Azure. 

En esta tarea, revisaremos las recomendaciones de Azure Advisor para nuestra máquina virtual. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Advisor**. 

2. En la hoja **Advisor**, seleccione **Información general**. Las recomendaciones de aviso están agrupadas por Confiabilidad, Seguridad, Rendimiento y Coste. 

    ![Captura de pantalla de la página Visión general de Advisor. ](../images/1003.png)

3. Seleccione **Todas las recomendaciones** y tómese un tiempo para ver cada recomendación y acciones sugeridas. 

    **Nota:** Dependiendo de sus recursos, sus recomendaciones serán diferentes. 

    ![Captura de pantalla de la página Todas las recomendaciones de Advisor. ](../images/1004.png)

4. Tenga en cuenta que puede descargar las recomendaciones como un archivo CSV o PDF. 

5. Tenga en cuenta que puede crear alertas. 

6. Si tiene tiempo, continúe experimentando con Azure PowerShell. 

¡Enhorabuena! Ha configurado Cloud Shell, creado una máquina virtual con PowerShell, practicado con comandos de PowerShell y visto las recomendaciones de Advisor.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
