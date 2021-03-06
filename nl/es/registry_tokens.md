---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-14"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Automatización del acceso a {{site.data.keyword.registrylong_notm}}
{: #registry_access}

Puede utilizar elementos de registro o una clave de API (IAM) de {{site.data.keyword.iamlong}} para automatizar el acceso a sus espacios de nombres de {{site.data.keyword.registrylong_notm}} para poder enviar por push y extraer imágenes.
{:shortdesc}

¿Está intentando utilizar las imágenes de registro en despliegues de Kubernetes? Consulte [Acceso a imágenes en otros espacios de nombres de Kubernetes, regiones de {{site.data.keyword.Bluemix_notm}} y cuentas](/docs/containers/cs_images.html#other).
{: tip}

Las claves API están enlazadas a su cuenta y pueden utilizarse en {{site.data.keyword.Bluemix_notm}} sin que necesite distintas credenciales para cada servicio. Puede utilizar la clave de API en la CLI o como parte de la automatización para iniciar sesión como su identidad de usuario.

Los elementos de registro solo abarcan {{site.data.keyword.registrylong_notm}}. Puede limitarlos a un acceso de sólo lectura y puede seleccionar si caducan o no caducan.

Si utiliza una clave de API, puede controlar el acceso a los espacios de nombres utilizando las políticas de IAM. Para obtener más información, consulte [Definición de políticas de rol de acceso de usuario](/docs/services/Registry/registry_users.html#user).

Para obtener más información acerca de las claves de API de {{site.data.keyword.registrylong_notm}}, consulte [Trabajar con claves API](/docs/iam/apikeys.html#manapikey).

Antes de empezar, [instale {{site.data.keyword.registrylong_notm}} y la CLI de Docker](registry_setup_cli_namespace.html#registry_cli_install).

## Acceso automático a sus espacios de nombres mediante el uso de claves API
{: #registry_api_key}

Puede utilizar claves API para automatizar el envío por push y la extracción de imágenes Docker a y desde los espacios de nombres.
{:shortdesc}

### Creación de una clave de API
{: #registry_api_key_create}

Puede crear un clave de API que puede utilizar para iniciar sesión en su registro.
{:shortdesc}

Puede crear tanto claves API de usuario como claves API de ID de servicio.

- Para crear una clave de API de ID de servicio, consulte [Creación de una clave de API para un ID de servicio](/docs/iam/serviceid_keys.html#creating-an-api-key-for-a-service-id).
- Para crear una clave de API de usuario, consulte [Creación de una clave de API](/docs/iam/userid_keys.html#creating-an-api-key).

### Utilización de una clave de API para automatizar el acceso
{: #registry_api_key_use}

Puede utilizar una clave de API para automatizar el acceso a sus espacios de nombres en {{site.data.keyword.registrylong_notm}}.
{:shortdesc}

Utilice la clave de API para iniciar sesión en su registro mediante la ejecución del siguiente mandato Docker. Substituya &lt;your_apikey&gt; por su clave de API, y sustituya &lt;registry_url&gt; por el URL del registro en el que está configurado sus espacios de nombres.

```
docker login -u iamapikey -p <your_apikey> <registry_url>
```
{: pre}

Para obtener información acerca del mandato, consulte [Cree una nueva clave de API de plataforma {{site.data.keyword.Bluemix_notm}}](/docs/cli/reference/ibmcloud/cli_api_policy.html#ibmcloud_iam_api_key_create).

## Automatización del acceso a sus espacios de nombres mediante señales
{: #registry_tokens}

Puede utilizar señales para automatizar el envío por push y la extracción de imágenes Docker a y desde los espacios de nombres {{site.data.keyword.registrylong_notm}}.
{:shortdesc}

Cualquiera que tenga una señal de registro puede acceder a la información protegida. Mediante la creación de una señal para su cuenta de {{site.data.keyword.Bluemix_notm}}, se puede otorgar acceso a todos los espacios de nombres que ha configurado en una región para los usuarios fuera de su cuenta de {{site.data.keyword.Bluemix_notm}}. Cada usuario o app en posesión de esta señal puede enviar por push o extraer imágenes a espacios de nombres sin tener que instalar el plug-in container-registry.

Cuando crea una señal para su cuenta de {{site.data.keyword.Bluemix_notm}}, puede decidir si dicha señal autoriza el acceso de sólo lectura (extraer) o el acceso de escritura (enviar por push y extraer) para el
registro. También puede especificar si una señal es permanente o si ésta caduca después de 24 horas. Puede crear y utilizar varias señales para controlar los diferentes tipos de acceso.

Si inicia la sesión en {{site.data.keyword.registrylong_notm}} utilizando una señal de registro, las políticas de acceso de IAM no se imponen. Si desea restringir el acceso a uno o varios espacios de nombres para un ID que se utiliza en la automatización, tenga en cuenta la posibilidad de utilizar una clave de API de ID de servicio de IAM en lugar de una señal de registro. Para obtener más información sobre cómo crear una clave de API y utilizarla con {{site.data.keyword.registrylong_notm}}, consulte [Automatización del acceso a los espacios de nombres mediante claves de API](#registry_api_key).

Utilice las siguientes tareas para gestionar sus señales:

- [Creación de una señal para su cuenta de {{site.data.keyword.Bluemix_notm}}](#registry_tokens_create)
- [Utilización de una señal para automatizar el acceso a su espacio de nombres ](#registry_tokens_use)
- [Eliminación de una señal de su cuenta de {{site.data.keyword.Bluemix_notm}}](#registry_tokens_remove)

### Creación de una señal para su cuenta de {{site.data.keyword.Bluemix_notm}}
{: #registry_tokens_create}

Puede crear una señal para otorgar acceso a todos los espacios de nombres {{site.data.keyword.registrylong_notm}} en una región.
{:shortdesc}

1. Cree una señal. En el ejemplo siguiente se crea una señal que no caduca que tiene acceso de lectura y escritura a todos los espacios de nombres que se encuentran configurados en una región.

   ```
   ibmcloud cr token-add --description "This is a token" --non-expiring --readwrite
   ```
   {: pre}

   <table>
        <thead>
        <th colspan=2><img src="images/idea.png" alt="light bulb icon"/> Descripción de los componentes de este mandato</th>
        </thead>
        <tbody>
        <tr>
        <td>`--description`</td>
        <td>Opcional. Utilice esta opción para describir la señal para que pueda identificarla más fácilmente más tarde.</td>
        </tr>
        <tr>
        <td>`--non-expiring`</td>
        <td>Opcional. Utilice esta opción para crear una señal que no caduca. Si no especifica esta opción, la señal se convierte en no válida después de 24 horas. <br> **Consejo:** Cuando ya no necesite una señal que no caduca para bloquear el acceso a los espacios de nombres, recuerde eliminar la señal.</td>
        </tr>
        <tr>
        <td>`--readwrite`</td>
        <td>Opcional. Utilice esta opción para crear una señal que permite a los usuarios enviar por push y extraer imágenes a y desde los espacios de nombres. Si no especifica esta opción, la señal se puede utilizar para extraer sólo imágenes.</td>
        </tr>
        </tbody>
   </table>

   Su salida de CLI tiene un aspecto similar a la salida siguiente:

   ```
   Token identifier   58669dd6-3ddd-5c78-99f9-ad0a5aabd9ad
   Token              <token_value>
   ```
   {: screen}

2. Verifique que la señal se ha creado.

   ```
   ibmcloud cr token-list
   ```
   {: pre}

### Utilización de una señal para automatizar el acceso a su espacio de nombres
{: #registry_tokens_use}

Puede utilizar una señal en su mandato `login docker` para automatizar el acceso a sus espacios de nombres en {{site.data.keyword.registrylong_notm}}. Dependiendo de si establece un acceso de sólo lectura o de lectura/escritura para la señal, los usuarios pueden enviar por push y extraer imágenes a y desde los espacios de nombres.
{:shortdesc}

1. Inicie una sesión en {{site.data.keyword.Bluemix_notm}}.

   ```
   ibmcloud login
   ```
   {: pre}

2. Enumere todas las señales de la cuenta de {{site.data.keyword.Bluemix_notm}} y tenga en cuenta el ID de señal que desea utilizar.

   ```
   ibmcloud cr token-list
   ```
   {: pre}

3. Recupere el valor de la señal para la señal. Sustituya &lt;id_señal&gt; con el ID de la señal.

   ```
   ibmcloud cr token-get <token_id>
   ```
   {: pre}

    Su valor de la señal se muestra en **Señal** de la salida de la CLI.

4. Utilice la señal como parte del mandato `docker login`. Sustituya &lt;valor_señal&gt; por el valor de la señal que ha recuperado en el paso anterior y &lt;url_registro&gt; por el URL en el registro donde los espacios de nombres está configurado.

   - Para espacios de nombres configurados en EE.UU. sur, utilice `registry.ng.bluemix.net`
   - Para espacios de nombres configurados en Reino Unido sur, utilice `registry.eu-gb.bluemix.net`
   - Para espacios de nombres configurados en UE central, utilice `registry.eu-de.bluemix.net`
   - Para espacios de nombres configurados en AP sur, utilice `registry.au-syd.bluemix.net`

   ```
   docker login -u token -p <token_value> <registry_url>
   ```
   {: pre}

   Para el parámetro `-u`, asegúrese de que escribe la serie `token` y no el ID de la señal.
   {: tip}

   Después de que haya iniciado una sesión en Docker utilizando la señal, puede enviar por push o extraer imágenes a y desde el espacio de nombres.

### Eliminación de una señal de su cuenta de {{site.data.keyword.Bluemix_notm}}
{: #registry_tokens_remove}

Elimine una señal de {{site.data.keyword.registrylong_notm}} cuando ya no la necesite.
{:shortdesc}

Las señales caducadas de {{site.data.keyword.registrylong_notm}} se eliminan automáticamente desde su cuenta de {{site.data.keyword.Bluemix_notm}} y no es necesario eliminarlas manualmente.
{:tip}

1. Inicie una sesión en {{site.data.keyword.Bluemix_notm}}.

   ```
   ibmcloud login
   ```
   {: pre}

2. Enumere todas las señales de la cuenta de {{site.data.keyword.Bluemix_notm}} y tenga en cuenta el ID de señal que desea eliminar.

   ```
   ibmcloud cr token-list
   ```
   {: pre}

3. Eliminar la señal.

   ```
   ibmcloud cr token-rm <token_id>
   ```
   {: pre}

## Opciones de autenticación para todos los clientes
{: #registry_authentication}

Puede autenticarse mediante el mandato `docker login` u otros clientes de registro.
{:shortdesc}

La mayoría de los usuarios pueden utilizar el mandato `ibmcloud cr login` para simplificar `docker login`, pero si está implementando la automatización o está utilizando un cliente diferente, es posible que quiera autenticarse manualmente. Debe presentar un nombre de usuario y una contraseña. En {{site.data.keyword.registrylong_notm}}, el nombre de usuario indica el tipo de secreto que se presenta en la contraseña.

Son válidos los siguientes nombres de usuarios:

- `iambearer` La contraseña contiene un señal de acceso a IAM. Este tipo de autenticación es de corta duración, pero puede derivarse de todos los tipos de identidad IAM.
- `iamrefresh` La contraseña debe contener un señal de actualización de IAM que se utiliza internamente para generar y actualizar un señal de acceso a IAM. Este tipo de autenticación es más duradero y es utilizado por el mandato `ibmcloud cr login`.
- `iamapikey` La contraseña es una clave de API de IAM. Este tipo de autenticación es el preferido para la automatización. Puede utilizar una clave de API de usuario o de ID de servicio, consulte [Creación de una clave de API](#registry_api_key_create).
- `token` La contraseña es una señal de registro. Puede utilizar este nombre de usuario para la automatización.

No es necesario utilizar el mandato `docker` para autenticarse con el registro. Por ejemplo, puede iniciar apps de Cloud Foundry desde las imágenes del registro utilizando la CLI de Cloud Foundry:

```
export CF_DOCKER_PASSWORD=<apikey>
ibmcloud cf push appname  -o registry.<region>.bluemix.net/<my_namespace>/<image_repo> --docker-username iamapikey
```
{: pre}

Sustituya _&lt;apikey&gt;_ por su clave de API, _&lt;region&gt;_ por el nombre de su [región](registry_overview.html#registry_regions), _&lt;my_namespace&gt;_ por su espacio de nombres y _&lt;image_repo&gt;_ por el repositorio.

Para obtener más información, consulte [Uso de un registro de imagen privado](/docs/services/ContinuousDelivery/pipeline_custom_docker_images.html#private_image_registry).
