---

copyright:
  years: 2018
lastupdated: "2018-10-19"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}

# Imagens públicas da {{site.data.keyword.IBM_notm}}
{: #public_images}

É possível acessar as imagens que são fornecidas pelo {{site.data.keyword.IBM}} usando a linha de comandos. Não é mais possível acessar as imagens públicas da {{site.data.keyword.IBM_notm}} usando a interface gráfica com o usuário.
{:shortdesc}

## Acessando as imagens públicas da IBM usando a CLI
{: #public_images_cli}

É possível acessar as imagens públicas da {{site.data.keyword.IBM_notm}} usando a linha de comandos.
{:shortdesc}

**Antes de iniciar**

- Efetue login no [{{site.data.keyword.cloud_notm}}](/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login):

  ```
  ibmcloud login
  ```
  {: pre}

Para listar as imagens públicas, conclua as etapas a seguir:

1. Tenha como destino o registro global:

   ```
   ibmcloud cr region-set global
   ```
   {: pre}

2. Liste as imagens públicas da {{site.data.keyword.IBM_notm}}:

   ```
   ibmcloud cr images --include-ibm
   ```
   {: pre}
