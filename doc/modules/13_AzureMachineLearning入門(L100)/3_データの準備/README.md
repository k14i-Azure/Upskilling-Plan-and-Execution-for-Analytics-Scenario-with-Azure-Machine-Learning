###### Azure Machine Learning 入門 (L100)

# 3. データの準備

- [3. データの準備](#3-データの準備)
  - [1. データの概念](#1-データの概念)
    - [1.1. URI](#11-uri)
  - [2. データ型のユース ケース](#2-データ型のユース-ケース)
    - [2.1. ファイル型はどのような場合に使用しますか?](#21-ファイル型はどのような場合に使用しますか)
    - [2.2. フォルダー型はどのような場合に使用しますか?](#22-フォルダー型はどのような場合に使用しますか)
    - [2.3. テーブル型はどのような場合に使用しますか?](#23-テーブル型はどのような場合に使用しますか)
  - [3. Azure Blob Storage へのアップロード](#3-azure-blob-storage-へのアップロード)
    - [3.1. 手順(例)](#31-手順例)
  - [4. データ資産の作成](#4-データ資産の作成)
    - [4.1. 手順(例)](#41-手順例)
  - [5. データへのラベル付け](#5-データへのラベル付け)
    - [5.1. 画像のラベル付け](#51-画像のラベル付け)
      - [5.1.1. 画像のラベル付けプロジェクトの作成ステップ](#511-画像のラベル付けプロジェクトの作成ステップ)
        - [5.1.1.1. プロジェクトの作成と詳細情報の入力](#5111-プロジェクトの作成と詳細情報の入力)
        - [5.1.1.2. オプション: 従業員の追加 (ベンダーへのアウトソーシング)](#5112-オプション-従業員の追加-ベンダーへのアウトソーシング)
        - [5.1.1.3. データセットの選択または作成](#5113-データセットの選択または作成)
        - [5.1.1.4. オプション: 増分更新の構成](#5114-オプション-増分更新の構成)
        - [5.1.1.5. ラベル カテゴリの追加](#5115-ラベル-カテゴリの追加)
        - [5.1.1.6. オプション: ラベル付けの手順の説明](#5116-オプション-ラベル付けの手順の説明)
        - [5.1.1.7. オプション: ラベル付けの品質管理 (プレビュー)](#5117-オプション-ラベル付けの品質管理-プレビュー)
        - [5.1.1.8. オプション: ML によるラベル付け](#5118-オプション-ml-によるラベル付け)
    - [5.2. テキストのラベル付け](#52-テキストのラベル付け)
      - [5.2.1. テキストのラベル付けプロジェクトの作成ステップ](#521-テキストのラベル付けプロジェクトの作成ステップ)
        - [5.2.1.1. プロジェクトの作成と詳細情報の入力](#5211-プロジェクトの作成と詳細情報の入力)
        - [5.2.1.2. オプション: 従業員の追加 (ベンダーへのアウトソーシング)](#5212-オプション-従業員の追加-ベンダーへのアウトソーシング)
        - [5.2.1.3. データセットの選択または作成](#5213-データセットの選択または作成)
        - [5.2.1.4. オプション: 増分更新の構成](#5214-オプション-増分更新の構成)
        - [5.2.1.5. ラベル カテゴリの追加](#5215-ラベル-カテゴリの追加)
        - [5.2.1.6. オプション: ラベル付けの手順の説明](#5216-オプション-ラベル付けの手順の説明)
        - [5.2.1.7. オプション: ラベル付けの品質管理 (プレビュー)](#5217-オプション-ラベル付けの品質管理-プレビュー)
        - [5.2.1.8. オプション: ML によるラベル付け](#5218-オプション-ml-によるラベル付け)
    - [5.3. ラベル付けプロジェクトの実行と監視](#53-ラベル付けプロジェクトの実行と監視)
      - [5.3.1. ダッシュボードでの進行状況の表示](#531-ダッシュボードでの進行状況の表示)
      - [5.3.2. ラベル付けされたデータと合意ラベルの確認](#532-ラベル付けされたデータと合意ラベルの確認)
      - [5.3.3. 詳細の表示と変更](#533-詳細の表示と変更)
    - [5.4. ラベル付けツールの使い方](#54-ラベル付けツールの使い方)
    - [5.5. ラベルの追加](#55-ラベルの追加)
    - [5.6. ラベルのエクスポート](#56-ラベルのエクスポート)
      - [5.6.1. 画像ラベルのエクスポート](#561-画像ラベルのエクスポート)
      - [5.6.2. テキストラベルのエクスポート](#562-テキストラベルのエクスポート)
    - [5.7. ラベル付けのアウトソーシング](#57-ラベル付けのアウトソーシング)
  - [6. データ資産 (データセット) のバージョン管理と追跡](#6-データ資産-データセット-のバージョン管理と追跡)
  - [7. データ ドリフトの監視](#7-データ-ドリフトの監視)
  - [8. データ準備の効率化](#8-データ準備の効率化)
  - [9. ラーニング](#9-ラーニング)
  - [10. 参考リンク](#10-参考リンク)


---


## 1. データの概念

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

### 1.1. [URI](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#uri)

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


## 2. [データ型](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#data-types)のユース ケース

### 2.1. ファイル型はどのような場合に使用しますか?

> ファイルの種類は、ほとんどのシナリオで、任意の種類の 1 つのデータ ファイル (表形式データを含む) を操作する場合に推奨されます。この種類では、ローカル コンピューター上のストレージの場所、接続されたデータストア、BLOB/ADLS ストレージ、または一般公開されている http(s) の場所の URI でファイルの場所を指定できます。サポートされている URI には多くの種類があります。Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は uri_file と呼ばれます。

### 2.2. フォルダー型はどのような場合に使用しますか?

> フォルダーの種類には、ファイルの種類と同じ機能とユース ケースがありますが、フォルダーの場所を指定するときに使用されます。Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は uri_folder と呼ばれます。

### 2.3. テーブル型はどのような場合に使用しますか?

> テーブル型は、共有を容易にするためにスキーマ定義を抽象化する必要がある高度なシナリオに最も役立ちます。再利用可能な資産にキャプチャする複雑な変換とスキーマがある場合に使用する必要があります。より単純な表形式データの場合は、[ファイル] と [フォルダー] の種類をお勧めします。テーブルの種類を選択した場合、Azure Machine Learning CLI v2 または Python SDK v2 では、このデータ型は mltable と呼ばれます。


---


## 3. Azure Blob Storage へのアップロード

### 3.1. 手順(例)

![Azure Blob Storage へのアップロード手順00001](./assets/images/AzureBlobStorageUploadBlob-00001.png)

![Azure Blob Storage へのアップロード手順00002](./assets/images/AzureBlobStorageUploadBlob-00002.png)

![Azure Blob Storage へのアップロード手順00003](./assets/images/AzureBlobStorageUploadBlob-00003.png)

![Azure Blob Storage へのアップロード手順00004](./assets/images/AzureBlobStorageUploadBlob-00004.png)

![Azure Blob Storage へのアップロード手順00005](./assets/images/AzureBlobStorageUploadBlob-00005.png)

![Azure Blob Storage へのアップロード手順00006](./assets/images/AzureBlobStorageUploadBlob-00006.png)

![Azure Blob Storage へのアップロード手順00007](./assets/images/AzureBlobStorageUploadBlob-00007.png)

![Azure Blob Storage へのアップロード手順00008](./assets/images/AzureBlobStorageUploadBlob-00008.png)

![Azure Blob Storage へのアップロード手順00009](./assets/images/AzureBlobStorageUploadBlob-00009.png)


---

## 4. [データ資産の作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-data-assets?tabs=cli)

> Azure ML データ資産は、Web ブラウザーのブックマーク (お気に入り) に似ています。 最も頻繁に使用されるデータを指す長いストレージ パス (URI) を覚える代わりに、データ資産を作成し、フレンドリ名を使ってその資産にアクセスできます。

> 対話型セッション (ノートブックなど) やジョブでデータにアクセスするだけの場合、最初にデータ資産を作成する必要は**ありません**。 ストレージ URI を使用してデータにアクセスできます。

補足: たとえば、データのラベル付けをする際に、データ資産が作成されている必要があります。 (データのラベル付けプロジェクトを作成する中でデータ資産を作成することもできます。) この場合、Azure ML v2 のデータ資産には対応しておらず、Azure ML v1 のデータ資産のみに対応していることに留意してください。

### 4.1. 手順(例)

![データ資産の作成手順00001](./assets/images/AML-Creating-Data-Asset-00001.png)

![データ資産の作成手順00002](./assets/images/AML-Creating-Data-Asset-00002.png)

![データ資産の作成手順00003](./assets/images/AML-Creating-Data-Asset-00003.png)

![データ資産の作成手順00004](./assets/images/AML-Creating-Data-Asset-00004.png)

![データ資産の作成手順00005](./assets/images/AML-Creating-Data-Asset-00005.png)

![データ資産の作成手順00006](./assets/images/AML-Creating-Data-Asset-00006.png)

![データ資産の作成手順00007](./assets/images/AML-Creating-Data-Asset-00007.png)

![データ資産の作成手順00008](./assets/images/AML-Creating-Data-Asset-00008.png)

![データ資産の作成手順00009](./assets/images/AML-Creating-Data-Asset-00009.png)

![データ資産の作成手順00010](./assets/images/AML-Creating-Data-Asset-00010.png)

![データ資産の作成手順00011](./assets/images/AML-Creating-Data-Asset-00011.png)

![データ資産の作成手順00012](./assets/images/AML-Creating-Data-Asset-00012.png)

![データ資産の作成手順00013](./assets/images/AML-Creating-Data-Asset-00013.png)

![データ資産の作成手順00014](./assets/images/AML-Creating-Data-Asset-00014.png)

![データ資産の作成手順00015](./assets/images/AML-Creating-Data-Asset-00015.png)

![データ資産の作成手順00016](./assets/images/AML-Creating-Data-Asset-00016.png)

![データ資産の作成手順00017](./assets/images/AML-Creating-Data-Asset-00017.png)

![データ資産の作成手順00018](./assets/images/AML-Creating-Data-Asset-00018.png)


---


## 5. データへのラベル付け

### 5.1. [画像のラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects)

> Azure Machine Learning のデータのラベル付けは、以下のように、データのラベル付けプロジェクトを作成、管理、監視するツールです。
> 
> * データ、ラベル、チーム メンバーを調整して、ラベル付けタスクを効率的に管理する。
> * 進行状況を追跡し、未完了のラベル付けタスクのキューを維持する。
> * プロジェクトを開始および停止し、ラベル付けの進行状況を制御する。
> * ラベル付きのデータを確認し、Azure Machine Learning データセットとしてエクスポートする。
>
> 画像データには、".jpg"、".jpeg"、".png"、".jpe"、".jfif"、".bmp"、".tif"、".tiff"、".dcm"、".dicom" のいずれかの種類のファイルを使用できます。

> このタスクを補助するために、支援付き機械学習データ ラベル付け、つまり人間参加型 (Human in the loop) のラベル付けを使用します。
> 
> 分類、物体検出 (境界ボックス)、インスタンスのセグメント化 (ポリゴン) を行うためのラベルを設定します。

#### 5.1.1. [画像のラベル付けプロジェクトの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#create-an-image-labeling-project)ステップ

![画像のラベル付けプロジェクトの作成](./assets/images/AML-Image-Data-Labeling-00001.png)

##### 5.1.1.1. [プロジェクトの作成と詳細情報の入力](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#create-an-image-labeling-project)

![プロジェクトの作成と詳細情報の入力1](./assets/images/AML-Image-Data-Labeling-00002.png)

- プロジェクト名
- メディアの種類
  - イメージ (こちらを選択)
  - テキスト
- ラベル付けタスクの種類
  - 画像分類の複数クラス
    - > クラスのセット内の 1 つのクラスのみを画像に適用します
  - 画像分類の複数ラベル
    - > クラスのセット内の 1 つまたは複数のラベルを画像に適用します。たとえば、犬の写真には、犬と昼間の両方のラベルが付けられる場合があります。
  - オブジェクト ID (四角形領域)
    - > 画像内の各オブジェクトにクラスと境界ボックスを割り当てます
  - 多角形 (インスタンスのセグメント化)
    - > イメージにポリゴンを描画し、それにラベル クラスを割り当てる

![プロジェクトの作成と詳細情報の入力2](./assets/images/AML-Image-Data-Labeling-00003.png)

##### 5.1.1.2. オプション: [従業員の追加 (ベンダーへのアウトソーシング)](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#add-workforce-optional)

- Azure Marketplace でベンダーのラベル付け会社を利用するかどうかを選択
- 現在選択できるベンダー:
  - [iSoftStone Inc](https://www.isoftstoneinc.com/)
  - [Quadrant Resource](https://www.quadrantresource.com/)

![従業員の追加 (ベンダーへのアウトソーシング)](./assets/images/AML-Image-Data-Labeling-00004.png)

##### 5.1.1.3. [データセットの選択または作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#specify-the-data-to-label)

> 注意: 1 つのプロジェクトに 50 万個を超えるファイルを含めることはできません。 データセットのファイル数がこれを超える場合は、最初の 50 万件のファイルだけが読み込まれます。

![データセットの選択または作成](./assets/images/AML-Image-Data-Labeling-00005.png)

##### 5.1.1.4. オプション: [増分更新の構成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#configure-incremental-refresh)

> ご使用のデータセットでは新しいデータポイントが定期的にチェックされます。新しいデータポイントがあった場合、プロジェクトの新しいタスクとして追加されます。

![増分更新の構成](./assets/images/AML-Image-Data-Labeling-00006.png)

##### 5.1.1.5. [ラベル カテゴリの追加](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#specify-label-classes)

- > 単純なリストを作成するには、[+ ラベル カテゴリの追加] を選択して各ラベルを作成します。
- > 異なるグループにラベルを作成するには、[+ ラベル カテゴリの追加] を選択して最上位レベルのラベルを作成します。 次に、各最上位レベルの下にある + を選択して、そのカテゴリの次のレベルのラベルを作成します。 任意のグループに対して最大 6 つのレベルを作成できます。
- ラベルの一括編集もできます。区切り記号として コンマ, タブ, 改行, コロン, セミコロン のいずれかを指定します。

![ラベル カテゴリの追加1](./assets/images/AML-Image-Data-Labeling-00007.png)

![ラベル カテゴリの追加2](./assets/images/AML-Image-Data-Labeling-00008.png)

##### 5.1.1.6. オプション: [ラベル付けの手順の説明](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#describe-the-image-labeling-task)

> 手順は、人間のラベラーがタスクを理解しようとするときに使用されます。ラベルの明確な定義とサンプルを指定すると、最適な結果が得られます。

![ラベル付けの手順の説明](./assets/images/AML-Image-Data-Labeling-00009.png)

##### 5.1.1.7. オプション: [ラベル付けの品質管理 (プレビュー)](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#quality-control-preview)

- 複数のラベラーの合意によるラベル付け。
- > 最小ラベラー: そのアセットのラベル付けをした、ラベル付け担当者 (Labelers) の最少人数は合意されているものと考えられています。1〜50 人。
- > 最大ラベラー: 個別の資産にラベルを付けることができるラベラーの最大数。1〜50 人。
- > 項目がラベラーの最大数に送られても合意に達しない場合、その状態は `Needs Review` になり、プロジェクト所有者が項目のラベル付けの責任を持つことになります。
- > 注意: インスタンスのセグメント化プロジェクトでは、合意ラベル付けを使用できません。
- > プロジェクトの開始後にこれらの設定を変更することはできません。

![ラベル付けの品質管理 (プレビュー)](./assets/images/AML-Image-Data-Labeling-00010.png)

##### 5.1.1.8. オプション: [ML によるラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#use-ml-assisted-data-labeling)

- > ラベラーがレビューするために、ラベル付け前のデータに対してモデルをトレーニングする ML Assist によるラベル付けを有効にすることにより、ラベル付けプロジェクトを高速化します。
- > 支援付き機械学習ラベル付けは、2 つのフェーズで構成されます。
  > - [クラスタリング](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#clustering)
  > - [事前ラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#prelabeling)
- コンピューティング先: 既定の使用 または カスタマイズ
  - > 既定の使用: このオプションでは、既定のラベル付けコンピューティング クラスターが既に存在する場合はそれが使用され、それ以外の場合は、支援支援付き機械学習ラベル付けを使用するために、既定のコンピューティング クラスターが作成されます。[カスタマイズ] オプションを選択して、カスタム コンピューティング クラスターを選択または作成することもできます。
  - > カスタマイズ: GPU コンピューティング クラスターの選択 または 作成

![ML によるラベル付け1](./assets/images/AML-Image-Data-Labeling-00011.png)

![ML によるラベル付け2](./assets/images/AML-Image-Data-Labeling-00012.png)

![ML によるラベル付け3](./assets/images/AML-Image-Data-Labeling-00013.png)

> 支援付き機械学習ラベル付けは、いくつかの項目がラベル付けされた後、自動的に開始します。 この自動しきい値は、プロジェクトによって異なります。 ただし、ラベル付けされたデータがプロジェクトに含まれていれば、支援付き機械学習トレーニングの実行を手動で開始できます。


### 5.2. [テキストのラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects)

#### 5.2.1. テキストのラベル付けプロジェクトの作成ステップ

![プロジェクトの作成と詳細情報の入力](./assets/images/AML-Text-Data-Labeling-00001.png)

##### 5.2.1.1. [プロジェクトの作成と詳細情報の入力](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#create-a-text-labeling-project)

- プロジェクト名
- メディアの種類
  - イメージ
  - テキスト (こちらを選択)
- ラベル付けタスクの種類
  - テキスト分類マルチクラス
    - > クラスのセット内の 1 つのラベルのみをテキストに適用します
  - テキスト分類の複数ラベル
    - > 一連のクラスの 1 つまたは複数のラベルをテキストに適用します
  - テキスト固有表現認識
    - > テキストに 1 つ以上のエンティティで注釈を付けます

![プロジェクトの作成と詳細情報の入力](./assets/images/AML-Text-Data-Labeling-00002.png)

##### 5.2.1.2. オプション: [従業員の追加 (ベンダーへのアウトソーシング)](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#add-workforce-optional)

- Azure Marketplace でベンダーのラベル付け会社を利用するかどうかを選択
- 現在選択できるベンダー:
  - [iSoftStone Inc](https://www.isoftstoneinc.com/)
  - [Quadrant Resource](https://www.quadrantresource.com/)

![従業員の追加 (ベンダーへのアウトソーシング)](./assets/images/AML-Text-Data-Labeling-00003.png)

##### 5.2.1.3. [データセットの選択または作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#select-or-create-a-dataset)

> 注意: 1 つのプロジェクトに 50 万個を超えるファイルを含めることはできません。 データセットのファイル数がこれを超える場合は、最初の 50 万件のファイルだけが読み込まれます。

![データセットの選択または作成](./assets/images/AML-Text-Data-Labeling-00004.png)

##### 5.2.1.4. オプション: [増分更新の構成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#configure-incremental-refresh)

> ご使用のデータセットでは新しいデータポイントが定期的にチェックされます。新しいデータポイントがあった場合、プロジェクトの新しいタスクとして追加されます。

![増分更新の構成](./assets/images/AML-Text-Data-Labeling-00005.png)

##### 5.2.1.5. [ラベル カテゴリの追加](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#specify-label-categories)

- > 単純なリストを作成するには、[+ ラベル カテゴリの追加] を選択して各ラベルを作成します。
- > 異なるグループにラベルを作成するには、[+ ラベル カテゴリの追加] を選択して最上位レベルのラベルを作成します。 次に、各最上位レベルの下にある + を選択して、そのカテゴリの次のレベルのラベルを作成します。 任意のグループに対して最大 6 つのレベルを作成できます。
- ラベルの一括編集もできます。区切り記号として コンマ, タブ, 改行, コロン, セミコロン のいずれかを指定します。

![ラベル カテゴリの追加1](./assets/images/AML-Text-Data-Labeling-00006.png)

![ラベル カテゴリの追加2](./assets/images/AML-Text-Data-Labeling-00007.png)

![ラベル カテゴリの追加3](./assets/images/AML-Text-Data-Labeling-00008.png)

![ラベル カテゴリの追加4](./assets/images/AML-Text-Data-Labeling-00009.png)

##### 5.2.1.6. オプション: [ラベル付けの手順の説明](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#describe-the-text-labeling-task)

> 手順は、人間のラベラーがタスクを理解しようとするときに使用されます。ラベルの明確な定義とサンプルを指定すると、最適な結果が得られます。

![ラベル付けの手順の説明](./assets/images/AML-Text-Data-Labeling-00010.png)

##### 5.2.1.7. オプション: [ラベル付けの品質管理 (プレビュー)](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#quality-control-preview)

- 複数のラベラーの合意によるラベル付け。
- > 最小ラベラー: そのアセットのラベル付けをした、ラベル付け担当者 (Labelers) の最少人数は合意されているものと考えられています。1〜50 人。
- > 最大ラベラー: 個別の資産にラベルを付けることができるラベラーの最大数。1〜50 人。
- > 項目がラベラーの最大数に送られても合意に達しない場合、その状態は `Needs Review` になり、プロジェクト所有者が項目のラベル付けの責任を持つことになります。
- > 注意: インスタンスのセグメント化プロジェクトでは、合意ラベル付けを使用できません。
- > プロジェクトの開始後にこれらの設定を変更することはできません。

![ラベル付けの品質管理 (プレビュー)](./assets/images/AML-Text-Data-Labeling-00011.png)

##### 5.2.1.8. オプション: [ML によるラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#use-ml-assisted-data-labeling)

- > ラベラーがレビューするために、ラベル付け前のデータに対してモデルをトレーニングする ML Assist によるラベル付けを有効にすることにより、ラベル付けプロジェクトを高速化します。
- 支援付き機械学習ラベル付けは、(画像のラベル付けと異なり) 単一のフェーズで構成されます。
  > - [事前ラベル付け](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#pre-labeling)
- コンピューティング先: 既定の使用 または カスタマイズ
  - > 既定の使用: このオプションでは、既定のラベル付けコンピューティング クラスターが既に存在する場合はそれが使用され、それ以外の場合は、支援支援付き機械学習ラベル付けを使用するために、既定のコンピューティング クラスターが作成されます。[カスタマイズ] オプションを選択して、カスタム コンピューティング クラスターを選択または作成することもできます。
  - > カスタマイズ: GPU コンピューティング クラスターの選択 または 作成

![ML によるラベル付け1](./assets/images/AML-Text-Data-Labeling-00012.png)

![ML によるラベル付け2](./assets/images/AML-Text-Data-Labeling-00013.png)

![ML によるラベル付け3](./assets/images/AML-Text-Data-Labeling-00014.png)

![ML によるラベル付け3](./assets/images/AML-Text-Data-Labeling-00015.png)

> 支援付き機械学習ラベル付けは、いくつかの項目がラベル付けされた後、自動的に開始します。 この自動しきい値は、プロジェクトによって異なります。 ただし、ラベル付けされたデータがプロジェクトに含まれていれば、支援付き機械学習トレーニングの実行を手動で開始できます。


### 5.3. ラベル付けプロジェクトの実行と監視

基本的に [画像のラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#run-and-monitor-the-project) と [テキストのラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#run-and-monitor-the-project) とで共通です。

#### 5.3.1. ダッシュボードでの進行状況の表示

[画像のラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#dashboard)

![labeling-dashboard](./assets/images/labeling-dashboard.png)

[テキストのラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#dashboard)

![text-labeling-dashboard](./assets/images/text-labeling-dashboard.png)

> 進行状況グラフには、ラベル付けされた項目、スキップされた項目、レビューが必要な項目、またはまだそれが行われていない項目の数が表示されます。

> グラフの下に、完了したタスクのラベルの分布が表示されます。 プロジェクトの種類によっては、1 つの項目に複数のラベルを付けることができます。 したがって、ラベルの合計数が項目の合計数を超える場合があります。
> 
> また、ラベラーの分布と、ラベル付けした項目の数も表示されます。

> ML によるラベル付けを有効にした場合は、下にスクロールして、ML によるラベル付けの状態を確認することができます。

#### 5.3.2. ラベル付けされたデータと合意ラベルの確認

> [データ] タブでは、データセットを表示して、ラベル付けされたデータを確認できます。 ラベルを表示するには、ラベル付けされたデータをスクロールします。 間違ってラベル付けされたデータが表示された場合は、それを選んで [拒否] を選ぶことで、ラベルを削除し、データをラベルなしのキューに戻すことができます。

[画像のラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#data-tab)

![select-filters](./assets/images/select-filters.png)

[テキストのラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#data)

![text-labeling-select-filter](./assets/images/text-labeling-select-filter.png)

共通

![select-need-review](./assets/images/select-need-review.png)

[画像のラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#data-tab)

![consensus-dropdown](./assets/images/consensus-dropdown.png)

[テキストのラベル付けプロジェクト](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#data)

![text-labeling-consensus-dropdown](./assets/images/text-labeling-consensus-dropdown.png)


#### 5.3.3. [詳細の表示と変更](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#details-tab)

> プロジェクトの詳細を表示し、変更します。 このタブでは、次のことができます。
> * プロジェクトの詳細と入力データセットを表示する
> * 一定の間隔での増分更新を有効または無効にするか、即時更新を要求する
> * プロジェクトでのラベル付きの出力を格納するために使用するストレージ コンテナーの詳細を表示する
> * プロジェクトにラベルを追加する
> * ラベルに付ける指示を編集する
> * 支援付き機械学習ラベル付けの設定を変更し、ラベル付けタスクを開始する


### 5.4. [ラベル付けツールの使い方](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-label-data#label-text)

* [画像分類タスク](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-label-data#image-tasks)
* [テキスト分類タスク](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-label-data#label-text)


### 5.5. [ラベルの追加](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#add-new-labels-to-a-project)

![add-label](./assets/images/add-label.png)


### 5.6. ラベルのエクスポート

#### 5.6.1. [画像ラベルのエクスポート](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-image-labeling-projects#export-the-labels)

> 画像ラベルは以下としてエクスポートできます。
> * COCO 形式。 COCO ファイルは、Azure Machine Learning ワークスペースの既定の BLOB ストアにある Labeling/export/coco 内のフォルダーに作成されます。
> * ラベル付き Azure Machine Learning データセット。

> エクスポートした Azure Machine Learning データセットには、Machine Learning の [データセット] セクションでアクセスします。

![exported-dataset](./assets/images/exported-dataset.png)

> データセットの詳細ページには、Python からラベルにアクセスするためのサンプル コードも表示されます。

> ラベル付きデータを Azure Machine Learning データセットにエクスポートした後、[AutoML を使って、ラベル付きデータでトレーニングされた Computer Vision モデルを作成できます](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-auto-train-image-models?tabs=cli#training-and-validation-data)。

#### 5.6.2. [テキストラベルのエクスポート](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-text-labeling-projects#export-the-labels)

> テキスト固有表現認識以外のすべての種類のプロジェクトでは、次をエクスポートできます。
> * CSV ファイル。 Azure Machine Learning ワークスペースにより、Labeling/export/csv 内のフォルダーに CSV ファイルが作成されます。
> * [ラベル付き Azure Machine Learning データセット](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-use-labeled-dataset)。
> 
> テキスト固有表現認識の場合、次をエクスポートできます。
> * [ラベル付き Azure Machine Learning データセット (v1)](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-use-labeled-dataset)。
> * CoNLL ファイル。 このエクスポートでは、コンピューティング リソースを割り当てる必要があります。 エクスポート プロセスはオフラインで実行され、実験の実行の一環としてファイルが生成されます。 ファイルをダウンロードする準備が整うと、右上に通知が表示されます。 その通知を選択すると、ファイルへのリンクが表示されます。


### 5.7. [ラベル付けのアウトソーシング](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-outsource-data-labeling)

1. [ベンダー選定](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-outsource-data-labeling#review)
2. [契約](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-outsource-data-labeling#enter-into-a-contract)
3. [アクセスの有効化](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-outsource-data-labeling#enable-access)

> 重要: ラベル付け会社とお客様によるやり取りのすべての側面 (範囲、品質、スケジュール、価格に関する問題を含むがこれに限定されない) については、Microsoft ではなくお客様が責任を負うものとします。


---


## 6. [データ資産 (データセット) のバージョン管理と追跡](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-version-track-datasets)

![データ資産のバージョン管理と追跡1](./assets/images/AML-Data-version-tracking-00001.png)

![データ資産のバージョン管理と追跡2](./assets/images/AML-Data-version-tracking-00002.png)

![データ資産のバージョン管理と追跡3](./assets/images/AML-Data-version-tracking-00003.png)

![データ資産のバージョン管理と追跡4](./assets/images/AML-Data-version-tracking-00004.png)

[データ資産の作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-data-assets?tabs=cli) で、以下のように説明しました。

> Azure ML データ資産は、Web ブラウザーのブックマーク (お気に入り) に似ています。 最も頻繁に使用されるデータを指す長いストレージ パス (URI) を覚える代わりに、データ資産を作成し、フレンドリ名を使ってその資産にアクセスできます。

データ資産のバージョンについても、そのときの状態に対するブックマークのようなイメージになります。

---


## 7. [データ ドリフトの監視](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets)

> Azure Machine Learning [データセット モニター](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets#dataset-monitors) (プレビュー) を使用すると、次のことを実行できます。
> * [データのドリフト](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets#what-is-data-drift)を分析して、時間の経過と共にどのように変化するかを把握する。
> * モデル データを監視して、トレーニング用データセットと供給データセットの違いを確認する。 デプロイされたモデルからモデル データを収集することから始めます。
> * 新しいデータを監視して、[ベースライン データセットとターゲット データセット](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets#baseline-and-target-datasets)の違いを確認する。
> * データの特徴をプロファイリングして、[時間の経過と共に統計的な特性がどのように変化するかを追跡](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets#understand-data-drift-results)する。
> * [データ ドリフトに関するアラート](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-monitor-datasets#metrics-alerts-and-events)を設定して、潜在的な問題を早期に警告する。
> * 非常に多くのドリフトがデータに発生したと判断した場合に、 新しいバージョンのデータセットを作成 する。
> * モニターの作成には、Azure Machine Learning のデータセットが使用されます。**データセットには timestamp 列が含まれている必要があります**。

データセット モニターの作成ステップは以下の通りです。
1. ターゲット データセットの選択
2. ベースライン データセットの選択
3. モニターの設定


---


## 8. データ準備の効率化

Azure の各種サービスを組み合わせることで、データの準備を効率化することができます。よく用いられるサービスは以下の通りです。

| # | サービス | 主な用途 |
| --- | --- | --- |
| 1 | [Azure Event Hubs](https://azure.microsoft.com/ja-jp/products/event-hubs)<br />または<br />[Azure IoT Hub](https://azure.microsoft.com/ja-jp/products/iot-hub) | データのキューイング |
| 2 | [Azure Stream Analytics](https://azure.microsoft.com/ja-jp/products/stream-analytics) | キューからのデータ取得と加工 |
| 3 | [Azure Data Factory](https://azure.microsoft.com/ja-jp/products/data-factory)<br />または<br />[Azure Synapse Analytics](https://azure.microsoft.com/ja-jp/products/synapse-analytics/) Pipelines | [ETL](https://learn.microsoft.com/ja-jp/azure/architecture/data-guide/relational-data/etl#extract-transform-and-load-etl-process) または [ELT](https://learn.microsoft.com/ja-jp/azure/architecture/data-guide/relational-data/etl#extract-load-and-transform-elt) |
| 4 | [Azure Cosmos DB](https://azure.microsoft.com/ja-jp/products/cosmos-db) | [NoSQL データベース](https://learn.microsoft.com/ja-jp/dotnet/architecture/cloud-native/relational-vs-nosql-data) |

[![Azure Synapse を使用した分析のエンド ツー エンド](./assets/images/azure-analytics-end-to-end.png)](./assets/images/azure-analytics-end-to-end.png)

引用元: [Azure Synapse を使用した分析のエンド ツー エンド - Azure Architecture Center | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/architecture/example-scenario/dataplate2e/data-platform-end-to-end?tabs=portal)

---


## 9. ラーニング

| #   | モジュール | 所要時間 |
| ---:| -------- | ------- |
| 1 | [機械学習用のデータの概要](https://learn.microsoft.com/ja-jp/training/modules/introduction-to-data-for-machine-learning/) | 45 分 |
| 2 | [Azure Machine Learning でデータを使用できるようにする](https://learn.microsoft.com/ja-jp/training/modules/make-data-available-azure-machine-learning/) | 39 分 |
| 3 | [Azure Machine Learning でのデータの操作](https://learn.microsoft.com/ja-jp/training/modules/work-with-data-in-aml/) | 45 分 |
| 4 | [Azure Machine Learning データ ラベル付けツールを使用してラベル付けされたデータセットを作成する](https://learn.microsoft.com/ja-jp/training/modules/create-labeled-dataset-using-azure-machine-learning-data-labeling-tools/)| 30 分 |
| 5 | [Azure Machine Learning を使用してデータ ドリフトを監視する](https://learn.microsoft.com/ja-jp/training/modules/monitor-data-drift-with-azure-machine-learning/) | 42 分|
| 6 | [Azure でのデータ ストレージ手法を選択する](https://learn.microsoft.com/ja-jp/training/modules/choose-storage-approach-in-azure/) | 30 分 |
| 7 | [Azure ストレージ サービスについて](https://learn.microsoft.com/ja-jp/training/modules/azure-storage-fundamentals/) | 27 分 |
| 8 | [Azure Storage アカウントの作成](https://learn.microsoft.com/ja-jp/training/modules/create-azure-storage-account/) | 30 分 |
| 9 | [Azure Blob Storage の構成](https://learn.microsoft.com/ja-jp/training/modules/configure-blob-storage/) | 36 分 |
| 10 | [Azure Blob Storage を調べる](https://learn.microsoft.com/ja-jp/training/modules/explore-azure-blob-storage/) | 31 分 |
| 11 | [Azure Blob Storage のライフサイクルを管理する](https://learn.microsoft.com/ja-jp/training/modules/manage-azure-blob-storage-lifecycle/) | 21 分 |
| 12 | [Azure Storage Explorer を使用してデータをアップロード、ダウンロード、管理する](https://learn.microsoft.com/ja-jp/training/modules/upload-download-and-manage-data-with-azure-storage-explorer/) | 37 分 |
| 13 | [複数のプロトコルを使用して Azure Blob Storage からデータにアクセスする](https://learn.microsoft.com/ja-jp/training/modules/access-data-azure-blob-storage-multiple-protocols/) | 36 分 |
| 14 | [Azure Storage へのアプリの接続](https://learn.microsoft.com/ja-jp/training/modules/connect-an-app-to-azure-storage/) | 1 時間 5 分 |
| 15 | [Azure Blob Storage の使用](https://learn.microsoft.com/ja-jp/training/modules/work-azure-blob-storage/) | 33 分 |
| 16 | [Azure Blob ストレージを使用してアプリケーション データを格納する](https://learn.microsoft.com/ja-jp/training/modules/store-app-data-with-azure-blob-storage/) | 50 分 |
| 17 | [Azure Blob Storage のパフォーマンス指標を分析する](https://learn.microsoft.com/ja-jp/training/modules/analyze-azure-blob-storage-performance-indicators/) | 46 分 |
| 18 | [Azure Blob Storage コンテナーからメトリックを収集する](https://learn.microsoft.com/ja-jp/training/modules/gather-metrics-blob-storage/) | 1 時間 1 分 |
| 19 | [Azure Storage の監視、診断、トラブルシューティング](https://learn.microsoft.com/ja-jp/training/modules/monitor-diagnose-and-troubleshoot-azure-storage/) | 41 分 |
| 20 | [Blob Storage アプリと ETag および BLOB リースでコンカレンシーをサポートする](https://learn.microsoft.com/ja-jp/training/modules/support-concurrency-blob-storage/) | 50 分 |
| 21 | [Azure Blob Storage を使用してコストを最適化する](https://learn.microsoft.com/ja-jp/training/modules/optimize-your-cost-azure-blob-storage/) | 45 分 |
| 22 | [Azure Data Lake Storage の概要](https://learn.microsoft.com/ja-jp/training/modules/intro-to-azure-data-lake-storage/) | 34 分 |
| 23 | [非リレーショナルデータ用にデータ ストレージ ソリューションを設計する](https://learn.microsoft.com/ja-jp/training/modules/design-data-storage-solution-for-non-relational-data/) | 33 分 |


| #   | ラーニング パス | 所要時間 |
| ---:| ------------ | ------- |
| 1 | [Azure Machine Learning でのデータの操作](https://learn.microsoft.com/ja-jp/training/paths/work-data-azure-machine-learning/) | 39 分 |
| 2 | [AZ-104:Azure でのストレージの実装と管理](https://learn.microsoft.com/ja-jp/training/paths/az-104-manage-storage/) | 4 時間 16 分 |
| 3 | [Azure にデータを格納する](https://learn.microsoft.com/ja-jp/training/paths/store-data-in-azure/) | 3 時間 40 分 |
| 4 | [Azure Data Lake Storage Gen2 を使用した大規模なデータ処理](https://learn.microsoft.com/ja-jp/training/paths/data-processing-with-azure-adls/) | 1 時間 50 分 |


---


## 10. 参考リンク

* [ストレージ アカウントの概要](https://learn.microsoft.com/ja-jp/azure/storage/common/storage-account-overview)
* [ストレージ アカウントを作成する](https://learn.microsoft.com/ja-jp/azure/storage/common/storage-account-create?tabs=azure-portal)
* [Azure Blob Storage の概要](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-blobs-introduction)
* [Azure Data Lake Storage Gen2](https://learn.microsoft.com/ja-jp/azure/storage/blobs/data-lake-storage-introduction)
* [データ レイクとは](https://learn.microsoft.com/ja-jp/azure/architecture/data-guide/scenarios/data-lake)
* [Azure でのビッグ データ ストレージ テクノロジの選択](https://learn.microsoft.com/ja-jp/azure/architecture/data-guide/technology-choices/data-storage)
* [データ ストア モデルについて](https://learn.microsoft.com/ja-jp/azure/architecture/guide/technology-choices/data-store-overview)
* [アプリケーションの Azure データ ストアを選択する](https://learn.microsoft.com/ja-jp/azure/architecture/guide/technology-choices/data-store-decision-tree)
* [データ ストアの選択条件](https://learn.microsoft.com/ja-jp/azure/architecture/guide/technology-choices/data-store-considerations)
* [ストレージ オプションを確認する](https://learn.microsoft.com/ja-jp/azure/cloud-adoption-framework/ready/considerations/storage-options)
