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

# Gerenciando o acesso de usuário com o Identity and Access Management
{: #iam}

O acesso ao {{site.data.keyword.registrylong}} para usuários em sua conta é controlado pelo {{site.data.keyword.IBM_notm}} {{site.data.keyword.iamshort}} (IAM).
{: shortdesc}

Quando as políticas do IAM são ativadas para sua conta no {{site.data.keyword.registrylong_notm}}, cada usuário que acessa o serviço {{site.data.keyword.registrylong_notm}} em sua conta deve receber uma política de acesso com uma função de usuário do IAM definida. Essa política determina qual função o usuário tem dentro do contexto do serviço e quais ações o usuário pode executar. Cada ação no {{site.data.keyword.registrylong_notm}} é mapeada para uma ou mais [funções de usuário do IAM](/docs/iam/users_roles.html).

As políticas do IAM são impostas apenas quando você usa o IAM para efetuar login no {{site.data.keyword.registrylong_notm}}. Se você efetuar login no {{site.data.keyword.registrylong_notm}} usando outro método, como um token de registro, suas políticas não serão impostas. Se você desejar restringir o acesso a um ou mais namespaces para um ID que está sendo usando para automação, considere usar um ID do serviço do IAM em vez de um token de registro. Para obter mais informações sobre IDs de Serviço, consulte [Criando e trabalhando com IDs de Serviço](/docs/iam/serviceid.html#serviceids).

Para obter mais informações sobre o IAM, consulte [IBM Cloud Access and Management](/docs/iam/index.html#iamoverview).

Para obter informações sobre como ativar políticas para o {{site.data.keyword.registrylong_notm}}, consulte [Definindo políticas de função de acesso de usuário](/docs/services/Registry/registry_users.html#user).

As políticas permitem que o acesso seja concedido em diferentes níveis. Algumas das opções incluem os níveis de acesso a seguir:

* Acesso ao serviço em sua conta
* Acesso a um recurso específico dentro do serviço
* Acesso a todos os serviços ativados pelo IAM em sua conta

Depois de definir o escopo da política de acesso, você designa uma função. Revise as tabelas a seguir que descrevem quais ações cada função permite dentro do serviço {{site.data.keyword.registrylong_notm}}.

Para obter informações sobre como designar funções de usuário na IU, consulte [Gerenciando o acesso ao IAM](/docs/iam/mngiam.html#iammanidaccser).

Experimente o tutorial [Tutorial: concedendo acesso aos recursos do {{site.data.keyword.registrylong_notm}}](/docs/services/Registry/registry_tutorial_configure_iam.html#iam_access).
{: tip}

## Funções de gerenciamento de plataforma
{: #platform_management_roles}

A tabela a seguir detalha as ações que são mapeadas para funções de gerenciamento de plataforma. As funções de gerenciamento de plataforma permitem que os usuários executem tarefas em recursos de serviço no nível de plataforma, por exemplo, designar acesso de usuário para o serviço e criar ou excluir IDs de Serviço.

| Função de gerenciamento da plataforma | Descrição das ações | Ações de exemplo|
|:-----------------|:-----------------|:-----------------|
| Visualizador | Sem suporte | |
| Aplicativos | Sem suporte | |
| Operador | Sem suporte | |
| Administrador | <ul><li>Configurar acesso para outros usuários</li><li>Configurar tokens de registro</li><li>Criar clusters</li></ul> | <ul><li>Para obter informações sobre como designar funções de usuário na IU, consulte [Gerenciando o acesso ao IAM](/docs/iam/mngiam.html#iammanidaccser).</li><li>Incluir, listar, recuperar e remover tokens de registro</li><li>Para criar clusters no {{site.data.keyword.containerlong_notm}}, deve-se designar a função de Administrador para o {{site.data.keyword.registrylong_notm}} para o usuário. Consulte [Preparando para criar clusters](/docs/containers/cs_clusters.html#cluster_prepare).</li></ul> |
{: caption="Tabela 1. Funções e ações do usuário do IAM" caption-side="top"}

Para {{site.data.keyword.registrylong_notm}}, existem as seguintes ações:

| Action| Operação em serviço | Função
|:-----------------|:-----------------|:--------------|
| `container-registry.registrytoken.create` | [`ibmcloud cr token-add`](/docs/services/Registry/registry_cli.html#bx_cr_token_add) Inclua um token que possa ser usado para controlar o acesso a um registro. | Administrador |
| `container-registry.registrytoken.delete` | [`ibmcloud cr token-rm`](/docs/services/Registry/registry_cli.html#bx_cr_token_rm) Remova um ou mais tokens especificados. | Administrador |
| `container-registry.registrytoken.get` | [`ibmcloud cr token-get`](/docs/services/Registry/registry_cli.html#bx_cr_token_get) Recupere o token especificado por meio do registro. | Administrador |
| `container-registry.registrytoken.list` | [`ibmcloud cr token-list`](/docs/services/Registry/registry_cli.html#bx_cr_token_list) Exiba todos os tokens que existem para sua conta do {{site.data.keyword.Bluemix_notm}}. | Administrador |
{: caption="Tabela 2. Ações e operações de plataforma para configurar o {{site.data.keyword.registrylong_notm}}" caption-side="top"}

## Funções de acesso de serviço
{: #service_access_roles}

A tabela a seguir detalha as ações que são mapeadas para as funções de acesso de serviço. As funções de acesso de serviço permitem que os usuários acessem o {{site.data.keyword.registrylong_notm}}, bem como a capacidade de chamar a API do {{site.data.keyword.registrylong_notm}}.

| Função de acesso de serviço | Descrição das ações | Ações de exemplo|
|:-----------------|:-----------------|:-----------------|
| Leitor | A função de Leitor pode visualizar informações. | <ul><li>Visualizar, inspecionar e fazer pull de imagens</li><li>Visualizar namespaces</li><li>Visualizar cotas</li><li>Visualizar relatórios de vulnerabilidade</li><li>Visualizar assinaturas de imagem</li></ul>|
| Gravador | A função de Gravador pode editar informações. |<ul><li>Construir, enviar por push e excluir imagens</li><li>Visualizar cotas</li><li>Assinar imagens</li><li>Incluir e remover namespaces</li></ul> |
| Gerente | A função de Gerenciador pode executar todas as ações. | <ul><li>Visualizar, inspecionar, fazer pull, construir, enviar por push e excluir imagens</li><li>Visualizar, incluir e remover namespaces</li><li>Visualizar e configurar cotas</li><li>Visualizar relatórios de vulnerabilidade</li><li>Visualizar e criar assinaturas de imagem</li><li>Revisar e mudar planos de precificação</li><li>Ativar o cumprimento de política do IAM</li><li>Gerenciar isenções do Vulnerability Advisor</li></ul> |
{: caption="Tabela 3. Funções e ações de acesso do serviço IAM" caption-side="top"}

 Para os comandos do {{site.data.keyword.registrylong_notm}} a seguir, deve-se ter pelo menos uma das funções especificadas, conforme mostrado nas tabelas a seguir. Para criar uma política que permita acesso ao {{site.data.keyword.registrylong_notm}}, deve-se criar uma política em que o nome do serviço seja `container-registry`, a instância de serviço esteja vazia e a região seja a região à qual você deseja conceder acesso ou esteja vazia para conceder acesso a todas as regiões.

### Funções de acesso para configurar o {{site.data.keyword.registrylong_notm}}
{: #access_roles_configure}

Para conceder a um usuário permissão para configurar seu {{site.data.keyword.registrylong_notm}} em sua conta, deve-se criar uma política que conceda uma ou mais funções na tabela a seguir. Ao criar sua política, não se deve especificar um `resource type` nem um `resource`.

**Exemplo**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Manager>
```
{: pre}

| Action| Operação em serviço | Função
|:-----------------|:-----------------|:--------------|
| `container-registry.auth.set` | [`ibmcloud cr iam-policies-enable`](/docs/services/Registry/registry_cli.html#bx_cr_iam_policies_enable) Ative o cumprimento de política do IAM. | Gerente |
| `container-registry.exemption.manager` | <ul><li>[`ibmcloud cr exemption-add`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_add) Crie uma isenção para um problema de segurança.</li><li>[`ibmcloud cr exemption-list`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_list) Listar suas isenções para problemas de segurança.</li><li>[`ibmcloud cr exemption-rm`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_rm) Excluir uma isenção para um problema de segurança.</li><li>[`ibmcloud cr exemption-types`](/docs/services/Registry/registry_cli.html#bx_cr_exemption_types) Listar os tipos de problemas de segurança que podem ser isentados.</li></ul> | Gerente |
| `container-registry.plan.get` | [`ibmcloud cr plan`](/docs/services/Registry/registry_cli.html#bx_cr_plan) Exiba seu plano de precificação. | Gerente |
| `container-registry.plan.set` | [`ibmcloud cr plan-upgrade`](/docs/services/Registry/registry_cli.html#bx_cr_plan_upgrade) Faça upgrade para o plano padrão. | Gerente |
| `container-registry.quota.get` | [`ibmcloud cr quota`](/docs/services/Registry/registry_cli.html#bx_cr_quota) Exiba suas cotas atuais para tráfego e armazenamento e informações de uso em relação às cotas. | Leitor, Gravador, Gerenciador |
| `container-registry.quota.set` | [`ibmcloud cr quota-set`](/docs/services/Registry/registry_cli.html#bx_cr_quota_set) Modifique a cota especificada. | Gerente |
{: caption="Tabela 4. Operações e ações de serviço para configurar o {{site.data.keyword.registrylong_notm}}" caption-side="top"}

### Funções de acesso para usar o {{site.data.keyword.registrylong_notm}}
{: #access_roles_using}

Para conceder a um usuário permissão para acessar o conteúdo do {{site.data.keyword.registrylong_notm}} em sua conta, deve-se criar uma política que conceda uma ou mais funções na tabela a seguir. Ao criar sua política, é possível restringir o acesso a um namespace específico especificando o tipo de recurso `namespace` e o nome do namespace como o recurso. Se você não especificar um `resource-type` e um `resource`, a política concederá acesso a todos os recursos na conta.

**Exemplo**

```
bx iam user-policy-create <user_email> --service-name container-registry --region <us-south> --roles <Reader> [--resource-type namespace --resource <namespace_name>]
```
{: pre}

| Action | Operação em serviço | Função
|:-----------------|:-----------------|:--------------|
| `container-registry.image.build` | [`ibmcloud cr build`](/docs/services/Registry/registry_cli.html#bx_cr_build) Construa uma imagem de contêiner. | Gravador, Gerente |
| `container-registry.image.delete` | [`ibmcloud cr image-rm`](/docs/services/Registry/registry_cli.html#bx_cr_image_rm) Exclua uma ou mais imagens. | Gravador, Gerente |
| `container-registry.image.inspect` | [`ibmcloud cr image-inspect`](/docs/services/Registry/registry_cli.html#bx_cr_image_inspect) Exiba detalhes sobre uma imagem específica. | Leitor, Gerenciador |
| `container-registry.image.list` | [`ibmcloud cr image-list`](/docs/services/Registry/registry_cli.html#bx_cr_image_list) Liste suas imagens de contêiner. | Leitor, Gerenciador |
| `container-registry.image.pull` | `docker pull` Faça pull da imagem. | Leitor, Gravador, Gerenciador |
| `container-registry.image.push` | <ul><li>`docker push` Envie a imagem por push.</li><li>[`ibmcloud cr ppa-archive-load`](/docs/services/Registry/registry_cli.html#bx_cr_ppa_archive_load) Importa o software IBM transferido por download do [IBM Passport Advantage Online para clientes ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/software/passportadvantage/pao_customer.html) e empacotado para uso com o Helm em seu namespace de registro privado.</li></ul> | Gravador, Gerente |
| `container-registry.image.vulnerabilities` | [`ibmcloud cr vulnerability-assessment`](/docs/services/Registry/registry_cli.html#bx_cr_va) Visualize um relatório de avaliação de vulnerabilidade para sua imagem. | Leitor, Gerenciador |
| `container-registry.namespace.create` | [`ibmcloud cr namespace-add`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_add) Inclua um namespace. | Gravador, Gerente |
| `container-registry.namespace.delete` | [`ibmcloud cr namespace-rm`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_rm) Remova um namespace. | Gravador, Gerente |
| `container-registry.namespace.list` | [`ibmcloud cr namespace-list`](/docs/services/Registry/registry_cli.html#bx_cr_namespace_list) Exiba seus namespaces. | Leitor, Gerenciador |
| `container-registry.signature.create` | `docker trust sign` Assine a imagem. | Gravador, Gerente |
| `container-registry.signature.delete` | `docker trust revoke` Exclua a assinatura. | Gravador, Gerente |
| `container-registry.signature.get` | `docker trust inspect` Inspecione a assinatura. | Leitor, Gerenciador |
{: caption="Tabela 5. Ações de serviço e operações para usar o {{site.data.keyword.registrylong_notm}}" caption-side="top"}
