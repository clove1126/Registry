---

copyright:
  years: 2018
lastupdated: "2018-09-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# Evénements {{site.data.keyword.cloudaccesstrailshort}}  
{: #at_events}

Utilisez le service {{site.data.keyword.cloudaccesstrailfull}} pour savoir comment les utilisateurs et les applications interagissent avec le service {{site.data.keyword.registrylong}} dans {{site.data.keyword.Bluemix}}. 
{:shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre des activités initiées par l'utilisateur qui change l'état d'un service dans {{site.data.keyword.Bluemix_notm}}. 
Pour plus d'informations, voir [{{site.data.keyword.cloudaccesstrailfull_notm}}](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla). 

Le tableau suivant répertorie les méthodes d'API générant un événement lorsqu'elles sont appelées :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Action</th>
	  <th>Description</th>
  </tr>
  <tr>
    <td>`container-registry.exemption.create`</td>
	  <td>Crée une exemption Vulnerability Advisor.</td>
  </tr>
  <tr>
    <td>`container-registry.exemption.delete`</td>
	  <td>Supprime une exemption Vulnerability Advisor.</td>
  </tr>
 </table>



## Où rechercher les événements ?
{: #ui}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le **domaine de compte** {{site.data.keyword.cloudaccesstrailshort}} qui se trouve dans la région {{site.data.keyword.Bluemix_notm}} où les événements sont générés.

La [région](/docs/services/Registry/registry_overview.html#registry_regions) dans laquelle un événement Vulnerability Advisor est disponible correspond à la région du registre {{site.data.keyword.registrylong_notm}} dans lequel la ressource (par exemple, l'image ou l'espace de nom) est disponible.






