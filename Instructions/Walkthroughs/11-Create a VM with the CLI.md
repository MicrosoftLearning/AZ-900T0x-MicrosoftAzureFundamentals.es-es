---
wts:
    title: '11 - Crear una VM con la CLI (10 min)'
    module: 'Módulo 03: Describir las soluciones principales y las herramientas de administración'
---
# 11: Crear una VM con la CLI (10 min)

En este tutorial, configuraremos Cloud Shell, utilizaremos la CLI de Azure para crear un grupo de recursos y una máquina virtual, y revisaremos las recomendaciones de Azure Advisor. 

# Tarea 1: Configurar el Cloud Shell 

En esta tarea, configuraremos Cloud Shell y luego usaremos la CLI de Azure para crear un grupo de recursos y una máquina virtual.  

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

    ![Captura de pantalla del icono de Azure Portal Azure Cloud Shell.](../images/1002.png)
   
3. En el cuadro de diálogo Le damos la bienvenida a Azure Cloud Shell, cuando se le pida que seleccione **Bash** o **PowerShell**, seleccione **Bash**. 

4. Se abrirá una nueva ventana con el mensaje **No tiene ningún almacenamiento montado**. Seleccione **Configuración avanzada**.

5. En la pantalla Configuración avanzada, rellene los siguientes campos y luego haga clic en Crear almacenamiento:
    - Grupo de recursos: **Crear un nuevo grupo de recursos**
    - Cuenta de almacenamiento: Cree una cuenta nueva y use un nombre único a nivel global (p. ej., cloudshellalmacenamientoxyz).
    - Recurso compartido de archivos: cree uno nuevo y denomínelo recursocompartidodearchivosdecloudshell.


# Tarea 2: Utilizar la CLI para crear una máquina virtual

En esta tarea, usaremos la CLI de Azure para crear un grupo de recursos y una máquina virtual.

1. Asegúrese de que **Bash** esté seleccionado en el menú desplegable superior izquierdo del panel Cloud Shell (y si no, selecciónelo).

    ![Captura de pantalla de Azure Portal Azure Cloud Shell con el menú desplegable Bash resaltado.](../images/1002a.png)


2. Compruebe el grupo de recursos que utiliza mediante el siguiente comando:

    ```cli
    az group list --output table
    ```

4. Escriba el siguiente comando en Cloud Shell y asegúrese de que todas las líneas salvo la última van seguidas del carácter barra diagonal inversa (`\`)  Si escribe el comando completo en la misma línea, no utilice caracteres de barra diagonal inversa. 

    ```cli
    az vm create \
    --name myVMCLI \
    --resource-group myRGCLI \
    --image UbuntuLTS \
    --location EastUS2 \
    --admin-username azureuser \
    --admin-password Pa$$w0rd1234
    ```

    >**Nota**: Si utiliza la línea de comandos en un equipo Windows, reemplace el carácter de barra diagonal inversa (`\`) con el carácter de intercalación (`^`).

    **Nota**: El comando tardará entre 2 y 3 minutos en completarse. El comando creará una máquina virtual y varios recursos asociados, como recursos de seguridad, almacenamiento y redes. No continúe con el siguiente paso hasta que se complete la implementación de la máquina virtual. 

5. Cuando el comando termine de ejecutarse, en la ventana del explorador cierre el panel Cloud Shell.

6. En Azure Portal, busque **Virtual Machines** y verifique que **myVMCLI** se está ejecutando.

    ![Captura de pantalla de la página de Virtual Machines con myVMPS en estado de ejecución.](../images/1101.png)


# Tarea 3: Ejecutar comandos en Cloud Shell

En esta tarea, practicaremos la ejecución de comandos de CLI desde Cloud Shell. 

1. Desde Azure Portal, abra el **Azure Cloud Shell** haciendo clic en el icono de la esquina superior derecha de Azure Portal.

2. Asegúrese de que **Bash** esté seleccionado en el menú desplegable superior izquierdo del panel Cloud Shell.

3. Recupere información sobre la máquina virtual que aprovisionó, incluido el nombre, el grupo de recursos, la ubicación y el estado. Observe que el PowerState se está **ejecutando**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

4. Reinicie la máquina virtual. Observe el mensaje de que la facturación continúa hasta que la máquina virtual se desasigna. 

    ```cli
    az vm stop --resource-group myRGCLI --name myVMCLI
    ```

5. Compruebe el estado de su máquina virtual. El PowerState ahora debería estar **parado**.

    ```cli
    az vm show --resource-group myRGCLI --name myVMCLI --show-details --output table 
    ```

# Tarea 4: Revisar las recomendaciones de Azure Advisor

En esta tarea, revisaremos las recomendaciones de Azure Advisor.

   **Nota:** Si ha completado el laboratorio anterior (Crear una VM con PowerShell), entonces ya ha realizado esta tarea. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Advisor**. 

2. En la hoja **Advisor**, seleccione **Información general**. Las recomendaciones se agrupan por confiabilidad, seguridad, rendimiento y coste. 

    ![Captura de pantalla de la página Visión general de Advisor. ](../images/1103.png)

3. Seleccione **Todas las recomendaciones** y tómese un tiempo para ver cada recomendación y acciones sugeridas. 

    **Nota:** Dependiendo de sus recursos, sus recomendaciones serán diferentes. 

    ![Captura de pantalla de la página Todas las recomendaciones de Advisor. ](../images/1104.png)

4. Tenga en cuenta que puede descargar las recomendaciones como un archivo CSV o PDF. 

5. Tenga en cuenta que puede crear alertas. 

6. Si tiene tiempo, continúe experimentando con la CLI de Azure. 

¡Enhorabuena! Ha configurado Cloud Shell, ha creado una máquina virtual con la CLI de Azure, ha practicado con los comandos de la CLI de Azure y ha visto las recomendaciones de Advisor.

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
