---
wts:
    title: '14: Administrar el acceso con RBAC (5 min)'
    module: 'Módulo 05: Descripción de las características de identidad, gobernanza, privacidad y cumplimiento'
---
# 14: Administrar el acceso con RBAC (5 min)

En este tutorial, asignaremos roles de permiso a recursos y visualizaremos registros.

# Tarea 1: Ver y asignar roles

En esta tarea, asignaremos el rol de colaborador de la máquina virtual. 

1. Inicie sesión en [Azure Portal](https://portal.azure.com).

2. Desde la hoja **Todos los servicios**, busque y seleccione **Grupos de recursos** y luego haga clic en **+ Agregar, + Crear, o + Nuevo**.

3. Cree un grupo de recursos. Haga clic en **Crear** cuando haya acabado. 

    | Configuración | Valor |
    | -- | -- |
    | Suscripción | **Usar los valores predeterminados** |
    | Grupo de recursos | **miRGRBAC** |
    | Región | **Este de EE. UU. (US)** |
   

4. Para crear, use **Revisar y crear** y luego haga clic en **Crear**.

5. Use **Actualizar** en la página del grupo de recursos y haga clic en la entrada que representa el grupo de recursos recién creado.

6. Haga clic en la hoja **Control de acceso (IAM)** y luego cambie a la pestaña **Roles**. Desplácese por la gran cantidad de definiciones de rol disponibles. Use los iconos informativos para tener una idea de los permisos de cada rol. También hay información sobre el número de usuarios y grupos asignados a cada rol.
 
![imagen](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Cambie a la pestaña **Asignaciones de roles** en la hoja **miRGRBAC - Control de acceso (IAM)**, haga clic en **+ Agregar** y, luego, haga clic en **Agregar asignación de roles**. Busque el rol Colaborador de la máquina virtual y selecciónelo. Cambie a la pestaña "Miembros" y asigne acceso a los usuarios siguientes: usuario, grupo o entidad de servicio. Luego, haga clic en + Seleccionar miembros, escriba su nombre en la función de búsqueda emergente y seleccione "Seleccionar". Luego, seleccione "Revisar y asignar".

    
    ![imagen](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Nota:** El rol de colaborador de la máquina virtual le permite administrar máquinas virtuales, pero no acceder a su sistema operativo ni administrar la red virtual ni la cuenta de almacenamiento a la que estén conectadas.

  

8. Haga clic en **Actualizar** en la página de asignaciones de roles y asegúrese de que ahora esté incluido como colaborador de la máquina virtual. 

    **Nota**: Esta asignación en realidad no le concede ningún privilegio adicional, ya que su cuenta ya tiene el rol Propietario, que incluye todos los privilegios asociados al rol Colaborador.

# Tarea 2: Supervisar asignaciones de roles y quitar un rol

En esta tarea, veremos el registro de actividad para comprobar la asignación de roles y luego quitaremos el rol. 

1. En la hoja del grupo de recursos myRGRBAC, haga clic en **Registro de actividad**.

2. Haga clic en **Agregar filtro**, seleccione **Operación** y luego haga clic en **Crear asignación de roles**.

    ![Captura de pantalla de la página Registro de actividad con el filtro configurado.](../images/1503.png)

3. Compruebe que el registro de actividad muestre su asignación de roles. 

    **Nota**: ¿Sabe cómo quitar su asignación de roles?

¡Enhorabuena! Ha creado un grupo de recursos, le ha asignado un rol de acceso y ha visualizado los registros de actividad. 

**Nota**: Para evitar costes adicionales, opcionalmente, puede quitar este grupo de recursos. Busque grupos de recursos, haga clic en su grupo de recursos y, a continuación, haga clic en **Eliminar grupo de recursos**. Compruebe el nombre del grupo de recursos y luego haga clic en **Eliminar**. Supervise las **Notificaciones** para ver cómo se realiza la eliminación.

