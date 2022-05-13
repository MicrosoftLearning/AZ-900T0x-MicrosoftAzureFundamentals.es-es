---
wts:
  title: '01: Crear una máquina virtual en el portal (10 minutos)'
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 010d6a19a66f6ac92627720379a4eb850b2ee423
ms.sourcegitcommit: 4a0bfef63f98844f16e2a364d156e96382b8fac5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2022
ms.locfileid: "144556875"
---
# <a name="01---create-a-virtual-machine-in-the-portal-10-min"></a>01: Crear una máquina virtual en el portal (10 minutos)

En este tutorial crearemos una máquina virtual en Azure Portal, nos conectaremos a esa máquina virtual, instalaremos el rol de servidor web y la probaremos. 

**Nota**: Tómese el tiempo durante este tutorial para hacer clic y leer los iconos informativos. 

# <a name="task-1-create-the-virtual-machine"></a>Tarea 1: Creación de la máquina virtual 
1. Inicie sesión en Azure Portal: **https://portal.azure.com**

3. En la hoja **Todos los servicios** del menú Portal, busque y seleccione **Máquinas virtuales**, luego haga clic en **+Crear** y seleccione **+Máquina virtual de Azure** en el menú desplegable.

4. En la pestaña **Datos básicos**, complete la siguiente información (deje los valores predeterminados para todo lo demás):

    | Configuración | Valores |
    |  -- | -- |
    | Subscription | **Usar los valores predeterminados** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre de la máquina virtual | **myVM** |
    | Region | **(EE. UU.) Este de EE. UU.**|
    | Opciones de disponibilidad | No se necesitan opciones de redundancia de la infraestructura|
    | Imagen | **Windows Server 2019 Datacenter - Gen2**|
    | Size | **Estándar D2s v3**|
    | Nombre de usuario de la cuenta de administrador | **azureuser** |
    | Contraseña de la cuenta de administrador (escríbala cuidadosamente) | **Pa$$w0rd1234**|
    | Reglas de puerto de entrada - | **Permitir los puertos seleccionados**|
    | Selección de puertos de entrada | **RDP (3389)** y **HTTP (80)**| 

5. Vaya a la pestaña Redes para asegurarse de que **HTTP (80) y RDP (3389)** están seleccionados en la sección **Seleccionar puertos de entrada**.

6. Vaya a la pestaña Administración y, en la sección **Supervisión**, seleccione la siguiente configuración:

    | Configuración | Valores |
    | -- | -- |
    | Diagnósticos de arranque | **Deshabilitar**|

7. Deje los valores predeterminados restantes y luego haga clic en el botón **Revisar y crear** en la parte inferior de la página.

8. Una vez que supere la validación, haga clic en el botón **Crear**. La implementación de la máquina virtual puede demorar entre cinco y siete minutos.

9. Recibirá actualizaciones en la página de implementación y a través del área **Notificaciones** (el icono en forma de campana de la barra de menús superior).

# <a name="task-2-connect-to-the-virtual-machine"></a>Tarea 2: Conexión a la máquina virtual

En esta tarea nos conectaremos a nuestra nueva máquina virtual usando el RDP (el Protocolo de escritorio remoto). 

1. Haga clic en el icono en forma de campana que aparece en la barra de herramientas azul de la parte superior y seleccione "Ir al recurso" cuando la implementación se haya completado con éxito. 

    **Nota**: También puede usar el vínculo **Ir al recurso** de la página de implementación. 

2. En la hoja **Información general** de la máquina virtual, haga clic en el botón **Conectar** y seleccione **RDP** en el menú desplegable.

    ![Captura de pantalla de las propiedades de la máquina virtual con el botón Conectar resaltado.](../images/0101.png)

    **Nota**: Las siguientes instrucciones le indican cómo conectarse a su VM desde un equipo con Windows. En un equipo Mac, necesita un cliente RDP, como este cliente de escritorio remoto de Mac App Store, y en un equipo Linux, puede usar un cliente RDP de código abierto.

2. En la página **Conectarse a una máquina virtual**, mantenga las opciones predeterminadas para conectarse con la dirección IP pública a través del puerto 3389 y haga clic en **Descargar archivo RDP**. Se descargará un archivo en la parte inferior izquierda de su pantalla.

3. **Abra** el archivo RDP descargado (ubicado en la parte inferior izquierda de la máquina de su laboratorio) y haga clic en **Conectar** cuando se le pida. 

    ![Captura de pantalla de las propiedades de la máquina virtual con el botón Conectar resaltado. ](../images/0102.png)

4. En la ventana **Seguridad de Windows**, inicie sesión con las credenciales de administrador que utilizó al crear el usuario **azureuser** y la contraseña **Pa$$w0rd1234** de la máquina virtual. 

5. Es posible que reciba un certificado con una advertencia durante el proceso de inicio de sesión. Haga clic en **Sí** o cree la conexión y conéctese a la VM que ha implementado. Debería conectarse correctamente.

    ![Captura de pantalla del cuadro de diálogo de advertencia de certificado que informa al usuario de un certificado no confiable, con el botón Sí resaltado. ](../images/0104.png)

Se iniciará una nueva máquina virtual (MiVM) en su laboratorio. Cierre las ventanas del Administrador de servidores y el panel del servidor que han aparecido (haga clic en la "x" de la esquina superior derecha). Debería ver el fondo de color azul de su máquina virtual. **¡Enhorabuena!** Ha implementado una máquina virtual que ejecuta Windows Server y se ha conectado a ella. 

# <a name="task-3-install-the-web-server-role-and-test"></a>Tarea 3: Instalar el rol del servidor web y probarlo

En esta tarea, instale el rol Servidor web en el servidor de la máquina virtual que acaba de crear y asegúrese de que se mostrará la página principal predeterminada de IIS. 

1. En la máquina virtual que acaba de abrir, inicie PowerShell. Para ello, busque **PowerShell** en la barra de búsqueda y, cuando lo encuentre, haga clic con el botón derecho en **Windows PowerShell** y luego en la opción **Ejecutar como administrador**.

    ![Captura de pantalla del escritorio de la máquina virtual con el botón Inicio presionado y PowerShell seleccionado, con la opción Ejecutar como administrador resaltada.](../images/0105.png)

2. Instale la característica **Servidor web** en la máquina virtual. Para ello, ejecute el siguiente comando en PowerShell. (Pegue el comando y presione ENTRAR para que se inicie la instalación).

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. Cuando complete este paso, aparecerá un aviso que indicará **Correcto** con el valor **Verdadero**. No es necesario que reinicie la máquina virtual para completar la instalación. Cierre la conexión RDP a la máquina virtual. Para ello, haga clic en la **x** que aparece en la barra azul de la parte superior central de la máquina virtual. También puede minimizarla si hace clic en el **-** que aparece en la barra azul de la parte superior central.

    ![Captura de pantalla del símbolo del sistema de Windows PowerShell con el comando Install-WindowsFeature -name Web-Server -IncludeManagementTools completado correctamente y la salida que indica que la operación ha tenido éxito.](../images/0106.png)

4. De vuelta en el portal, navegue hasta la hoja **Información general** de MiVM y use el botón **Clic para copiar al Portapapeles** para copiar la dirección IP pública de MiVM. Abra una nueva pestaña del explorador, pegue la dirección IP pública en el cuadro de texto de URL y pulse la tecla **Entrar** para acceder a ella.

    ![Captura de pantalla del panel de propiedades de la máquina virtual de Azure Portal con la dirección IP copiada.](../images/0107.png)

5. Se abrirá la página principal predeterminada del servidor web IIS.

    ![Captura de pantalla de la página principal predeterminada del servidor web IIS a la que se accede a través de la dirección IP pública en un explorador web.](../images/0108.png)

**¡Enhorabuena!** Ha creado una nueva máquina virtual que ejecuta un servidor web accesible a través de su dirección IP pública. Si tuviera una aplicación web para hospedar, podría implementar archivos de aplicación en la máquina virtual y hospedarlos para su acceso público en la máquina virtual implementada.


**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para comprobar que la eliminación se haya completado correctamente. 
