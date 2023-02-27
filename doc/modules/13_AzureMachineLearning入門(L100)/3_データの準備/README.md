###### Azure Machine Learning 入門 (L100)

# 3. データの準備

## データの概念

[データ | Azure Machine Learning 用語集 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#data)

> Azure Machine Learning では、さまざまな種類の [データ](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data) を利用できます。
> 
> * URI (ローカル/クラウド ストレージ内の場所)
>   * `uri_folder`
>   * `uri_file`
> * テーブル (表形式データの抽象化)
>   * `mltable`
> * プリミティブ
>   * `string`
>   * `boolean`
>   * `number`
> 
> ほとんどのシナリオでは、[URI](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#uri) (`uri_folder` および `uri_file`) を使用します。これは、ストレージをマウントするか、ノードにダウンロードすることで、ジョブ内のコンピューティング ノードのファイルシステムに簡単にマップできるストレージ内の場所です。
> 
> `mltable` は、AutoML ジョブ、並列ジョブ、およびいくつかの高度なシナリオで使用される表形式データの抽象化です。 Azure Machine Learning を使用し始めたばかりで、AutoML を使用していない場合は、URI から始めることを強くお勧めします。

### [URI](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#uri)

> URI (Uniform Resource Identifier) は、ローカル コンピューター上のストレージの場所、Azure ストレージ、または公開されている http(s) の場所を表します。
