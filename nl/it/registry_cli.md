---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# {{site.data.keyword.registrylong_notm}} CLI
{: #containerregcli}

Puoi utilizzare la CLI {{site.data.keyword.registrylong}}, che è fornita nel plug-in container-registry, per gestire il tuo registro e le relative risorse per il tuo account {{site.data.keyword.Bluemix_notm}}.
{: shortdesc}

**Prerequisiti**

* Installa la [CLI {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/cli/index.html#overview). Il prefisso per l'esecuzione dei comandi utilizzando la CLI {{site.data.keyword.Bluemix_notm}} è `ibmcloud`.

* Prima di eseguire i comandi del registro, effettua l'accesso a {{site.data.keyword.Bluemix_notm}}
 con il comando `ibmcloud login` per generare un token di accesso e autenticare la tua sessione.

Nella riga di comando, vieni avvisato quando sono disponibili gli aggiornamenti ai plugin e alla CLI `ibmcloud`. Assicurati di mantenere la CLI aggiornata in modo da poter utilizzare tutti i comandi e gli indicatori disponibili.

Se desideri visualizzare la versione corrente del tuo plugin CLI {{site.data.keyword.registrylong}} (`container-registry`), esegui `ibmcloud plugin list`.

Per informazioni su come utilizzare la CLI {{site.data.keyword.registrylong_notm}}, vedi [Introduzione a {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/index.html#index).

Per ulteriori informazioni sui ruoli della piattaforma IAM e di accesso al servizio necessari per alcuni comandi, consulta [Gestione dell'accesso utente con Identity and Access Management (IAM)](/docs/services/Registry/iam.html#iam).

Non inserire informazioni personali nelle immagini del contenitore, nei nomi degli spazi dei nomi, nei campi di descrizione (ad esempio, nei token di registro) o in qualsiasi dato di configurazione dell'immagine (ad esempio, nomi o etichette dell'immagine).
{:tip}

<table summary="Gestisci {{site.data.keyword.registrylong_notm}}">
<caption>Tabella 1. Comandi per la gestione di {{site.data.keyword.registrylong_notm}}
</caption>
 <thead>
 <th colspan="5">Comandi per la gestione del registro</th>
 </thead>
 <tbody>
 <tr>
 <td>[`ibmcloud cr api
](#bx_cr_api)</td>
 <td>[`ibmcloud cr build`](#bx_cr_build)</td>
 <td>[`ibmcloud cr exemption-add`](#bx_cr_exemption_add)</td>
 <td>[`ibmcloud cr exemption-list` (`ibmcloud cr exemptions`)](#bx_cr_exemption_list)</td>
 <td>[`ibmcloud cr exemption-rm`](#bx_cr_exemption_rm)</td>
 </tr>
 <tr>
 <td>[`ibmcloud cr exemption-types`](#bx_cr_exemption_types)</td>
 <td>[`ibmcloud cr iam-policies-enable`](#bx_cr_iam_policies_enable)</td>
 <td>[`ibmcloud cr image-inspect`](#bx_cr_image_inspect)</td>
 <td>[`ibmcloud cr image-list` (`ibmcloud cr images`)](#bx_cr_image_list)</td>
 <td>[`ibmcloud cr image-rm`](#bx_cr_image_rm)</td>
 </tr>
 <tr>

 <td>[`ibmcloud cr info
](#bx_cr_info)</td>
 <td>[`ibmcloud cr login
](#bx_cr_login)</td>
 <td>[`ibmcloud cr namespace-add`](#bx_cr_namespace_add)</td>
 <td>[`ibmcloud cr namespace-list` (`ibmcloud cr namespaces`)](#bx_cr_namespace_list)</td>
 <td>[`ibmcloud cr namespace-rm`](#bx_cr_namespace_rm)</td>
 </tr>
 <tr>
 <td>[`ibmcloud cr plan`](#bx_cr_plan)</td>
 <td>[`ibmcloud cr plan-upgrade`](#bx_cr_plan_upgrade)</td>
 <td>[`ibmcloud cr ppa-archive-load`](#bx_cr_ppa_archive_load)</td>
 <td>[`ibmcloud cr quota`](#bx_cr_quota)</td>
 <td>[`ibmcloud cr quota-set`](#bx_cr_quota_set)</td>
 </tr>
 <tr>
 <td>[`ibmcloud cr region
](#bx_cr_region)</td>
 <td>[`ibmcloud cr region-set`](#bx_cr_region_set)</td>
 <td>[`ibmcloud cr token-add`](#bx_cr_token_add)</td>
 <td>[`ibmcloud cr token-get`](#bx_cr_token_get)</td>
 <td>[`ibmcloud cr token-list` (`ibmcloud cr tokens`)](#bx_cr_token_list)</td>
 </tr>
 <tr>
 <td>[`ibmcloud cr token-rm`](#bx_cr_token_rm)</td>
 <td>[`ibmcloud cr vulnerability-assessment` (`ibmcloud cr va`)](#bx_cr_va)</td>
 </tr>
 </tbody></table>

## `ibmcloud cr api
`
{: #bx_cr_api}

Restituisce i dettagli sull'endpoint API del registro in cui vengono eseguiti i comandi.

```
ibmcloud cr api
```
{: codeblock}

**Prerequisiti**

Nessun valore

## `ibmcloud cr build`
{: #bx_cr_build}

Crea un'immagine Docker in {{site.data.keyword.registrylong_notm}}.

```
ibmcloud cr build [--no-cache] [--pull] [--quiet | -q] [--build-arg CHIAVE=VALORE ...] [--file FILE | -f FILE] --tag DIRECTORY TAG
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`DIRECTORY`</dt>
<dd>L'ubicazione del tuo contesto di build, che contiene i tuoi file Dockerfile e prerequisiti. Se esegui il comando quando la tua directory di lavoro è impostata sulla posizione in cui è memorizzato il contesto di build, puoi sostituire `DIRECTORY` con un punto (.).</dd>
<dt>`--no-cache`</dt>
<dd>(Facoltativo)  Se specificato, i livelli di immagine memorizzati in cache dalle build precedenti non vengono utilizzati in questa build.</dd>
<dt>`--pull`</dt>
<dd>(Facoltativo) Se specificato, le immagini di base vengono estratte anche se sull'host di build esiste già un'immagine con una tag corrispondente.</dd>
<dt>`--quiet`, `-q`</dt>
<dd>(Facoltativo) Se specificato, l'output di build viene eliminato a meno che non si verifichi un errore.</dd>
<dt>`--build-arg CHIAVE=VALORE`</dt>
<dd>(Facoltativo) Specifica un argomento di build aggiuntivo nel formato `'CHIAVE=VALORE'`. È possibile specificare più argomenti di build includendo questo parametro più volte. Il valore di ogni argomento di build è disponibile come variabile di ambiente quando specifichi una riga ARG che corrisponde alla chiave nel tuo Dockerfile.</dd>
<dt>`--file FILE`, `-f FILE`</dt>
<dd>(Facoltativo) Se utilizzi gli stessi file per più build, puoi scegliere un percorso di un Dockerfile diverso. Specifica la posizione del Dockerfile in relazione al contesto di build. Se non specificato, il valore predefinito è `PATH/Dockerfile`, dove PATH è la root del contesto di build.</dd>
<dt>`--tag TAG`, `-t TAG`</dt>
<dd>Il nome completo dell'immagine che desideri creare, che include lo spazio dei nomi e l'URL del registro.</dd>
</dl>

**Esempio**

Crea un'immagine Docker che non utilizza una cache di compilazione da compilazioni precedenti, dove l'output di compilazione è soppresso, la tag è *`registry.ng.bluemix.net/bluebird/bird:1`* e la directory è la tua directory di lavoro.

```
ibmcloud cr build --no-cache --quiet --tag registry.ng.bluemix.net/bluebird/bird:1 .
```
{: pre}

## `ibmcloud cr exemption-add`
{: #bx_cr_exemption_add}

Crea un'esenzione per un problema di sicurezza. Puoi creare un'esenzione per un problema di sicurezza che si applica a diversi ambiti. L'ambito può essere l'account, lo spazio dei nomi, il repository o una tag.

```
ibmcloud cr exemption-add --scope AMBITO --issue-type TIPO_PROBLEMA --issue-id ID_PROBLEMA
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--scope AMBITO`</dt>
<dd>Per impostare il tuo account come ambito, utilizza `"*"` come valore. Per impostare uno spazio dei nomi, un repository o una tag come ambito, immetti il valore in uno dei seguenti formati: `namespace`, `namespace/repository`, `namespace/repository:tag`
</dd>
<dt>`--issue-type TIPO_PROBLEMA`</dt>
<dd>Il tipo di problema di sicurezza che vuoi esentare. Per trovare i tipi di problema validi, esegui `ibmcloud cr exemption-types`.
</dd>
<dt>`--issue-id ID_PROBLEMA`</dt>
<dd>L'ID del problema di sicurezza che vuoi esentare. Per trovare un ID problema, esegui `ibmcloud cr va <image>`, dove *&lt;image&gt;* è il nome della tua immagine, e usa il valore pertinente dalla colonna **Vulnerability ID** o **Configuration Issue ID**.
</dd>
</dl>

**Esempi**

Crea un'esenzione CVE per CVE con ID `CVE-2018-17929` per tutte le immagini nel repository `registry.ng.bluemix.net/bluebird/bird`.

```
ibmcloud cr exemption-add --scope registry.ng.bluemix.net/bluebird/bird --issue-type cve --issue-id CVE-2018-17929
```
{: pre}

Crea un'esenzione CVE al livello dell'account per CVE con ID `CVE-2018-17929`.

```
ibmcloud cr exemption-add --scope "*" --issue-type cve --issue-id CVE-2018-17929
```
{: pre}

Crea un'esenzione del problema di configurazione per il problema `application_configuration:nginx.ssl_protocols` per una sola immagine con la tag `registry.ng.bluemix.net/bluebird/bird:1`.

```
ibmcloud cr exemption-add --scope registry.ng.bluemix.net/bluebird/bird:1 --issue-type configuration --issue-id application_configuration:nginx.ssl_protocols
```
{: pre}

## `ibmcloud cr exemption-list` (`ibmcloud cr exemptions`)
{: #bx_cr_exemption_list}

Elenca le tue esenzioni per i problemi di sicurezza.

```
ibmcloud cr exemption-list [--scope AMBITO]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--scope AMBITO`</dt>
<dd>(Facoltativo) Elenca solo le esenzioni che si applicano a questo ambito. Per impostare uno spazio dei nomi, un repository o una tag come ambito, immetti il valore in uno dei seguenti formati: `namespace`, `namespace/repository`, `namespace/repository:tag`
</dd>
</dl>

**Esempio**

Elenca tutte le tue esenzioni per i problemi di sicurezza che si applicano alle immagini nel repository *`bluebird/bird`*. L'output include le esenzioni al livello dell'account, le esenzioni associate allo spazio dei nomi *`bluebird`* e le esenzioni associate al repository *`bluebird/bird`* ma senza alcuna tag specifica associata all'interno del repository *`bluebird/bird`*.

```
ibmcloud cr exemption-list --scope bluebird/bird
```
{: pre}

## `ibmcloud cr exemption-rm`
{: #bx_cr_exemption_rm}

Elimina un'esenzione per un problema di sicurezza. Per visualizzare le tue esenzioni esistenti, esegui `ibmcloud cr exemption-list`.

```
ibmcloud cr exemption-rm --scope AMBITO --issue-type TIPO_PROBLEMA --issue-id ID_PROBLEMA
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--scope AMBITO`</dt>
<dd>Per impostare il tuo account come ambito, utilizza `"*"` come valore. Per impostare uno spazio dei nomi, un repository o una tag come ambito, immetti il valore in uno dei seguenti formati: `namespace`, `namespace/repository`, `namespace/repository:tag`
</dd>
<dt>`--issue-type TIPO_PROBLEMA`</dt>
<dd>Il tipo di problema dell'esenzione per il problema di sicurezza che vuoi rimuovere. Per trovare i tipi di problema per le tue esenzioni, esegui `ibmcloud cr exemption-list`.
</dd>
<dt>`--issue-id ID_PROBLEMA`</dt>
<dd>L'ID dell'esenzione per il problema di sicurezza che vuoi rimuovere. Per trovare gli ID sicurezza per le tue esenzioni, esegui `ibmcloud cr exemption-list`.
</dd>
</dl>

**Esempi**

Elimina un'esenzione CVE per CVE con ID `CVE-2018-17929` per tutte le immagini nel repository `registry.ng.bluemix.net/bluebird/bird`.

```
ibmcloud cr exemption-rm --scope registry.ng.bluemix.net/bluebird/bird --issue-type cve --issue-id CVE-2018-17929
```
{: pre}

Elimina un'esenzione CVE al livello dell'account per CVE con ID `CVE-2018-17929`.

```
ibmcloud cr exemption-rm --scope "*" --issue-type cve --issue-id CVE-2018-17929
```
{: pre}

Elimina un'esenzione del problema di configurazione per il problema `application_configuration:nginx.ssl_protocols` per una sola immagine con la tag `registry.ng.bluemix.net/bluebird/bird:1`.

```
ibmcloud cr exemption-rm --scope registry.ng.bluemix.net/bluebird/bird:1 --issue-type configuration --issue-id application_configuration:nginx.ssl_protocols
```
{: pre}

## `ibmcloud cr exemption-types`
{: #bx_cr_exemption_types}

Elenca i tipi di problemi di sicurezza che puoi esentare.

```
ibmcloud cr exemption-types
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

## `ibmcloud cr iam-policies-enable`
{: #bx_cr_iam_policies_enable}

Se stai utilizzando l'autenticazione IAM, questo comando abilita l'autorizzazione dettagliata. Per ulteriori informazioni, consulta [Gestione dell'accesso utente con Identity and Access Management (IAM)](/docs/services/Registry/iam.html#iam) e [Definizione delle politiche del ruolo di accesso utente](/docs/services/Registry/registry_users.html#user).

```
ibmcloud cr iam-policies-enable
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

## `ibmcloud cr image-inspect`
{: #bx_cr_image_inspect}

Visualizza i dettagli di una specifica immagine.

```
ibmcloud cr image-inspect [--format FORMATO] IMMAGINE [IMMAGINE...]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Lettore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--format FORMATO`</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un template Go.

Per ulteriori informazioni, vedi [Formattazione e filtro dell'output della CLI per i comandi {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>`IMMAGINE`</dt>
<dd>Il nome dell'immagine per cui vuoi ottenere un report. Puoi analizzare più immagini elencando ogni immagine nel comando con uno spazio tra ciascun nome.

<p>Per trovare i nomi delle tue immagini, esegui `ibmcloud cr image-list`. Combina il contenuto delle colonne **Repository** e **Tag** per creare il nome dell'immagine nel formato `repository:tag`. Se nel nome immagine non è specificata alcuna tag, viene analizzata l'immagine contrassegnata con la tag `latest`. </p>

</dd>
</dl>

**Esempio**

Visualizza i dettagli sulle porte esposte per l'immagine *`registry.ng.bluemix.net/bluebird/bird:1`*, utilizzando la direttiva di formattazione *`"{{ .Config.ExposedPorts }}"`*.

```
ibmcloud cr image-inspect  --format "{{ .Config.ExposedPorts }}" registry.ng.bluemix.net/bluebird/bird:1
```
{: pre}

## `ibmcloud cr image-list` (`ibmcloud cr images`)
{: #bx_cr_image_list}

Visualizza tutte le immagini nel tuo account {{site.data.keyword.Bluemix_notm}}.

Il nome dell'immagine è la combinazione del contenuto delle colonne **Repository** e **Tag** nel formato: `repository:tag`
{:tip}

```
ibmcloud cr image-list [--no-trunc] [--format FORMATO] [-q, --quiet] [--restrict LIMITAZIONE] [--include-ibm]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Lettore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--no-trunc`</dt>
<dd>(Facoltativo) Non troncare i digest immagine.</dd>
<dt>`--format FORMATO`</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un template Go.

Per ulteriori informazioni, vedi [Formattazione e filtro dell'output della CLI per i comandi {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>`-q`, `--quiet`</dt>
<dd>(Facoltativo) Ogni immagine viene elencata nel formato: `repository:tag`</dd>
<dt>`--restrict LIMITAZIONE`</dt>
<dd>(Facoltativo) Limita l'output per visualizzare solo le immagini nello spazio dei nomi o nello spazio dei nomi e nel repository specificati. </dd>
<dt>`--include-ibm`</dt>
<dd>(Facoltativo) Include le immagini pubbliche fornite da {{site.data.keyword.IBM_notm}} nell'output. Senza questa opzione, vengono elencate solo le immagini private per impostazione predefinita.</dd>
</dl>

**Esempio**

Visualizza le immagini nello spazio dei nomi *`bluebird`* nel formato `repository:tag`, senza troncare i digest immagine.

```
ibmcloud cr image-list --restrict bluebird --quiet --no-trunc
```
{: pre}

## `ibmcloud cr image-rm`
{: #bx_cr_image_rm}

Elimina una o più immagini specificate da {{site.data.keyword.registrylong_notm}}.

```
ibmcloud cr image-rm IMMAGINE [IMMAGINE...]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`IMMAGINE`</dt>
<dd>Il nome dell'immagine che desideri eliminare. Puoi eliminare più immagini contemporaneamente elencando ogni immagine nel comando con uno spazio tra ciascun nome. `IMMAGINE` deve essere nel formato `repository:tag`, ad esempio: `registry.ng.bluemix.net/namespace/image:latest`

<p>Per trovare i nomi delle tue immagini, esegui `ibmcloud cr image-list`. Combina il contenuto delle colonne **Repository** e **Tag** per creare il nome dell'immagine nel formato `repository:tag`. Se nel nome immagine non è specificata alcuna tag, per impostazione predefinita viene eliminata l'immagine contrassegnata con la tag `latest`.</p>

</dd>
</dl>

**Esempio**

Elimina l'immagine *`registry.ng.bluemix.net/bluebird/bird:1`*.

```
ibmcloud cr image-rm registry.ng.bluemix.net/bluebird/bird:1
```
{: pre}

## `ibmcloud cr info
`
{: #bx_cr_info}

Visualizza il nome e l'account del registro a cui sei collegato.

```
ibmcloud cr info
```
{: codeblock}

**Prerequisiti**

Nessun valore

## `ibmcloud cr login
`
{: #bx_cr_login}

Questo comando esegue il comando `docker login` nel registro. Il comando `docker login` è obbligatorio per abilitare l'esecuzione dei comandi `docker push` o `docker pull` per il registro. Questo comando non è obbligatorio per eseguire altri comandi `ibmcloud cr`. Se Docker non è installato, questo comando restituisce un messaggio di errore.

```
ibmcloud cr login
```
{: codeblock}

**Prerequisiti**

Nessun valore

## `ibmcloud cr namespace-add`
{: #bx_cr_namespace_add}

Scegli un nome per il tuo spazio dei nomi e aggiungilo al tuo account {{site.data.keyword.Bluemix_notm}}.

```
ibmcloud cr namespace-add SPAZIONOMI
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`SPAZIONOMI`</dt>
<dd>Lo spazio dei nomi che desideri aggiungere. Lo spazio dei nomi deve essere univoco tra tutti gli account {{site.data.keyword.Bluemix_notm}} nella stessa regione. Gli spazi dei nomi devono avere tra i 4 e i 30 caratteri e contenere solo lettere minuscole, numeri, trattini e caratteri di sottolineatura. Gli spazi dei nomi devono iniziare e terminare con una lettera o un numero.
  
<p>  
<strong>Suggerimento</strong> non inserire informazioni personali nei tuoi nomi dello spazio dei nomi.
</p>
  
</dd>
</dl>

**Esempio**

Crea uno spazio dei nomi con il nome *`bluebird`*.

```
ibmcloud cr namespace-add bluebird
```
{: pre}

## `ibmcloud cr namespace-list` (`ibmcloud cr namespaces`)
{: #bx_cr_namespace_list}

Visualizza tutti gli spazi dei nomi che appartengono al tuo account {{site.data.keyword.Bluemix_notm}}.

```
ibmcloud cr namespace-list
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Lettore o Gestore per {{site.data.keyword.registrylong_notm}}

## `ibmcloud cr namespace-rm`
{: #bx_cr_namespace_rm}

Rimuove uno spazio dei nomi dal tuo account {{site.data.keyword.Bluemix_notm}}. Le immagini in questo spazio dei nomi vengono eliminate quando si rimuove lo spazio dei nomi.

```
ibmcloud cr namespace-rm SPAZIONOMI
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`SPAZIONOMI`</dt>
<dd>Lo spazio dei nomi che desideri rimuovere.</dd>
</dl>

**Esempio**

Rimuovi lo spazio dei nomi *`bluebird`*.

```
ibmcloud cr namespace-rm bluebird
```
{: pre}

## `ibmcloud cr plan`
{: #bx_cr_plan}

Visualizza il piano dei prezzi.

```
ibmcloud cr plan
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

## `ibmcloud cr plan-upgrade`
{: #bx_cr_plan_upgrade}

Esegue il tuo upgrade al piano standard.

Per informazioni sui piani, vedi [Piani del registro](/docs/services/Registry/registry_overview.html#registry_plans).

```
ibmcloud cr plan-upgrade [PIANO]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`PIANO`</dt>
<dd>Il nome del piano dei prezzi a cui desideri eseguire l'upgrade. Se `PLAN` non viene specificato, il valore predefinito è `standard`.</dd>
</dl>

**Esempio**

Esegui l'upgrade al piano dei prezzi standard.

```
ibmcloud cr plan-upgrade standard
```
{: pre}

## `ibmcloud cr ppa-archive-load`
{: #bx_cr_ppa_archive_load}

Importa il software {{site.data.keyword.IBM_notm}} scaricato da [IBM Passport Advantage Online for customers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/software/passportadvantage/pao_customer.html) e impacchettato per essere utilizzato con Helm nel tuo spazio dei nomi del registro privato.

Le immagini del contenitore vengono trasmesse al tuo spazio dei nomi {{site.data.keyword.registryshort_notm}} privato. I grafici Helm sono scritti in una directory `ppa-import` che viene creata nella directory da cui esegui il comando. Facoltativamente, puoi utilizzare il [progetto open source Chart Museum ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/kubernetes/charts/tree/master/stable/chartmuseum) per ospitare i grafici Helm.

```
ibmcloud cr ppa-archive-load --archive FILE --namespace SPAZIONOMI
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
  <dt>`--archive FILE`</dt>
  <dd>Il percorso del file compresso scaricato da IBM Passport Advantage.</dd>
  <dt>`--namespace SPAZIONOMI`</dt>
  <dd>Uno dei tuoi spazi dei nomi. Le immagini del contenitore nel file compresso vengono trasmesse a questo spazio dei nomi. Per elencare gli spazi dei nomi, esegui `ibmcloud cr namespace-list`.</dd>
  <dt>`--chartmuseum-uri URI`</dt>
  <dd>(Facoltativo) L'identificativo di risorsa univoco per [Chart Museum ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/kubernetes/charts/tree/master/stable/chartmuseum).</dd>
  <dt>`--chartmuseum-user UTENTE`</dt>
  <dd>(Facoltativo) Il tuo nome utente di [Chart Museum ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/kubernetes/charts/tree/master/stable/chartmuseum).</dd>
  <dt>`--chartmuseum-password PASSWORD`</dt>
  <dd>(Facoltativo) La tua password di [Chart Museum ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/kubernetes/charts/tree/master/stable/chartmuseum).</dd>
</dl>

**Esempio**

Importa il software IBM e impacchettalo per l'utilizzo con Helm nel tuo spazio dei nomi del registro privato *`bluebird`*, in cui il percorso al file compresso è *`downloads/compressed_file.tgz`*.

```
ibmcloud cr ppa-archive-load --archive downloads/compressed_file.tgz --namespace bluebird
```
{: pre}

## `ibmcloud cr quota`
{: #bx_cr_quota}

Visualizza le tue quote correnti per traffico e archiviazione e le informazioni di utilizzo rispetto a tali quote.

```
ibmcloud cr quota
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Lettore, Scrittore o Gestore per {{site.data.keyword.registrylong_notm}}

## `ibmcloud cr quota-set`
{: #bx_cr_quota_set}

Modifica la quota specificata.

```
ibmcloud cr quota-set [--traffic TRAFFICO] [--storage ARCHIVIAZIONE]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--traffic TRAFFICO`</dt>
<dd>(Facoltativo) Modifica la tua quota di traffico sul valore specificato in megabyte. L'operazione non riesce se non sei autorizzato a impostare il traffico o se imposti un valore che supera il tuo piano dei prezzi corrente.</dd>
<dt>`--storage ARCHIVIAZIONE`</dt>
<dd>(Facoltativo) Modifica la tua quota di archiviazione sul valore specificato in megabyte. L'operazione non riesce se non sei autorizzato a impostare le quote di archiviazione o se imposti un valore che supera il tuo piano dei prezzi corrente.</dd>
</dl>

**Esempio**

Imposta il tuo limite di quota per il pull del traffico su *7000* megabyte e l'archiviazione su *600* megabyte.

```
ibmcloud cr quota-set --traffic 7000 --storage 600
```
{: pre}

## `ibmcloud cr region
`
{: #bx_cr_region}

Visualizza la regione di destinazione e il registro.

```
ibmcloud cr region
```
{: codeblock}

**Prerequisiti**

Nessun valore

Per ulteriori informazioni, vedi [Regioni](/docs/services/Registry/registry_overview.html#registry_regions).

## `ibmcloud cr region-set`
{: #bx_cr_region_set}

Imposta una regione di destinazione per i comandi {{site.data.keyword.registrylong_notm}}. Per elencare le regioni disponibili, esegui il comando senza parametri.

```
ibmcloud cr region-set [REGIONE]
```
{: codeblock}

**Prerequisiti**

Nessun valore

**Opzioni del comando**
<dl>
<dt>`REGIONE`</dt>
<dd>(Facoltativo) Il nome della tua regione di destinazione, ad esempio, `us-south`.

Per ulteriori informazioni, vedi [Regioni](/docs/services/Registry/registry_overview.html#registry_regions).

</dd>
</dl>

**Esempio**

Specifica la regione Stati Uniti Sud

```
ibmcloud cr region-set us-south
```
{: pre}

## `ibmcloud cr token-add`
{: #bx_cr_token_add}

Aggiungi un token che puoi utilizzare per controllare l'accesso a un registro.

```
ibmcloud cr token-add [--description DESCRIZIONE] [-q, --quiet] [--non-expiring] [--readwrite]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo della piattaforma IAM di Amministratore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--description DESCRIZIONE`</dt>
<dd>(Facoltativo) Specifica il valore come una descrizione per il token, che viene visualizzata quando esegui `ibmcloud cr token-list`. Se il tuo token viene creato automaticamente da {{site.data.keyword.containerlong_notm}}, la descrizione viene impostata sul nome del tuo cluster Kubernetes. In questo caso, il token viene rimosso automaticamente alla rimozione del cluster.
  
<p> 
  <strong>Suggerimento</strong> non inserire informazioni personali nella tua descrizione del token.
</p>

</dd>
<dt>`-q`, `--quiet`</dt>
<dd>(Facoltativo) Visualizza solo il token, senza alcun testo circostante.</dd>
<dt>`--non-expiring`</dt>
<dd>(Facoltativo) Crea un token con l'accesso che non scade. Se questo parametro non è impostato, l'accesso da un token scade dopo 24 ore per impostazione predefinita.</dd>
<dt>`--readwrite`</dt>
<dd>(Facoltativo) Crea un token che concede l'accesso in lettura e scrittura. Senza questa opzione, l'accesso è di sola lettura per impostazione predefinita.</dd>
</dl>

**Esempio**

Aggiungi un token con la descrizione *Token for my account* che non scade e ha l'accesso di lettura/scrittura.

```
ibmcloud cr token-add --description "Token for my account" --non-expiring --readwrite
```
{: pre}

## `ibmcloud cr token-get`
{: #bx_cr_token_get}

Richiama il token specificato dal registro.

```
ibmcloud cr token-get TOKEN
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo della piattaforma IAM di Amministratore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`TOKEN`</dt>
<dd>(Facoltativo) L'identificativo univoco del token che desideri richiamare. Per elencare i tuoi token, esegui `ibmcloud cr token-list`.</dd>
</dl>

**Esempio**

Richiama il token *10101010-101x-1x10-x1xx-x10xx10xxx10*.

```
ibmcloud cr token-get 10101010-101x-1x10-x1xx-x10xx10xxx10
```
{: pre}

## `ibmcloud cr token-list` (`ibmcloud cr tokens`)
{: #bx_cr_token_list}

Visualizza tutti i token esistenti per il tuo account {{site.data.keyword.Bluemix_notm}}.

```
ibmcloud cr token-list --format FORMATO
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo della piattaforma IAM di Amministratore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`--format FORMATO`</dt>
<dd>(Facoltativo) Formatta gli elementi di output utilizzando un template Go.

Per ulteriori informazioni, vedi [Formattazione e filtro dell'output della CLI per i comandi {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>

**Esempio**

Visualizza tutti i token in sola lettura, utilizzando la direttiva di formattazione *`"{{ if eq .ReadOnly true}}{{.ID}} - {{.Expiry}} - {{.ReadOnly}} - {{.Description}}{{ end }}"`*.

```
ibmcloud cr token-list --format "{{ if eq .ReadOnly true}}{{.ID}} - {{.Expiry}} - {{.ReadOnly}} - {{.Description}}{{ end }}"
```
{: pre}

Questo esempio produce l'output nel seguente formato:

```
10101010-101a-1a10-a1aa-a10aa10aaa10 - 1234567890 - true - demo
```
{: screen}

## `ibmcloud cr token-rm`
{: #bx_cr_token_rm}

Rimuove uno o più token specificati.

```
ibmcloud cr token-rm TOKEN [TOKEN...]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo della piattaforma IAM di Amministratore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`TOKEN`</dt>
<dd>(Facoltativo) TOKEN può essere il token stesso o l'identificativo univoco del token, come mostrato in `ibmcloud cr token-list`. È possibile specificare più token e devono essere separati da uno spazio.</dd>
</dl>

**Esempio**

Rimuovi il token *10101010-101x-1x10-x1xx-x10xx10xxx10*.

```
ibmcloud cr token-rm 10101010-101x-1x10-x1xx-x10xx10xxx10
```
{: pre}

## `ibmcloud cr vulnerability-assessment` (`ibmcloud cr va`)
{: #bx_cr_va}

Visualizza un report di valutazione delle vulnerabilità per le tue immagini.

```
ibmcloud cr vulnerability-assessment [--extended | -e] [--vulnerabilities | -v] [--configuration-issues | -c] [--output FORMATO | -o FORMATO] IMMAGINE [IMMAGINE...]
```
{: codeblock}

**Prerequisiti**

Autorizzazioni necessarie: il ruolo di accesso al servizio IAM di Lettore o Gestore per {{site.data.keyword.registrylong_notm}}

**Opzioni del comando**
<dl>
<dt>`IMMAGINE`</dt>
<dd>Il nome dell'immagine per cui vuoi ottenere un report. Il report ti informa se l'immagine ha delle vulnerabilità di pacchetto note. Puoi richiedere report per più immagini contemporaneamente elencando ogni immagine nel comando con uno spazio tra ciascun nome.

<p>Per trovare i nomi delle tue immagini, esegui `ibmcloud cr image-list`. Combina il contenuto delle colonne **Repository** e **Tag** per creare il nome dell'immagine nel formato `repository:tag`. Se nel nome immagine non è specificata alcuna tag, il report valuta l'immagine contrassegnata con la tag `latest`.</p>

<p>Sono supportati i seguenti sistemi operativi:

<ul>
<li>Alpine</li>
<li>CentOS</li>
<li>Debian</li>
<li>RHEL (Red Hat Enterprise Linux)</li>
<li>Ubuntu</li>
</ul>
</p>

Per ulteriori informazioni, vedi [Gestione della sicurezza delle immagini con il Controllo vulnerabilità](/docs/services/va/va_index.html).

</dd>
<dt>`--output FORMATO`, `-o FORMATO`</dt>
<dd>(Facoltativo) L'output del comando viene restituito nel formato scelto. Il formato predefinito è `text`. Sono supportati i seguenti formati:

<ul>
<li>`text`</li>
<li>`json`</li>
</ul>

</dd>
<dt>`--vulnerabilities`, `-v`</dt>
<dd>(Facoltativo) L'output del comando è limitato per mostrare solo le vulnerabilità.</dd>
<dt>`--configuration-issues`, `-c`</dt>
<dd>(Facoltativo) L'output del comando è limitato per mostrare solo i problemi di configurazione.</dd>
<dt>`--extended`, `-e`</dt>
<dd>(Facoltativo) L'output del comando mostra informazioni aggiuntive sulle correzioni per i pacchetti vulnerabili.</dd>

</dl>

**Esempi**

Visualizza un report di valutazione delle vulnerabilità standard per la tua immagine.

```
ibmcloud cr vulnerability-assessment registry.ng.bluemix.net/bluebird/bird:1
```
{: pre}

Visualizza un report di valutazione delle vulnerabilità per la tua immagine *`registry.ng.bluemix.net/bluebird/bird:1`* in formato JSON, che mostra solo le vulnerabilità.

```
ibmcloud cr vulnerability-assessment --vulnerabilities  --output json registry.ng.bluemix.net/bluebird/bird:1
```
{: pre}
