###### Azure Machine Learning 入門 (L100)

# 1. イントロダクション

- [1. イントロダクション](#1-イントロダクション)
  - [1. アーキテクチャ](#1-アーキテクチャ)
  - [2. 使い方](#2-使い方)
  - [3. 概念](#3-概念)
    - [3.1. Azure Machine Learning v2 (現行) と v1](#31-azure-machine-learning-v2-現行-と-v1)
    - [3.2. リソース](#32-リソース)
      - [3.2.1. ワークスペース](#321-ワークスペース)
      - [3.2.2. コンピューティング](#322-コンピューティング)
        - [3.2.2.1. コンピューティング インスタンス](#3221-コンピューティング-インスタンス)
        - [3.2.2.2. コンピューティング クラスター](#3222-コンピューティング-クラスター)
        - [3.2.2.3. コンピューティング ターゲット](#3223-コンピューティング-ターゲット)
      - [3.2.3. データストア](#323-データストア)
    - [3.3. アセット](#33-アセット)
      - [3.3.1. 環境](#331-環境)
        - [3.3.1.1. キュレーション環境](#3311-キュレーション環境)
        - [3.3.1.2. カスタム環境 (ユーザー管理環境)](#3312-カスタム環境-ユーザー管理環境)
        - [3.3.1.3. システム管理環境](#3313-システム管理環境)
      - [3.3.2. 実験](#332-実験)
      - [3.3.3. データ および データ資産(v2)・データセット(v1)](#333-データ-および-データ資産v2データセットv1)
      - [3.3.4. モデル](#334-モデル)
      - [3.3.5. パイプライン](#335-パイプライン)
      - [3.3.6. コンポーネント](#336-コンポーネント)
      - [3.3.7. エンドポイント](#337-エンドポイント)
  - [4. 環境構築](#4-環境構築)
    - [4.1. CLI のインストールと設定](#41-cli-のインストールと設定)
    - [4.2. Python 開発環境の構築](#42-python-開発環境の構築)
      - [4.2.1. サポートされる Python のバージョン](#421-サポートされる-python-のバージョン)
    - [4.3. Visual Studio Code 拡張機能のセットアップ](#43-visual-studio-code-拡張機能のセットアップ)
  - [5. 参考リンク](#5-参考リンク)


---


## 1. アーキテクチャ

![Azure Machine Learning の全体像](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00035.png)


---


## 2. 使い方

![Azure Machine learning の基本的な使い方](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00036.png)


---


## 3. 概念

### 3.1. Azure Machine Learning v2 (現行) と v1

Azure Machine Learning の現行のバージョンは v2 です。 v1 に対しては基本的に後方互換性があります。

v2 の利用を進める中で、v1 の概念や機能に触れる機会があると思います。違いを確認したい場合は、以下のドキュメントを参考にしてください。

* [v1 から v2 へのアップグレード - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-migrate-from-v1)

また、v2 と v1 の違いの詳細を確認したい場合は、ドキュメントの
* リソースと資産をアップグレードする
* トレーニングをアップグレードする
* エンドポイントをアップグレードする
配下にある各種ドキュメントを参照してください。


### 3.2. [リソース](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2)

> 機械学習ワークフローを実行するために必要なセットアップ リソースやインフラストラクチャ リソース。

    リソース
    ├─ 1. ワークスペース
    ├─ 2. コンピューティング
    └─ 3. データストア


#### 3.2.1. [ワークスペース](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#workspace)

![Workspaces](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00046.png)

![Azure Machine Learning Workspace とは？](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00065.png)

> [ワークスペース](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-workspace) は、Azure Machine Learning の最上位のリソースで、Azure Machine Learning を使用するときに作成するすべての成果物を操作するための一元的な場所を提供します。 ワークスペースには、スクリプトのログ、メトリック、出力、スナップショットなど、すべてのジョブの履歴が保持されます。 ワークスペースには、データストアやコンピューティングなどのリソースへの参照が格納されます。 また、モデル、環境、コンポーネント、データ アセットなど、すべてのアセットも保持されます。

![ワークロードに応じて Workspace を構築する](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00067.png)


#### 3.2.2. [コンピューティング](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#compute)

![計算環境の種類](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00069.png)

![マネージドリソース](assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00051.png)

![Azure Machine Learning Compute Cluster](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00070.png)

> コンピューティングとは、ジョブを実行したり、エンドポイントをホストしたりする、指定されたコンピューティング リソースのことです。 Azure Machine Learning では、コンピューティングの種類として以下がサポートされています。
> 
> * **コンピューティング クラスター** - [クラウド](https://azure.microsoft.com/ja-jp/resources/cloud-computing-dictionary/what-is-the-cloud/)上に CPU または GPU コンピューティング ノードのクラスターを簡単に作成できる、マネージド コンピューティング インフラストラクチャ。
> * **[コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)** - 完全に構成および管理される、クラウド上の開発環境。 このインスタンスは、トレーニングまたは推論コンピューティングとして、開発やテストに使用できます。 これは、クラウド上の[仮想マシン](https://azure.microsoft.com/ja-jp/resources/cloud-computing-dictionary/what-is-a-virtual-machine/)のようなものです。
> * **[Kubernetes クラスター](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-attach-kubernetes-anywhere)** - トレーニング済みの機械学習モデルを [Azure Kubernetes Service](https://azure.microsoft.com/ja-jp/products/kubernetes-service/) にデプロイするために使用されます。 Azure ML ワークスペースから [Azure Kubernetes Service (AKS) クラスター](https://learn.microsoft.com/ja-jp/azure/aks/concepts-clusters-workloads#kubernetes-cluster-architecture)を作成するか、既存の AKS クラスターをアタッチすることができます。
> * **アタッチ型コンピューティング** - 独自のコンピューティング リソースをワークスペースにアタッチし、トレーニングと推論に使用できます。

##### 3.2.2.1. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-manage-compute-instance)

> コンピューティング インスタンスは、クラウド内で完全に構成され管理される自分の開発環境として使用します。 開発とテストの場合、このインスタンスを[トレーニング コンピューティング ターゲット](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-target#training-compute-targets)として使うこともできます。 コンピューティング インスタンスは複数のジョブを並列に実行でき、ジョブ キューを備えています。 開発環境であるため、コンピューティング インスタンスをワークスペース内の他のユーザーと共有することはできません。

##### 3.2.2.2. [コンピューティング クラスター](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-attach-compute-cluster)

> Azure Machine Learning コンピューティング クラスターは、シングルノードまたはマルチノードのコンピューティングを簡単に作成できるマネージド コンピューティング インフラストラクチャです。 コンピューティング クラスターは、ワークスペース内の他のユーザーと共有できるリソースです。 コンピューティングはジョブが送信されると自動的にスケールアップされ、Azure 仮想ネットワークに配置できます。 コンピューティング クラスターでは、仮想ネットワークでもパブリック IP なしのデプロイはサポートされません。 

##### 3.2.2.3. [コンピューティング ターゲット](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-target)

> "コンピューティング ターゲット" とは、トレーニング スクリプトを実行したり、サービスのデプロイをホストしたりする、指定されたコンピューティング リソースまたは環境のことです。 この場所は、ローカル コンピューターでも、クラウドベースのコンピューティング リソースでもかまいません。 コンピューティング ターゲットを使用すると、コードを変更しなくても、後でコンピューティング環境を容易に変更できます。

![Compute Targets](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00052.png)

![デプロイメントの選択肢](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00076.png)


#### 3.2.3. [データストア](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#datastore)

![Datasets and Data Stores](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00047.png)

> Azure Machine Learning データストアでは、Azure のデータ ストレージへの接続情報が安全に保持されるため、ご自身のスクリプトでそのコードを書く必要はありません。 データストアを登録および作成すると、ストレージ アカウントに簡単に接続し、基になるストレージ サービスのデータにアクセスできます。 [CLI v2](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-configure-cli?tabs=public) と [SDK v2](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-workspace?tabs=python) では、次の種類の[クラウドベース ストレージ](https://azure.microsoft.com/ja-jp/resources/cloud-computing-dictionary/what-is-cloud-storage/) サービスがサポートされています。
> 
> * [Azure BLOB](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-blobs-introduction) [コンテナー](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-blobs-introduction#containers)
> * [Azure ファイル共有](https://learn.microsoft.com/ja-jp/azure/storage/files/storage-how-to-use-files-portal?tabs=azure-portal)
> * [Azure Data Lake](https://learn.microsoft.com/ja-jp/azure/data-lake-store/data-lake-store-overview)
> * [Azure Data Lake Gen2](https://learn.microsoft.com/ja-jp/azure/storage/blobs/data-lake-storage-introduction)


### 3.3. [アセット](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2)

> Azure ML コマンドを使用して、またはトレーニング/スコアリングの実行の一部として作成されます。 アセットはバージョン管理され、Azure ML ワークスペースに登録できます。

    アセット
    ├─ 1. 環境
    ├─ 2. 実験
    ├─ 3. データ および データ資産(v2)・データセット(v1)
    ├─ 4. モデル
    ├─ 5. パイプライン
    ├─ 6. コンポーネント
    └─ 7. エンドポイント

#### 3.3.1. [環境](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#environment)

![Azure ML Environments](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00054.png)

> [Azure Machine Learning 環境](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-environments) は、[機械学習](https://azure.microsoft.com/ja-jp/resources/cloud-computing-dictionary/what-is-machine-learning-platform/)タスクが行われる環境をカプセル化したものです。 そこでは、トレーニングとスコアリングのスクリプトに関連する、ソフトウェア パッケージ、環境変数、およびソフトウェア設定を指定します。 環境は、Machine Learning ワークスペース内で管理およびバージョン管理されるエンティティです。 [環境を使用する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-environments-v2?tabs=cli)ことで、さまざまなコンピューティング先で再現、監査、移植できる機械学習ワークフローを実現できます。

> 環境は、キュレーション、ユーザー管理、システム管理の 3 つのカテゴリに大別できます。

##### 3.3.1.1. キュレーション環境

> キュレートされた環境は Azure Machine Learning から提供され、既定でお使いのワークスペースで利用できます。 これらには、現状のまま使用する目的で、Python のパッケージと設定のコレクションが含まれていて、さまざまな機械学習フレームワークの使用を開始する助けとなります。 これらの事前に作成された環境を利用すると、デプロイ時間の短縮も可能です。 完全な一覧については、[キュレーションされた環境に関する記事](https://learn.microsoft.com/ja-jp/azure/machine-learning/resource-curated-environments)を参照してください。

##### 3.3.1.2. カスタム環境 (ユーザー管理環境)

> カスタム環境では、環境のセットアップはお客様の責任となります。 コンピューティングでトレーニングまたはスコアリング スクリプトに必要なパッケージとその他の依存関係を必ずインストールしてください。 Azure ML では以下のものを使用して独自の環境を作成できます
> 
> * [Docker](https://docs.docker.jp/get-started/overview.html) [イメージ](https://docs.docker.jp/get-started/overview.html#id16)
> * さらにカスタマイズするための [conda](https://ja.wikipedia.org/wiki/Anaconda_(Python%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)) YAML を含んだ基本 Docker イメージ
> * Docker ビルドのコンテキスト

##### 3.3.1.3. システム管理環境

> Python 環境を [Conda](https://conda.io/docs/) で自動的に管理したいときは、システム管理環境を使用します。 新しい Conda 環境は、Docker のベース イメージ上の Conda 仕様から具体化されています。


#### 3.3.2. 実験

![Azure ML Runs and Experiments](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00055.png)


#### 3.3.3. [データ](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#data) および データ資産(v2)・データセット(v1)

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

![Datasets and Data Stores](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00047.png)

![Datasets](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00053.png)

https://learn.microsoft.com/ja-jp/azure/machine-learning/migrate-to-v2-assets-data

> [V1](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/concept-azure-machine-learning-architecture) では、AzureML データセットを [Filedataset](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-create-register-datasets#filedataset) または [Tabulardataset](https://learn.microsoft.com/ja-jp/azure/machine-learning/v1/how-to-create-register-datasets#tabulardataset) にすることができます。 [V2](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-migrate-from-v1) では、AzureML データ資産を uri_folder、uri_file、mltable のいずれかにすることができます。 [Filedataset を uri_folder および uri_file に、Tabulardataset を mltable に概念的に対応させることができます](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-migrate-from-v1#data-datasets-in-v1)。
> 
> * URI (uri_folder、uri_file) - Uniform Resource Identifier。ローカル コンピューターまたはクラウド上のストレージの場所への参照であり、これにより、ジョブ内のデータに簡単にアクセスできるようになります。
> * MLTable - 表形式データのスキーマ定義を抽象化し、データのコンシューマーがテーブルを Pandas/Dask/Spark データフレームに具体化しやすくする方法。

すなわち、 v1 のデータセットは集合的な概念だったものが、 v2 ではデータ資産の名の下に、[データ型](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data#data-types)として表現されるようになったと理解してください。

v2 のデータ資産は、v1 のデータセットに対して下位互換性を持っています。

> V2 ジョブで V1 データセットを使用すると、次のように V2 の型に自動的にマップされます。
> * V1 FileDataset = V2 Folder (uri_folder)
> * V1 TabularDataset = V2 Table (mltable)

![データセットの管理](./assets/images/Azure-Machine-Learning-%E3%81%A8-Cognitive-Search-%E6%A6%82%E8%A6%81_1280x720px-00008.png)

![Dataset Monitor](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00066.png)


#### 3.3.4. [モデル](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#model)

![Azure ML Models and Model Registry](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00056.png)

> Azure 機械学習モデルは、機械学習モデルと対応するメタデータを表すバイナリ ファイルで構成されます。 モデルは、ローカルまたはリモートのファイルやディレクトリから作成できます。 リモートの場所としては、`https`、`wasbs`、および`azureml` がサポートされています。 作成されたモデルは、指定された名前とバージョンでワークスペース内で追跡されます。 Azure ML では、モデルのストレージ形式として次の 3 種類がサポートされています。
> 
> * `custom_model`
> * `mlflow_model`
> * `triton_model`

![推論環境のモデル更改](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00078.png)


#### 3.3.5. [パイプライン](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-ml-pipelines)

![Azure ML Pipelines](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00057.png)

![Machine Learning Pipeline](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00062.png)

> Azure Machine Learning パイプラインは、独立して実行できる完全な機械学習タスクのワークフローです。 Azure Machine Learning パイプラインは、機械学習モデルを生成する上でのベスト プラクティスを標準化するのに役立ち、チームが規模に応じて実行できるようにし、モデル構築の効率を向上させます。


#### 3.3.6. [コンポーネント](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#component)

> Azure Machine Learning コンポーネントは、機械学習[パイプライン](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-ml-pipelines)で 1 つのステップを実行する自己格納型のコードです。 コンポーネントは、高度な機械学習パイプラインの構成要素です。 コンポーネントは、データ処理、モデル トレーニング、モデル スコアリングなどのタスクを実行できます。 コンポーネントは関数に類似しており、名前とパラメーターを持ち、入力を予想し、出力を返します。


#### 3.3.7. [エンドポイント](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-endpoints)

![Web Services](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00062.png)

> 機械学習モデルをトレーニングした後、他のユーザーがそのモデルを使用して推論を実行できるようにするために、それをデプロイする必要があります。 Azure Machine Learning では、エンドポイントとデプロイを使用して、そうすることができます。
> 
> この文脈でのエンドポイントは、クライアントで要求 (入力データ) を送信し、トレーニングされたモデルの推論 (スコアリング) 出力を受信するためのインターフェイスを提供する HTTPS パスになります。

> デプロイは、実際の推論を実行するモデルをホストするのに必要なリソースのセットです。
> 
> 1 つのエンドポイントに複数のデプロイを含めることができます。 

> Azure Machine Learning では、[オンライン エンドポイント](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-endpoints#what-are-online-endpoints)と[バッチ エンドポイント](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-endpoints#what-are-batch-endpoints)の両方を実装できます。

![Azure ML Managed Endpoints](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00065.png)

---

## 4. 環境構築

    環境構築
    ├─ 1. CLI のインストールと設定
    ├─ 2. Python 開発環境の構築
    └─ 3. Visual Studio Code 拡張機能のセットアップ


### 4.1. CLI のインストールと設定

https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-configure-cli?tabs=public


### 4.2. Python 開発環境の構築

https://learn.microsoft.com/ja-jp/python/api/overview/azure/ai-ml-readme?view=azure-python

#### 4.2.1. サポートされる Python のバージョン

* [Azure Machine Learning Python SDK v2](https://learn.microsoft.com/ja-jp/python/api/overview/azure/ai-ml-readme?view=azure-python)
  * Python 3.7 以上 (3.7、3.8、3.9、3.10)
* [Azure Machine Learning Python SDK v1](https://learn.microsoft.com/ja-jp/python/api/overview/azure/ml/install?view=azure-ml-py)
  * Python 3.7 以上
  * 但し azureml-automl パッケージは 3.7 または 3.8 のみ


### 4.3. Visual Studio Code 拡張機能のセットアップ

https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-setup-vs-code


---


## 5. 参考リンク

* [Azure 用語集 - Azure 辞書 | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/azure-glossary-cloud-terminology)
* [クラウド コンピューティングの用語 | Microsoft Azure](https://azure.microsoft.com/ja-jp/resources/cloud-computing-dictionary/)
* [Azure 基礎の概念 - Cloud Adoption Framework | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/cloud-adoption-framework/ready/considerations/fundamental-concepts)
* [環境イメージのトラブルシューティング - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-troubleshoot-environments)
