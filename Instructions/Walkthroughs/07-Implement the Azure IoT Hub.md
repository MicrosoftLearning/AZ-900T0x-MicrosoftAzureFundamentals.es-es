---
wts:
  title: '7: Implementar Azure IoT Hub (10 minutos)'
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: c2098875e07323c84eac8a405c8a59ad70eaabcd
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908540"
---
# <a name="07---implement-an-azure-iot-hub-10-min"></a>7: Implementar Azure IoT Hub (10 minutos)

En este tutorial, configuraremos una nueva instancia de Azure IoT Hub en Azure Portal, y luego autenticaremos una conexión a un dispositivo IoT con el simulador de dispositivo Raspberry Pi en línea. Los datos y los mensajes del sensor se pasan del simulador de Raspberry Pi a su Azure IoT Hub, y puede ver las métricas para la actividad de mensajería en Azure Portal.

# <a name="task-1-create-an-iot-hub"></a>Tarea 1: Creación de un centro de IoT 

En esta tarea, crearemos una instancia de IoT Hub. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Centro de IoT** y luego haga clic en **+ Agregar, + Crear, o + Nuevo**.

3. En la pestaña **Datos básicos** de la hoja **Centro de IoT**, complete los campos con los siguientes detalles (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea único a nivel global):

    | Configuración | Value |
    |--|--|
    | Subscription | **Mantener los valores predeterminados** |
    | Grupo de recursos | **Crear un grupo de recursos** |
    | Nombre de la instancia de IoT Hub | **my-hub-groupxxxxx** |
    | Region | **Este de EE. UU.** |

    **Nota**: Recuerde cambiar **xxxxx** de modo que sea un **nombre de IoT Hub** único.

4. Vaya a la pestaña **Administración** y use el menú desplegable para configurar **Nivel de precios y de escala** en **S1: Nivel estándar**.

5. Haga clic en el botón **Revisar y Crear**.

6. Haga clic en el botón **Crear** para comenzar a crear su nueva instancia de Azure IoT Hub.

7. Espere hasta que se implemente la instancia de Azure IoT Hub. 

# <a name="task-2-add-an-iot-device"></a>Tarea 2: Agregar un dispositivo de IoT

En esta tarea, agregaremos un dispositivo IoT al centro de IoT. 

1. Cuando la implementación se haya completado, haga clic en **Ir al recurso** desde la hoja de implementación. Si no, desde la hoja **Todos los servicios**, busque y seleccione **Centro de IoT** y ubique su nueva instancia de centro de IoT.

    ![Captura de pantalla de la implementación en curso y notificaciones de implementación exitosa en Azure Portal.](../images/0601.png)

2. Para agregar un nuevo dispositivo de IoT, desplácese hacia abajo hasta la sección **Administración de dispositivos** y haga clic en **Dispositivos**. A continuación, haga clic en **+ Agregar dispositivo**.

    ![Captura de pantalla del panel de dispositivos IoT, resaltado dentro de la hoja de navegación del centro IoT, en Azure Portal. El botón Nuevo se resalta para ilustrar cómo agregar una nueva identidad del dispositivo IoT al centro de IoT.](../images/0602.png)

3. Proporcione un nombre para su nuevo dispositivo IoT, **myRaspberryPi**, y haga clic en el botón **Guardar**. Esto creará una nueva identidad del dispositivo IoT en su Azure IoT Hub.

4. Si no ve su nuevo dispositivo, **actualice** la página de dispositivos IoT. 

5. Seleccione **myRaspberryPi** y copie el valor **Cadena de conexión primaria**. Utilizará esta clave en la siguiente tarea para autenticar una conexión al simulador de Raspberry Pi.

    ![Captura de pantalla de la página Cadena de conexión primaria con el icono de copia resaltado.](../images/0603.png)

# <a name="task-3-test-the-device-using-a-raspberry-pi-simulator"></a>Tarea 3: Probar el dispositivo con el simulador de Raspberry Pi

En esta tarea probaremos nuestro dispositivo con el simulador de Raspberry Pi. 

1. Abra una nueva pestaña en el explorador web y escriba este vínculo de acceso directo https://aka.ms/RaspPi. Le dirigirá al sitio de un simulador de Raspberry Pi. Si tiene tiempo, infórmese sobre el simulador de Raspberry Pi. Cuando haya terminado, seleccione la "**X**" para cerrar la ventana emergente.

2. En el área de código, en el lado derecho, ubique la línea con 'const connectionString ='. Reemplácela por la cadena de conexión que copió de Azure Portal. Tenga en cuenta que la cadena de conexión incluye las entradas DeviceId (**myRaspberryPi**) y SharedAccessKey.

    ![Captura de pantalla del área de codificación dentro del simulador de Raspberry Pi.](../images/0604.png)

3. Haga clic en **Ejecutar** (debajo del área de código) para ejecutar la aplicación. La salida de la consola debe mostrar los datos y mensajes del sensor que se envían desde el simulador de Raspberry Pi a su Azure IoT Hub. Los datos y mensajes se envían cada vez que parpadea el LED del simulador Raspberry Pi. 

    ![Captura de pantalla de la consola del simulador Raspberry Pi.  La salida de la consola muestra los datos y mensajes del sensor enviados desde el simulador de Raspberry Pi a Azure IoT Hub.](../images/0605.png)

5. Haga clic en **Detener** para dejar de enviar datos.

6. Vuelva a Azure Portal.

7. Vaya a la hoja **Información general** del centro de IoT y desplácese hacia abajo hasta la información de **Uso de IoT Hub** para visualizar el uso. Cambie el período de tiempo en **Mostrar datos del último período de** para ver los datos de la última hora.

    ![Captura de pantalla de las métricas dentro del área Uso de IoT Hub de Azure Portal.](../images/0606.png)


¡Enhorabuena! Ha configurado Azure IoT Hub para recopilar datos del sensor de un dispositivo IoT.

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
