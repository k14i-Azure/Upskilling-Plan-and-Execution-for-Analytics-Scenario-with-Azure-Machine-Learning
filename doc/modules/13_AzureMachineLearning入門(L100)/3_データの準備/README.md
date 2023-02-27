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

| # | 保存先 | URI の例 |
| --- | --- | --- |
| 1 | ローカル コンピューター | `./home/username/data/my_data` |
| 2 | 公開されている http(s) サーバー | `https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv` |
| 3 | BLOB ストレージ | `wasbs://<containername>@<accountname>.blob.core.windows.net/<folder>/` |
| 4 | Azure Data Lake (gen2) | `abfss://<file_system>@<account_name>.dfs.core.windows.net/<folder>/<file>.csv` |
| 5 | Azure Data Lake (gen1) | `adl://<accountname>.azuredatalakestore.net/<folder1>/<folder2>` |
| 6 | Azure ML データストア | `azureml://datastores/<data_store_name>/paths/<folder1>/<folder2>/<folder3>/<file>.parquet` |


---


## [データ型](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#data-types)のユース ケース

### ファイル型はどのような場合に使用しますか?

> ファイルの種類は、ほとんどのシナリオで、任意の種類の 1 つのデータ ファイル (表形式データを含む) を操作する場合に推奨されます。この種類では、ローカル コンピューター上のストレージの場所、接続されたデータストア、BLOB/ADLS ストレージ、または一般公開されている http(s) の場所の URI でファイルの場所を指定できます。サポートされている URI には多くの種類があります。Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は uri_file と呼ばれます。

### フォルダー型はどのような場合に使用しますか?

> フォルダーの種類には、ファイルの種類と同じ機能とユース ケースがありますが、フォルダーの場所を指定するときに使用されます。Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は uri_folder と呼ばれます。

### テーブル型はどのような場合に使用しますか?

> テーブル型は、共有を容易にするためにスキーマ定義を抽象化する必要がある高度なシナリオに最も役立ちます。再利用可能な資産にキャプチャする複雑な変換とスキーマがある場合に使用する必要があります。より単純な表形式データの場合は、[ファイル] と [フォルダー] の種類をお勧めします。テーブルの種類を選択した場合、Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は mltable と呼ばれます。


---


## Azure Blob Storage へのアップロード



---

## [データ資産の作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-data-assets?tabs=cli)

> Azure ML データ資産は、Web ブラウザーのブックマーク (お気に入り) に似ています。 最も頻繁に使用されるデータを指す長いストレージ パス (URI) を覚える代わりに、データ資産を作成し、フレンドリ名を使ってその資産にアクセスできます。

> 対話型セッション (ノートブックなど) やジョブでデータにアクセスするだけの場合、最初にデータ資産を作成する必要は**ありません**。 ストレージ URI を使用してデータにアクセスできます。

