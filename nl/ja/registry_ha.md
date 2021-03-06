---

copyright:
  years: 2018
lastupdated: "2018-09-11"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}



# 高可用性および災害復旧
{: #ha-dr}

{{site.data.keyword.registrylong}} サービスは、可用性の高い、領域的なサービスです。
{:shortdesc}

* サポートされる各領域では、複数の可用性ゾーンにわたるレジストリー・インフラストラクチャー全体でトラフィックが負荷分散されるため、単一障害点は存在しません。

* {{site.data.keyword.registrylong_notm}} に保存されたデータは定期的にバックアップされるので、耐障害性が高まります。

* 領域全体が使用不可になるケースに備えたい場合は、複数の領域のレジストリーにイメージをプッシュすることができます。 
  
  また、誤ってイメージを削除したり上書きしたりした場合に備えて、複数のレジストリーにイメージをプッシュすることもできます。

  領域について詳しくは、[領域](/docs/services/Registry/registry_overview.html#registry_regions)を参照してください。
