---

copyright:
  years: 2018
lastupdated: "2018-12-03"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Gestión del acceso de usuario con Identity and Access Management
{: #iam}

El acceso a {{site.data.keyword.registrylong}} para los usuarios de su cuenta está controlado por {{site.data.keyword.IBM_notm}} {{site.data.keyword.iamshort}} (IAM).
{: shortdesc}

Cuando las políticas de IAM están habilitadas para su cuenta en {{site.data.keyword.registrylong_notm}}, a cada usuario que acceda al servicio {{site.data.keyword.registrylong_notm}} en su cuenta se le debe asignar una política de acceso con un rol de usuario de IAM definido. Esta política determina qué rol tiene el usuario dentro del contexto del servicio y qué acciones puede llevar a cabo el usuario. Cada acción de {{site.data.keyword.registrylong_notm}} se correlaciona con uno o varios [roles de usuario de IAM](/docs/iam/users_roles.html).

Las políticas de IAM solo se imponen cuando se utiliza IAM para iniciar la sesión en {{site.data.keyword.registrylong_notm}}. Si inicia una sesión en {{site.data.keyword.registrylong_notm}} utilizando otro método, como por ejemplo una señal de registro, sus políticas no se imponen. Si desea restringir el acceso a uno o varios espacios de nombres para un ID que utiliza en la automatización, tenga en cuenta la posibilidad de utilizar un ID de servicio de IAM en lugar de una señal de registro. Para obtener más información sobre los ID de servicio, consulte [Creación y trabajo con los ID de servicio](/docs/iam/serviceid.html#serviceids).

Para obtener más información sobre IAM, consulte [IBM Cloud Access y Management](/docs/iam/index.html#iamoverview).

Para obtener información sobre cómo habilitar políticas para {{site.data.keyword.registrylong_notm}}, consulte [Definición de políticas de rol de acceso de usuario](/docs/services/Registry/registry_users.html#user).

Las políticas permiten otorgar acceso en distintos niveles. Algunas de las opciones incluyen los siguientes niveles de acceso:

* Acceso al servicio en su cuenta
* Acceso a un recurso específico dentro del servicio
* Acceso a todos los servicios habilitados para IAM de su cuenta

Después de definir el ámbito de la política de acceso, asigne un rol. Consulte las tablas siguientes, en las que se describen las acciones que permite cada rol dentro del servicio {{site.data.keyword.registrylong_notm}}.

Para obtener información sobre la asignación de roles de usuario en la interfaz de usuario, consulte [Gestión del acceso de IAM](/docs/iam/mngiam.html#iammanidaccser).

Pruebe la guía de aprendizaje [Guía de aprendizaje: Concesión de acceso a los recursos de {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_tutorial_configure_iam.html#iam_access).
{: tip}

## Roles de gestión de plataforma
{: #platform_management_roles}

En la tabla siguiente se muestran acciones que se correlacionan con los roles de gestión de la plataforma. Los roles de gestión de la plataforma permiten a los usuarios realizar tareas sobre los recursos de servicio a nivel de plataforma, por ejemplo asignar acceso de usuario para el servicio y crear o suprimir ID de servicio.

| Rol de gestión de plataforma | Descripción de acciones | Acciones de ejemplo|
|:-----------------|:-----------------|:-----------------|
| Visor | No soportado | |
| Editor | No soportado | |
| Operador | No soportado | |
| Administrador | <ul><li>Configurar acceso para otros usuarios</li><li>Configurar señales de registro</li><li>Crear clústeres</li></ul> | <ul><li>Para obtener información sobre la asignación de roles de usuario en la interfaz de usuario, consulte [Gestión del acceso de IAM](/docs/iam/mngiam.html#iammanidaccser).</li><li>Añadir, listar, recuperar y eliminar señales de registro</li><li>Para crear clústeres en {{site.data.keyword.containerlong_notm}}, debe asignar el rol de Administrador para {{site.data.keyword.registrylong_notm}} al usuario; consulte [Preparación para crear clústeres](/docs/containers/cs_clusters.html#cluster_prepare).</li></ul> |
{: caption="Tabla 1. Roles de usuario y acciones de IAM" caption-side="top"}

Para {{site.data.keyword.registrylong_notm}}, existen las acciones siguientes:

| Acción| Operación sobre el servicio | Rol
|:-----------------|:-----------------|:--------------|
| `container-registry.registrytoken.create` | [`ibmcloud cr token-add`](/docs/services/Registry/registry_cli.html#bx_cr_token_add) Añadir una señal que puede utilizar para controlar el acceso a un registro. | Administrador |
| `container-registry.registrytoken.delete` | [`ibmcloud cr token-rm`](/docs/services/Registry/registry_cli.html#bx_cr_token_rm) Eliminar una o varias señales especificadas. | Administrador |
| `container-registry.registrytoken.get` | [`ibmcloud cr token-get`](/docs/services/Registry/registry_cli.html#bx_cr_token_get) Recuperar la señal especificada del registro. | Administrador |
| `container-registry.registrytoken.list` | [`ibmcloud cr token-list`](/docs/services/Registry/registry_cli.html#bx_cr_token_list) Visualizar todas las señales que existen para su cuenta de {{site.data.keyword.Bluemix_notm}}. | Administrador |
{: caption="Tabla 2. Acciones y operaciones de la plataforma para configurar {{site.data.keyword.registrylong_notm}}" caption-side="top"}

## Roles de acceso de servicio
{: #service_access_roles}

En la tabla siguiente se muestran acciones que se correlacionan con roles de acceso al servicio. Los roles de acceso al servicio permiten a los usuarios acceder a {{site.data.keyword.registrylong_notm}}, así como la posibilidad de llamar a la API de {{site.data.keyword.registrylong_notm}}.

| Rol de acceso al servicio | Descripción de acciones | Acciones de ejemplo|
|:-----------------|:-----------------|:-----------------|
| Lector | El rol Lector puede ver información. | <ul><li>Ver, inspeccionar y extraer imágenes</li><li>Ver espacios de nombres</li><li>Ver cuotas</li><li>Ver informes de vulnerabilidades</li><li>Ver firmas de imágenes</li></ul>|
| Escritor | El rol Escritor puede editar información. |<ul><li>Crear, enviar y suprimir imágenes</li><li>Ver cuotas</li><li>Firmar imágenes</li><li>Añadir y eliminar espacios de nombres</li></ul> |
| Gestor | El rol Gestor puede realizar todas las acciones. | <ul><li>Ver, inspeccionar, extraer, crear, enviar y suprimir imágenes</li><li>Ver, añadir y eliminar espacios de nombres</li><li>Ver y establecer cuotas</li><li>Ver informes de vulnerabilidades</li><li>Ver y crear firmas de imágenes</li><li>Revisar y cambiar planes de precios</li><li>Habilitar la imposición de políticas de IAM</li><li>Gestionar exenciones de Vulnerability Advisor</li></ul> |
{: caption="Tabla 3. Roles y acciones de acceso a servicio de IAM" caption-side="top"}

 Para los siguientes mandatos de {{site.data.keyword.registrylong_notm}}, debe tener al menos uno de los roles especificados que se muestran en las tablas siguientes. Para crear una política que permita el acceso a {{site.data.keyword.registrylong_notm}}, debe crear una política en la que el nombre de servicio sea `container-registry`, la instancia de servicio esté vacía y la región sea la región a la que desea otorgar acceso o bien esté vacía para dar acceso a todas las regiones.

### Roles de acceso para configurar {{site.data.keyword.registrylong_notm}}
{: #access_roles_configure}

Para otorgar a un usuario permiso para configurar su {{site.data.keyword.registrylong_notm}} en su cuenta, debe crear una política que otorgue uno o varios de los roles de la tabla siguiente. Cuando cree la política, no debe especificar un `tipo de recurso` ni un `recurso`.

**Ejemplo**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Manager>
```
{: pre}

| Acción| Operación sobre el servicio | Rol
|:-----------------|:-----------------|:--------------|
| `container-registry.auth.set` | [`ibmcloud cr iam-policies-enable`](/docs/services/Registry/registry_cli.html#bx_cr_iam_policies_enable) Habilitar la imposición de políticas de IAM. | Gestor |
| `container-registry.exemption.manager` | <ul><li>[`ibmcloud cr exemption-add`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_add) Crear una exención para un problema de seguridad.</li><li>[`ibmcloud cr exemption-list`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_list) Obtener una lista de las exenciones para problemas de seguridad.</li><li>[`ibmcloud cr exemption-rm`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_rm) Suprimir una exención para un problema de seguridad.</li><li>[`ibmcloud cr exemption-types`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_types) Obtener una lista de los tipos de problemas de seguridad que puede eximir.</li></ul> | Gestor |
| `container-registry.plan.get` | [`ibmcloud cr plan`](/docs/services/Registry/registry_cli.html#bx_cr_plan) Visualizar su plan de precios. | Gestor |
| `container-registry.plan.set` | [`ibmcloud cr plan-upgrade`](/docs/services/Registry/registry_cli.html#bx_cr_plan_upgrade) Actualizar al plan estándar. | Gestor |
| `container-registry.quota.get` | [`ibmcloud cr quota`](/docs/services/Registry/registry_cli.html#bx_cr_quota) Visualizar las cuotas actuales para tráfico y almacenamiento e información de uso relacionada con las mismas. | Lector, Escritor, Gestor |
| `container-registry.quota.set` | [`ibmcloud cr quota-set`](/docs/services/Registry/registry_cli.html#bx_cr_quota_set) Modificar la cuota especificada. | Gestor |
{: caption="Tabla 4. Acciones y operaciones de servicio para configurar {{site.data.keyword.registrylong_notm}}" caption-side="top"}

### Roles de acceso para utilizar {{site.data.keyword.registrylong_notm}}
{: #access_roles_using}

Para otorgar a un usuario permiso para acceder al contenido de {{site.data.keyword.registrylong_notm}} en su cuenta, debe crear una política que otorgue uno o varios de los roles de la tabla siguiente. Cuando crea la política, puede restringir el acceso a un espacio de nombres específico especificando el tipo de recurso `namespace` y el nombre de espacio de nombres como recurso. Si no especifica un `resource-type` y un `resource`, la política otorga acceso a todos los recursos de la cuenta.

**Ejemplo**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Reader> [--resource-type namespace --resource <namespace_name>]
```
{: pre}

| Acción | Operación sobre el servicio | Rol
|:-----------------|:-----------------|:--------------|
| `container-registry.image.build` | [`ibmcloud cr build`](/docs/services/Registry/registry_cli.html#bx_cr_build) Crear una imagen de contenedor. | Escritor, Gestor |
| `container-registry.image.delete` | [`ibmcloud cr image-rm`](/docs/services/Registry/registry_cli.html#bx_cr_image_rm) Suprimir una o varias imágenes. | Escritor, Gestor |
| `container-registry.image.inspect` | [`ibmcloud cr image-inspect`](/docs/services/Registry/registry_cli.html#bx_cr_image_inspect) Visualizar detalles sobre una imagen específica. | Lector, Gestor |
| `container-registry.image.list` | [`ibmcloud cr image-list`](/docs/services/Registry/registry_cli.html#bx_cr_image_list) Obtener una lista de las imágenes de contenedor. | Lector, Gestor |
| `container-registry.image.pull` | `docker pull` Extraer la imagen. | Lector, Escritor, Gestor |
| `container-registry.image.push` | <ul><li>`docker push` Enviar la imagen.</li><li>[`ibmcloud cr ppa-archive-load`](/docs/services/Registry/registry_cli.html#bx_cr_ppa_archive_load) Importa software de IBM que se ha descargado de [IBM Passport Advantage Online para clientes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/software/passportadvantage/pao_customer.html) y se ha empaquetado para que se utilice con Helm en el espacio de nombres del registro privado.</li></ul> | Escritor, Gestor |
| `container-registry.image.vulnerabilities` | [`ibmcloud cr vulnerability-assessment`](/docs/services/Registry/registry_cli.html#bx_cr_va) Ver un informe de evaluación de vulnerabilidades para la imagen. | Lector, Gestor |
| `container-registry.namespace.create` | [`ibmcloud cr namespace-add`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_add) Añadir un espacio de nombres. | Escritor, Gestor |
| `container-registry.namespace.delete` | [`ibmcloud cr namespace-rm`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_rm) Eliminar un espacio de nombres. | Escritor, Gestor |
| `container-registry.namespace.list` | [`ibmcloud cr namespace-list`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_list) Mostrar sus espacios de nombres. | Lector, Gestor |
| `container-registry.signature.create` | `docker trust sign` Firmar la imagen. | Escritor, Gestor |
| `container-registry.signature.delete` | `docker trust revoke` Suprimir la firma. | Escritor, Gestor |
| `container-registry.signature.get` | `docker trust inspect` Inspeccionar la firma. | Lector, Gestor |
{: caption="Tabla 5. Acciones y operaciones de servicio para utilizar {{site.data.keyword.registrylong_notm}}" caption-side="top"}
