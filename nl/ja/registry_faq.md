---

copyright:
  years: 2018, 
lastupdated: "2018-11-15"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:faq: data-hd-content-type='faq'}

# よくある質問 (FAQ)
{: #registry_faq}

{{site.data.keyword.registrylong}} に関するよくある質問。
{: shortdesc}

## パブリック・イメージの一覧を表示する方法を教えてください。
{: #faq_list_public_images}
{: faq}

パブリック・イメージの一覧を表示するには、次のように `ibmcloud` コマンドを実行してください。グローバル・レジストリーを対象にしてから、 IBM 提供のパブリック・イメージの一覧を表示します。

```
ibmcloud cr region-set global
```
{: pre}

```
ibmcloud cr images --include-ibm
```
{: pre}

## Docker 以外のツールで、イメージを作成してレジストリーにプッシュすることはできますか?
{: #faq_tools}
{: faq}

はい。ただし、OCI のイメージ・フォーマットおよびプロトコルに対応したツールでなければなりません。
