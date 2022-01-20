---
wts:
    title: '4: Crear una red virtual (20 minutos)'
    module: 'Módulo 2: Servicios principales de Azure (Cargas de trabajo)'
---
# 4: Crear una red virtual (20 minutos)

En este tutorial crearemos una red virtual, implementaremos dos máquinas virtuales en esa red virtual y luego las configuraremos para permitir que una máquina virtual haga ping a la otra dentro de esa red.

# Tarea 1: Crear una red virtual 

En esta tarea, crearemos una red virtual. 

Nota: Antes de comenzar el laboratorio, deshabilite el firewall público y privado en su máquina virtual. Para ello, seleccione el menú Inicio > Configuración > Red e Internet y busque Firewall de Windows

1. Inicie sesión en Azure Portal en <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Desde la hoja **Todos los servicios**, busque y seleccione **Redes virtuales** y haga clic en **+ Agregar, + Crear o + Nuevo**. 

3. En la pestaña **Datos básicos**, complete la siguiente información (deje los valores predeterminados para todo lo demás):

    | Configuración | Valor | 
    | --- | --- |
    | Suscripción | **Dejar los valores predeterminados** |
    | Grupo de recursos | **Crear nuevo grupo de recursos** |
    | Nombre | **vnet1** |
    | Región | **Este de EE. UU. (US)** |
    
   
4. Haga clic en el botón **Revisar y crear**. Asegúrese de que la validación sea exitosa. Luego, seleccione Crear para implementar el recurso.


# Tarea 2: Crear dos máquinas virtuales

En esta tarea crearemos dos máquinas virtuales en la red virtual. 

1. Desde la hoja **Todos los servicios** busque **Máquinas virtuales** y luego haga clic en **+ Agregar, +Crear o +Nuevo** y seleccione **Máquina virtual** en el menú desplegable. 

2. En la pestaña **Datos básicos**, complete la siguiente información (deje los valores predeterminados para todo lo demás):

   | Configuración | Valor | 
   | --- | --- |
   | Suscripción | **Usar los valores predeterminados** |
   | Grupo de recursos |  **Seleccionar el predeterminado en el menú desplegable** |
   | Nombre de la máquina virtual | **vm1**|
   | Región | **Este de EE. UU. (US)** |
   | Imagen | **Windows Server 2019 Datacenter - Gen2** |
   | Nombre de usuario| **azureuser** |
   | Contraseña| **Pa$$w0rd1234** |
   | Puertos de entrada públicos| Seleccione **Permitir puertos seleccionados**  |
   | Puertos de entrada seleccionados| **RDP (3389):** |
   

3. Seleccione la pestaña **Redes**. Asegúrese de que la máquina virtual esté ubicada en la red virtual **vnet1**. Revise la configuración predeterminada, pero no realice ningún otro cambio. 

4. Haga clic en **Revisar y crear**. Después de que la validación sea exitosa, haga clic en **Crear**. Los tiempos de implementación pueden variar, pero generalmente la implementación demora entre tres y seis minutos.

5. Supervise su implementación, pero continúe con el siguiente paso. 

6. Cree una segunda máquina virtual repitiendo los pasos anteriores del **2 al 4**. Asegúrese de usar un nombre de máquina virtual diferente, de que la máquina virtual está dentro de la misma red virtual y de que usa una nueva dirección IP pública:

    | Configuración | Valor |
    | --- | --- |
    | Grupo de recursos | **Seleccionar el valor predeterminado en la lista desplegable (igual que la Tarea 1-3 y Tarea 2-2)** |
    | Nombre de la máquina virtual |  **vm2** |
    | Red virtual | **vnet1** |
    | IP pública | **vm2-ip** |

7. Espere a que las dos máquinas virtuales se implementen y muestren el estado *En ejecución*.

# Tarea 3: Probar la conexión 

En esta tarea, probaremos si las máquinas virtuales pueden comunicarse (hacer ping) entre sí. En el caso de que no puedan, instalaremos una regla para permitir una conexión ICMP. Normalmente, las conexiones ICMP se bloquean automáticamente.

1. Desde la hoja **Todos los recursos**, busque **vm1**, abra la hoja **Información general** y asegúrese de que su **Estado** sea **En ejecución**. Es posible que necesite **Actualizar** la página.

2. En la hoja **Información general**, seleccione **Conectar** y después seleccione **RDP** en el menú desplegable.

    **Nota**: Las siguientes instrucciones le indican cómo conectarse a su VM desde un equipo con Windows. 

3. En la hoja **Conectar mediante RDP**, mantenga las opciones predeterminadas para conectarse por dirección IP a través del puerto 3389 y haga clic en **Descargar archivo RDP**.

4. Abra el archivo RDP descargado (ubicado en la parte inferior izquierda de la VM) y haga clic en **Conectar** cuando se le pida. 

5. En la ventana **Seguridad de Windows**, escriba el nombre de usuario **azureuser** y la contraseña **Pa$$w0rd1234** y luego haga clic en **Aceptar**.

6. Es posible que reciba una advertencia de certificado durante el proceso de inicio de sesión. Haga clic en **Sí** para crear la conexión y conéctese a la VM que ha implementado. Debería conectarse correctamente. Cierre las ventanas de Windows Server y las ventanas del panel de información que aparecen. Debería ver un fondo azul de Windows. Ahora se encuentra en la máquina virtual.

7. En la máquina virtual recién creada, deshabilite el firewall público y privado. Para ello, seleccione el menú Inicio > Configuración > Red e Internet y busque Firewall de Windows

8. Abra PowerShell en la máquina virtual. Para ello, haga clic en el botón **Inicio** y, en Búsqueda, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y luego seleccione **Ejecutar como administrador**.

9. En PowerShell, intente hacer ping a vm2. Para ello escriba:

   ```PowerShell
   ping vm2
   ```

 10. Debería tener éxito. Ha hecho ping a VM2 desde VM1.


**¡Enhorabuena!** Ha configurado e implementado dos máquinas virtuales en una red virtual, y luego las ha conectado.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuación, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
