---
wts:
    title: '03 - Implementación de Azure Container Instances (10 minutos)'
    module: 'Módulo 2 - Servicios principales de Azure (Cargas de trabajo)'
---

# 03: Implementar Azure Container Instances (10 min)

En este tutorial crearemos, configuraremos e implementaremos un contenedor en Azure Portal mediante Azure Container Instances (ACI). El contenedor es una aplicación web Bienvenido a ACI que muestra una página HTML estática. 

# Tarea 1: Creación de una instancia de contenedor 

En esta tarea, crearemos una nueva instancia de contenedor para la aplicación web. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. En la hoja **Todos los servicios**, busque y seleccione **Container instances** y luego haga clic en **+ Agregar, + Crear y + Nueva**. 

3. Proporcione los siguientes detalles básicos para la nueva instancia de contenedor (deje los valores predeterminados para todo lo demás): 

	| Configuración| Valor|
	|----|----|
	| Suscripción | ***Utilice la suscripción predeterminada suministrada*** |
	| Grupo de recursos | **Crear un nuevo grupo de recursos** |
	| Nombre del contenedor| **mycontainer**|
	| Región | **(EE. UU.) Este de EE. UU.** |
	| Fuente de imagen| **Docker Hub u otro registro**|
	| Tipo de imagen| **Público**|
	| Imagen| **mcr.microsoft.com/azuredocs/aci-helloworld**|
	| Tipo de sistema operativo| **Linux** |
	| Tamaño| ***Dejar en el valor predeterminado***|


4. Configure la pestaña Redes (reemplace **xxxx** con letras y dígitos de manera que el nombre sea único a nivel global). Deje el resto de la configuración con los valores predeterminados.

	| Configuración| Valor|
	|--|--|
	| Etiqueta de nombre DNS| **Micontenedordnsxxxxx** |

	
	**Nota**: Su contenedor será accesible públicamente en dns-name-label.region.azurecontainer.io. Si recibe el mensaje de error **Etiqueta de nombre DNS no disponible** después de la implementación, especifique una etiqueta de nombre DNS diferente (para ello, reemplace xxxxx) y vuelva a realizar la implementación. 

5. Haga clic en **Revisar y crear** para iniciar el proceso de validación automática.

6. Haga clic en **Crear** para crear la instancia de contenedor. 

7. Supervise la página de implementación y la de **Notificaciones**. 


# Tarea 2: Compruebe la implementación de la instancia del contenedor

En esta tarea, comprobamos que la instancia del contenedor se está ejecutando asegurándonos de que se muestre la página principal.

1. Una vez completada la implementación, haga clic en el vínculo **Ir al recurso** en la hoja de implementación o el vínculo al recurso en el área de notificación.

2. En la hoja **Visión general** de **mycontainer**, asegúrese de que el **Estado** de su contenedor esté **ejecutándose**. 

3. Localice el nombre de dominio completo (FQDN).

	![Captura de pantalla del panel de información general para el contenedor recién creado en Azure Portal, con el FQDN resaltado. ](../images/0202.png)

2. Copie el FQDN del contenedor en una nueva pestaña del explorador web y presione **Entrar**. La página principal debería aparecer. 

	![Captura de pantalla del mensaje de bienvenida de ACI que se muestra en un explorador web.](../images/0203.png)


**¡Enhorabuena!** Ha utilizado Azure Portal para implementar correctamente una aplicación en un contenedor de Azure Container Instances.

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
