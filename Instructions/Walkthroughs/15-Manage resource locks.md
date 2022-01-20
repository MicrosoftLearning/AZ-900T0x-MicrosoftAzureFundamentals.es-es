---
wts:
    title: '15 - Administrar bloqueos de recursos (5 min)'
    module: 'Módulo 5: Descripción de las características de identidad, gobernanza, privacidad y cumplimiento'
---
# 15: Administrar bloqueos de recursos (5 min)

En este tutorial, agregaremos un bloqueo al grupo de recursos y probaremos la eliminación del grupo de recursos. Se pueden aplicar bloqueos a una suscripción de un grupo de recursos o a recursos individuales para evitar la eliminación o modificación accidental de recursos críticos.  


# Tarea 1:  Agregar un bloqueo al grupo de recursos y probar su eliminación

En esta tarea, agregaremos un bloqueo de recursos al grupo de recursos y probaremos la eliminación del grupo de recursos. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. En Azure Portal, vaya al grupo de recursos **myRGLocks**.

3. Puede aplicar un bloqueo a una suscripción, un grupo de recursos o un recurso individual para evitar la eliminación o modificación accidental de recursos críticos. 

4. En la sección **Configuración**, haga clic en **Bloqueos** y luego en **+ Agregar**. 

    ![Captura de pantalla del grupo de recursos myRGLocks que muestra el panel Bloqueos.](../images/1601.png)

5. Configure el nuevo bloqueo. Al finalizar, haga clic en **Aceptar**. 

    | Configuración | Valor |
    | -- | -- |
    | Nombre del bloqueo | '''RGLock''' |
    | Tipo de bloqueo | **Eliminar** |
    | | |

6. Haga clic en **Información general** y en **Eliminar grupo de recursos**. Escriba el nombre del grupo de recursos y haga clic en **Aceptar**. Recibirá un mensaje de error que indica que el grupo de recursos está bloqueado y que no se puede eliminar.

    ![Captura de pantalla del error sobre el bloqueo contra la eliminación.](../images/1602.png)

# Tarea 2: Probar a eliminar un miembro del grupo de recursos

En esta tarea, probaremos si el bloqueo de recursos protege una cuenta de almacenamiento en el grupo de recursos. 

1. Desde la hoja **Todos los servicios**, busque y seleccione **Cuentas de almacenamiento** y haga clic en **+ Agregar, + Crear, o + Nuevo** 

2. En la pestaña **Cuentas de almacenamiento** de la hoja **+Agregar +Nuevo +Crear**, complete la siguiente información (reemplace **xxxx** en el nombre de la cuenta de almacenamiento con letras y dígitos de modo que el nombre sea globalmente único). Deje los valores predeterminados para todo lo demás.

    | Configuración | Valor | 
    | --- | --- |
    | Suscripción | **Seleccione su suscripción** |
    | Grupo de recursos | **myRGLocks** |
    | Nombre de la cuenta de almacenamiento | **storageaccountxxxx** |
    | Ubicación | **(EE. UU.) Este de EE. UU.**  |
    | Rendimiento | **Estándar** |
    | Tipo de cuenta | **StorageV2 (uso general v2)** |
    | Replicación | **Almacenamiento con redundancia local (LRS)** |
    | Nivel de acceso (predeterminado) | **Frecuente** |
   

3. Haga clic en **Revisar y crear** para revisar la configuración de su cuenta de almacenamiento y permitir que Azure valide la configuración. 

4. Una vez validada, haga clic en **Crear**. Espere la notificación de que la cuenta se creó correctamente. 

5.  Espere la notificación de que la cuenta de almacenamiento se creó correctamente. 

6. Acceda a su nueva cuenta de almacenamiento y, desde el panel **Información general**, haga clic en **Eliminar**. Recibirá un mensaje de error que indica que el recurso o su primario tiene un bloqueo de eliminación. 

    ![Captura de pantalla del error al eliminar la cuenta de almacenamiento.](../images/1603.png)

    **Nota**: Aunque no hayamos creado específicamente un bloqueo para la cuenta de almacenamiento, hemos creado un bloqueo en el nivel del grupo de recursos que contiene la cuenta de almacenamiento. Como tal, este bloqueo de nivel *primario* nos impide eliminar el recurso y la cuenta de almacenamiento hereda el bloqueo del nivel primario.

# Tarea 3: Quitar el bloqueo de recurso

En esta tarea quitaremos el bloqueo del recurso y lo probaremos. 

1. Vuelva a la hoja del grupo de recursos **myRGLocks-XXXXXXXX** y, en la sección **Configuración**, haga clic en **Bloqueos**.
    
2. Haga clic en el vínculo **Eliminar** de la derecha de la entrada **myRGLocks-XXXXXXXX**, a la derecha de **Editar**.

    ![Captura de pantalla del bloqueo con el vínculo Eliminar resaltado](../images/1604.png)

3. Vuelva a la hoja de la cuenta de almacenamiento y confirme que ahora puede eliminar el recurso.

¡Enhorabuena! Creó un grupo de recursos, agregó un bloqueo al grupo de recursos y probó su eliminación, probó la eliminación de un recurso en el grupo de recursos y quitó el bloqueo de un recurso. 

**Nota**: Para evitar costes adicionales, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, luego, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.
