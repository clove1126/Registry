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

# Gestione dell'accesso utente con Identity and Access Management (IAM)
{: #iam}

L'accesso a {{site.data.keyword.registrylong}} per gli utenti nel tuo account è controllato da {{site.data.keyword.IBM_notm}} {{site.data.keyword.iamshort}} (IAM).
{: shortdesc}

Quando le politiche IAM sono abilitate per il tuo account in {{site.data.keyword.registrylong_notm}}, ogni utente che accede al servizio {{site.data.keyword.registrylong_notm}} nel tuo account deve avere assegnata una politica di accesso con un ruolo utente IAM definito. Questa politica determina il ruolo che l'utente ha all'interno del contesto del servizio e quali azioni può eseguire. Ogni azione in {{site.data.keyword.registrylong_notm}} è associata a uno o più [ruoli utente IAM](/docs/iam/users_roles.html).

Le politiche IAM vengono applicate solo quando utilizzi IAM per accedere a {{site.data.keyword.registrylong_notm}}. Se accedi a {{site.data.keyword.registrylong_notm}} utilizzando un altro metodo, come ad esempio un token di registro, le tue politiche non vengono applicate. Se desideri limitare l'accesso a uno o più spazi dei nomi per un ID che stai utilizzando per l'automazione, considera l'utilizzo di un ID servizio IAM invece di un token di registro. Per ulteriori informazioni sugli ID servizio, consulta [Creazione e gestione degli ID servizio](/docs/iam/serviceid.html#serviceids).

Per ulteriori informazioni su IAM, consulta [Accesso e gestione di IBM Cloud](/docs/iam/index.html#iamoverview).

Per informazioni sull'abilitazione delle politiche per {{site.data.keyword.registrylong_notm}}, consulta [Definizione delle politiche del ruolo di accesso utente](/docs/services/Registry/registry_users.html#user).

Le politiche abilitano l'accesso da concedere a diversi livelli. Alcune delle opzioni includono i seguenti livelli di accesso:

* Accesso al servizio nel tuo account
* Accesso a una risorsa specifica all'interno del servizio
* Accesso a tutti i servizi abilitati IAM nel tuo account

Dopo aver definito l'ambito della politica di accesso, assegna un ruolo. Esamina le seguenti tabelle che delineano le azioni che ogni ruolo consente all'interno del servizio {{site.data.keyword.registrylong_notm}}.

Per informazioni sull'assegnazione dei ruoli utente nell'IU, consulta [Gestione dell'accesso IAM](/docs/iam/mngiam.html#iammanidaccser).

Prova l'esercitazione [Esercitazione: concessione dell'accesso alle risorse {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_tutorial_configure_iam.html#iam_access).
{: tip}

## Ruoli di gestione della piattaforma
{: #platform_management_roles}

La seguente tabella illustra le azioni che sono associate ai ruoli di gestione della piattaforma. I ruoli di gestione della piattaforma consentono agli utenti di eseguire attività sulle risorse del servizio a livello di piattaforma, ad esempio l'assegnazione dell'accesso utente al servizio e la creazione o eliminazione degli ID servizio.

| Ruolo di gestione della piattaforma | Descrizione delle azioni | Azioni di esempio|
|:-----------------|:-----------------|:-----------------|
| Visualizzatore | Non supportato | |
| Editor | Non supportato | |
| Operatore | Non supportato | |
| Amministratore | <ul><li>Configura l'accesso per altri utenti</li><li>Configura i token di registro</li><li>Crea i cluster</li></ul> | <ul><li>Per informazioni sull'assegnazione dei ruoli utente nell'IU, consulta [Gestione dell'accesso IAM](/docs/iam/mngiam.html#iammanidaccser).</li><li>Aggiungi, elenca, richiama e rimuovi i token di registro</li><li>Per creare i cluster in {{site.data.keyword.containerlong_notm}}, devi assegnare all'utente il ruolo Amministratore per {{site.data.keyword.registrylong_notm}}, consulta [Preparazione per la creazione dei cluster](/docs/containers/cs_clusters.html#cluster_prepare).</li></ul> |
{: caption="Tabella 1. Azioni e ruoli utente IAM" caption-side="top"}

Per {{site.data.keyword.registrylong_notm}}, sono possibili le seguenti azioni:

| Azione| Operazione sul servizio | Ruolo
|:-----------------|:-----------------|:--------------|
| `container-registry.registrytoken.create` | [`ibmcloud cr token-add`](/docs/services/Registry/registry_cli.html#bx_cr_token_add) Aggiungi un token che puoi utilizzare per controllare l'accesso a un registro. | Amministratore |
| `container-registry.registrytoken.delete` | [`ibmcloud cr token-rm`](/docs/services/Registry/registry_cli.html#bx_cr_token_rm) Rimuovi uno o più token specificati. | Amministratore |
| `container-registry.registrytoken.get` | [`ibmcloud cr token-get`](/docs/services/Registry/registry_cli.html#bx_cr_token_get) Richiama il token specificato dal registro. | Amministratore |
| `container-registry.registrytoken.list` | [`ibmcloud cr token-list`](/docs/services/Registry/registry_cli.html#bx_cr_token_list) Visualizza tutti i token esistenti per il tuo account {{site.data.keyword.Bluemix_notm}}. | Amministratore |
{: caption="Tabella 2. Operazioni e azioni della piattaforma per la configurazione di {{site.data.keyword.registrylong_notm}}" caption-side="top"}

## Ruoli di accesso al servizio
{: #service_access_roles}

La seguente tabella illustra le azioni che sono associate ai ruoli di accesso al servizio. I ruoli di accesso al servizio abilitano gli utenti ad accedere a {{site.data.keyword.registrylong_notm}} nonché la possibilità di chiamare l'API {{site.data.keyword.registrylong_notm}}.

| Ruolo di accesso al servizio | Descrizione delle azioni | Azioni di esempio|
|:-----------------|:-----------------|:-----------------|
| Lettore | Il ruolo Lettore può visualizzare le informazioni. | <ul><li>Visualizza, controlla ed esegui il pull delle immagini</li><li>Visualizza gli spazi dei nomi</li><li>Visualizza le quote</li><li>Visualizza i report di vulnerabilità</li><li>Visualizza le firme dell'immagine</li></ul>|
| Scrittore | Il ruolo Scrittore può modificare le informazioni. |<ul><li>Crea, esegui il push ed elimina le immagini</li><li>Visualizza le quote</li><li>Firma le immagini</li><li>Aggiungi e rimuovi gli spazi dei nomi</li></ul> |
| Gestore | Il ruolo Gestore può eseguire tutte le azioni. | <ul><li>Visualizza, controlla, esegui il pull, crea, esegui il push ed elimina le immagini</li><li>Visualizza, aggiungi e rimuovi gli spazi dei nomi</li><li>Visualizza e imposta le quote</li><li>Visualizza i report di vulnerabilità</li><li>Visualizza e crea le firme dell'immagine</li><li>Controlla e modifica i piani dei prezzi</li><li>Abilita l'applicazione della politica IAM</li><li>Gestisci le esenzioni del Controllo vulnerabilità</li></ul> |
{: caption="Tabella 3. Azioni e ruoli di accesso al servizio IAM" caption-side="top"}

 Per i seguenti comandi {{site.data.keyword.registrylong_notm}}, devi disporre di almeno uno dei ruoli specificati come mostrato nelle seguenti tabelle. Per creare una politica che consenta l'accesso a {{site.data.keyword.registrylong_notm}} devi creare una politica in cui il nome del servizio è `container-registry`, l'istanza del servizio è vuota e la regione è quella a cui desideri concedere l'accesso o lascia il campo vuoto per concedere l'accesso a tutte le regioni.

### Ruoli di accesso per la configurazione di {{site.data.keyword.registrylong_notm}}
{: #access_roles_configure}

Per concedere a un utente l'autorizzazione per configurare il tuo {{site.data.keyword.registrylong_notm}} nel tuo account, devi creare una politica che concede uno o più ruoli nella seguente tabella. Quando crei la tua politica, non devi specificare `resource type` o `resource`.

**Esempio**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Manager>
```
{: pre}

| Azione| Operazione sul servizio | Ruolo
|:-----------------|:-----------------|:--------------|
| `container-registry.auth.set` | [`ibmcloud cr iam-policies-enable`](/docs/services/Registry/registry_cli.html#bx_cr_iam_policies_enable) Abilita l'applicazione della politica IAM. | Gestore |
| `container-registry.exemption.manager` | <ul><li>[`ibmcloud cr exemption-add`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_add) Crea un'esenzione per un problema di sicurezza.</li><li>[`ibmcloud cr exemption-list`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_list) Elenca le tue esenzioni per i problemi di sicurezza.</li><li>[`ibmcloud cr exemption-rm`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_rm) Elimina un'esenzione per un problema di sicurezza.</li><li>[`ibmcloud cr exemption-types`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_types) Elenca i tipi dei problemi di sicurezza che puoi esentare.</li></ul> | Gestore |
| `container-registry.plan.get` | [`ibmcloud cr plan`](/docs/services/Registry/registry_cli.html#bx_cr_plan) Visualizza il tuo piano dei prezzi. | Gestore |
| `container-registry.plan.set` | [`ibmcloud cr plan-upgrade`](/docs/services/Registry/registry_cli.html#bx_cr_plan_upgrade) Esegui l'upgrade al piano standard. | Gestore |
| `container-registry.quota.get` | [`ibmcloud cr quota`](/docs/services/Registry/registry_cli.html#bx_cr_quota) Visualizza le tue quote correnti per traffico e archiviazione e le informazioni di utilizzo rispetto a tali quote. | Lettore, Scrittore e Gestore |
| `container-registry.quota.set` | [`ibmcloud cr quota-set`](/docs/services/Registry/registry_cli.html#bx_cr_quota_set) Modifica la quota specificata. | Gestore |
{: caption="Tabella 4. Operazioni e azioni del servizio per la configurazione di {{site.data.keyword.registrylong_notm}}" caption-side="top"}

### Ruoli di accesso per l'utilizzo di {{site.data.keyword.registrylong_notm}}
{: #access_roles_using}

Per concedere a un utente l'autorizzazione ad accedere al contenuto di {{site.data.keyword.registrylong_notm}} nel tuo account, devi creare una politica che concede uno o più ruoli nella seguente tabella. Quando crei la tua politica, puoi limitare l'accesso a uno spazio dei nomi specifico specificando il tipo di risorsa `namespace` e il nome dello spazio dei nomi come risorsa. Se non si specifica `resource-type` e `resource`, la politica concede l'accesso a tutte le risorse presenti nell'account.

**Esempio**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Reader> [--resource-type namespace --resource <namespace_name>]
```
{: pre}

| Azione | Operazione sul servizio | Ruolo
|:-----------------|:-----------------|:--------------|
| `container-registry.image.build` | [`ibmcloud cr build`](/docs/services/Registry/registry_cli.html#bx_cr_build) Crea un'immagine contenitore. | Scrittore, Gestore |
| `container-registry.image.delete` | [`ibmcloud cr image-rm`](/docs/services/Registry/registry_cli.html#bx_cr_image_rm) Elimina una o più immagini. | Scrittore, Gestore |
| `container-registry.image.inspect` | [`ibmcloud cr image-inspect`](/docs/services/Registry/registry_cli.html#bx_cr_image_inspect) Visualizza i dettagli di un'immagine specifica. | Lettore, Gestore |
| `container-registry.image.list` | [`ibmcloud cr image-list`](/docs/services/Registry/registry_cli.html#bx_cr_image_list) Elenca le tue immagini contenitore. | Lettore, Gestore |
| `container-registry.image.pull` | `docker pull` Esegui il pull dell'immagine. | Lettore, Scrittore e Gestore |
| `container-registry.image.push` | <ul><li>`docker push` Esegui il push dell'immagine.</li><li>[`ibmcloud cr ppa-archive-load`](/docs/services/Registry/registry_cli.html#bx_cr_ppa_archive_load) Importa il software IBM scaricato da [IBM Passport Advantage Online for customers ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/software/passportadvantage/pao_customer.html) e impacchettato per essere utilizzato con Helm nel tuo spazio dei nomi del registro privato.</li></ul> | Scrittore, Gestore |
| `container-registry.image.vulnerabilities` | [`ibmcloud cr vulnerability-assessment`](/docs/services/Registry/registry_cli.html#bx_cr_va) Visualizza un report di valutazione delle vulnerabilità per la tua immagine. | Lettore, Gestore |
| `container-registry.namespace.create` | [`ibmcloud cr namespace-add`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_add) Aggiungi uno spazio dei nomi. | Scrittore, Gestore |
| `container-registry.namespace.delete` | [`ibmcloud cr namespace-rm`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_rm) Rimuovi uno spazio dei nomi. | Scrittore, Gestore |
| `container-registry.namespace.list` | [`ibmcloud cr namespace-list`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_list) Visualizza il tuo spazio dei nomi. | Lettore, Gestore |
| `container-registry.signature.create` | `docker trust sign` Firma l'immagine. | Scrittore, Gestore |
| `container-registry.signature.delete` | `docker trust revoke` Elimina la firma. | Scrittore, Gestore |
| `container-registry.signature.get` | `docker trust inspect` Controlla la firma. | Lettore, Gestore |
{: caption="Tabella 5. Operazioni e azioni del servizio per l'utilizzo di {{site.data.keyword.registrylong_notm}}" caption-side="top"}
