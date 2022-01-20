---
wts:
    title: '10 - Crear una VM con PowerShell (10 minutos)'
    module: 'Módulo 03: Describir las soluciones principales y las herramientas de administración'
---
# 10: Crear una VM con PowerShell (10 min)

En este tutorial, configuraremos Cloud Shell, utilizaremos el módulo Azure PowerShell para crear un grupo de recursos y una máquina virtual, y revisaremos las recomendaciones de Azure Advisor. 

# Tarea 1: Configurar el Cloud Shell 

En esta tarea, configuraremos Cloud Shell. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com). **Puede encontrar sus credenciales de inicio de sesión en la pestaña Recursos (justo al lado de la pestaña Instrucciones).**
2. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

    ![Captura de pantalla del icono de Azure Portal Azure Cloud Shell.](../images/1002.png)

3. Cuando se le pida que seleccione **Bash** o **PowerShell**, seleccione **PowerShell**.

4. En la pantalla **No tiene ningún almacenamiento montado**, seleccione **Mostrar la configuración avanzada** y luego rellene la siguiente información.

    | Configuración | Valores |
    |  -- | -- |
    | Grupo de recursos | **Crear un nuevo grupo de recursos** |
    | Cuenta de almacenamiento (Cree una nueva cuenta y utilice un nombre único a nivel global (p. ej., mialmacenamientodecloudshell) | **cloudshellxxxxxxx** |
    | Recurso compartido de archivos (crear nuevo) | **almacenamientodeshell** |

5. Seleccione **Crear almacenamiento**.

# Tarea 2: Crear un grupo de recursos y una máquina virtual.

En esta tarea, utilizaremos PowerShell para crear un grupo de recursos y una máquina virtual.  

1. Asegúrese de que **PowerShell** esté seleccionado en el menú desplegable superior izquierdo del panel Cloud Shell.

2. Compruebe su nuevo grupo de recursos. Para ello, ejecute el siguiente comando en la ventana de Powershell. Presione **Entrar** para ejecutar el comando.

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
    
4. Cuando se le pida, proporcione el nombre de usuario (**azureuser**) y la contraseña (**Pa$$w0rd1234**) que se configurarán como la cuenta de administrador local en la máquina virtual Azureadmin.

5. Una vez que la VM se haya creado, cierre el panel de Cloud Shell en la sesión de PowerShell.

6. En Azure Portal, busque **Virtual Machines** y verifique que **myVMPS** se esté ejecutando. Este proceso puede durar unos minutos.

    ![Captura de pantalla de la página de Virtual Machines con myVMPS en estado de ejecución.](../images/1001.png)

7. Acceda a la nueva máquina virtual y revise las configuraciones de Descripción general y Redes para comprobar que su información se haya implementado correctamente. 

# Tarea 3: Ejecutar comandos en Cloud Shell

En esta tarea, practicaremos la ejecución de comandos de PowerShell desde Cloud Shell. 

1. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

2. Asegúrese de que **PowerShell** esté seleccionado en el menú desplegable superior izquierdo del panel Cloud Shell.

3. Recupere información sobre su máquina virtual, incluido el nombre, el grupo de recursos, la ubicación y el estado. Observe que el PowerState se está **ejecutando**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

4. Detenga la máquina virtual mediante el siguiente comando. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```
5. Cuando se le solicite, confirme (Sí) a la acción. Espere hasta que aparezca el estado **Operación correcta**.

6. Compruebe el estado de su máquina virtual. Ahora PowerState debería estar **desasignado**. También puede comprobar el estado de la máquina virtual en el portal. Cierre Cloud Shell.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# Tarea 4: Revisar las recomendaciones de Azure Advisor

**Nota:** Esta misma tarea se encuentra en el laboratorio Crear una VM con la CLI de Azure. 

En esta tarea, revisaremos las recomendaciones de Azure Advisor para nuestra máquina virtual. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Advisor**. 

2. En la hoja **Advisor**, seleccione **Información general**. Las recomendaciones se agrupan por confiabilidad, seguridad, rendimiento y coste. 

    ![Captura de pantalla de la página Visión general de Advisor. ](../images/1003.png)

3. Seleccione **Todas las recomendaciones** y tómese un tiempo para ver cada recomendación y acciones sugeridas. 

    **Nota:** Dependiendo de sus recursos, sus recomendaciones serán diferentes. 

    ![Captura de pantalla de la página Todas las recomendaciones de Advisor. ](../images/1004.png)

4. Tenga en cuenta que puede descargar las recomendaciones como un archivo CSV o PDF. 

5. Tenga en cuenta que puede crear alertas. 

6. Si tiene tiempo, continúe experimentando con Azure PowerShell. 

¡Enhorabuena! Ha configurado Cloud Shell, creado una máquina virtual con PowerShell, practicado con comandos de PowerShell y visto las recomendaciones de Advisor.

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
