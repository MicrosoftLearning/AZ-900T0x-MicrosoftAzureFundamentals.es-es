---
wts:
    title: '01 - Crear una máquina virtual en el portal (10 minutos)'
    module: 'Módulo 2: Servicios principales de Azure (Cargas de trabajo)'
---
# 01: Crear una máquina virtual en el portal (10 min)

En este tutorial crearemos una máquina virtual en Azure Portal, nos conectaremos a ella, instalaremos el rol de servidor web y la probaremos. 

**Nota**: Tómese el tiempo durante este tutorial para hacer clic y leer los iconos informativos. 

# Tarea 1: Crear la máquina virtual 
1. Inicie sesión en Azure Portal: **https://portal.azure.com**

3. En la hoja **Todos los servicios** del menú de Portal, busque y seleccione **Máquinas virtuales** y luego haga clic en **+Agregar, +Crear, +Nueva** y seleccione **+Máquina virtual** en el menú desplegable.

4. En la pestaña **Datos básicos**, complete la siguiente información (deje los valores predeterminados para todo lo demás):

    | Configuración | Valores |
    |  -- | -- |
    | Suscripción | **Utilice la suscripción predeterminada suministrada** |
    | Grupo de recursos | **Crear un nuevo grupo de recursos** |
    | Nombre de la máquina virtual | **MiVM** |
    | Región | **Este de EE. UU.**|
    | Opciones de disponibilidad | No se necesitan opciones de redundancia de la infraestructura|
    | Imagen | **Windows Server 2019 Datacenter - Gen 2**|
    | Tamaño | **Estándar D2s v3**|
    | Nombre de usuario de la cuenta de administrador | **azureuser** |
    | Contraseña de la cuenta de administrador (escríbala cuidadosamente) | **Pa$$w0rd1234**|
    | Reglas de puerto de entrada: | **Permitir los puertos seleccionados**|
    | Seleccionar puertos de entrada | **RDP (3389)** y **HTTP (80)**| 

5. Cambie a la pestaña Redes para asegurarse de que **HTTP (80) y RDP (3389)** están seleccionados en la sección **Seleccionar puertos de entrada**.

6. Vaya a la pestaña Administración y, en la sección **Supervisión**, seleccione la siguiente configuración:

    | Configuración | Valores |
    | -- | -- |
    | Diagnóstico de arranque | **Deshabilitar**|

7. Deje los valores predeterminados restantes y luego haga clic en el botón **Revisar y crear** en la parte inferior de la página.

8. Una vez que supere la validación, haga clic en el botón **Crear**. La implementación de la máquina virtual puede demorar entre cinco y siete minutos.

9. Recibirá actualizaciones en la página de implementación y a través del área **Notificaciones** (el icono en forma de campana que aparece en la barra de menús de la parte superior).

# Tarea 2: Conectarse a la máquina virtual

En esta tarea, nos conectaremos a nuestra nueva máquina virtual mediante RDP (Protocolo de escritorio remoto). 

1. Haga clic en el icono en forma de campana que aparece en la barra de herramientas azul de la parte superior y seleccione "Ir al recurso" cuando la implementación se haya completado con éxito. 

    **Nota**: También puede usar el vínculo **Ir al recurso** de la página de implementación. 

2. En la hoja **Información general** de la máquina virtual, haga clic en el botón **Conectar** y seleccione **RDP** en el menú desplegable.

    ![Captura de pantalla de las propiedades de la máquina virtual con el botón Conectar resaltado.](../images/0101.png)

    **Nota**: Las siguientes instrucciones le indican cómo conectarse a su VM desde un equipo con Windows. En un equipo Mac, necesita un cliente RDP, como este cliente de escritorio remoto de Mac App Store, y en un equipo Linux, puede usar un cliente RDP de código abierto.

2. En la página **Conectarse a una máquina virtual**, mantenga las opciones predeterminadas para conectarse con la dirección IP pública a través del puerto 3389 y seleccione **Descargar archivo RDP**. Se descargará un archivo en la parte inferior de su pantalla.

3. **Abra** el archivo RDP que se ha descargado (ubicado en la parte inferior izquierda de la máquina de su laboratorio) y haga clic en **Conectar** cuando se le pida. 

    ![Captura de pantalla de las propiedades de la máquina virtual con el botón Conectar resaltado. ](../images/0102.png)

4. En la ventana **Seguridad de Windows**, inicie sesión con las credenciales de administrador que utilizó cuando creó el nombre de usuario **azureuser** y la contraseña **Pa$$w0rd1234** de su máquina virtual. 

5. Es posible que reciba un certificado de advertencia durante el proceso de inicio de sesión. Haga clic en **Sí** para crear la conexión y conectarse a su VM implementada. Debería conectarse correctamente.

    ![Captura de pantalla del cuadro de diálogo de advertencia de certificado que informa al usuario de un certificado no confiable, con el botón Sí resaltado. ](../images/0104.png)

Se iniciará una nueva máquina virtual (MiVM) en su laboratorio. Cierre las ventanas del Administrador de servidores y el panel que han aparecido (haga clic en la "x" que se encuentra en la parte superior derecha). Debería ver el fondo azul de su máquina virtual. **¡Enhorabuena!** Ha implementado y se ha conectado a una máquina virtual que ejecuta Windows Server. 

# Tarea 3: Instalar la función del servidor web y probarla

En esta tarea, instalará el rol de servidor web en el servidor de la máquina virtual que acaba de crear y se asegurará de que se muestre la página principal predeterminada del IIS. 

1. En la máquina virtual que acaba de abrir, inicie PowerShell. Para ello, busque **PowerShell** en la barra de búsqueda y, cuando lo encuentre, haga clic con el botón derecho en **Windows PowerShell** y luego en la opción **Ejecutar como administrador**.

    ![Captura de pantalla del escritorio de la máquina virtual con el botón de inicio presionado y PowerShell seleccionado, con la opción Ejecutar como administrador resaltada.](../images/0105.png)

2. Instale la característica **Servidor web** en la máquina virtual. Para ello, ejecute el siguiente comando en PowerShell. (Pegue el comando y presione ENTRAR para que se inicie la instalación).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Cuando complete este paso, aparecerá un aviso que indicará **Correcto** con el valor **Verdadero**. No es necesario que reinicie la máquina virtual para completar la instalación. Cierre la conexión RDP a la máquina virtual. Para ello, haga clic en la **x** que aparece en la barra azul de la parte superior central de la máquina virtual. También puede minimizarla si hace clic en el **-** que aparece en la barra azul de la parte superior central.

    ![Captura de pantalla del símbolo del sistema de Windows PowerShell con el comando Install-WindowsFeature -name Web-Server -IncludeManagementTools completado correctamente y la salida que indica que fue exitoso.](../images/0106.png)

4. Una vez que haya regresado al portal, vuelva a la hoja **Información general** de MiVM y utilice el botón **Copiar al portapapeles** para copiar la dirección IP pública de MiVM y luego abra una nueva pestaña del explorador, pegue la dirección IP pública en el cuadro de texto de la URL y presione la tecla **Entrar** para navegar hasta ella.

    ![Captura de pantalla del panel de propiedades de la máquina virtual de Azure Portal con la dirección IP copiada.](../images/0107.png)

5. Se mostrará la página principal predeterminada del servidor web IIS.

    ![Captura de pantalla de la página principal predeterminada del servidor web IIS a la que se accede a través de la dirección IP pública en un explorador web.](../images/0108.png)

**¡Enhorabuena!** Ha creado una nueva máquina virtual que ejecuta un servidor web accesible a través de su dirección IP pública. Si tuviera una aplicación web para hospedar, podría implementar archivos de aplicación en la máquina virtual y hospedarlos para su acceso público en la máquina virtual implementada.


**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
