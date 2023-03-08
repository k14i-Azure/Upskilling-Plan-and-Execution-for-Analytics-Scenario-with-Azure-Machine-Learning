###### Azure Machine Learning 入門 (L100)

# 5. CLI (Azure Machine Learning CLI extension)

- [5. CLI (Azure Machine Learning CLI extension)](#5-cli-azure-machine-learning-cli-extension)
  - [1. 概要](#1-概要)
  - [2. 特徴](#2-特徴)
  - [3. 前提](#3-前提)
  - [4. 使用例](#4-使用例)
    - [4.1. 前提](#41-前提)
      - [4.1.1. 豆知識](#411-豆知識)
    - [4.2. インストールと設定](#42-インストールと設定)
    - [4.3. リソースの作成](#43-リソースの作成)
      - [4.3.1. 参考: リソースグループの作成](#431-参考-リソースグループの作成)
      - [4.3.2. 参考: Azure Blob Storage の作成](#432-参考-azure-blob-storage-の作成)
      - [4.3.3. ワークスペースの作成](#433-ワークスペースの作成)
      - [4.3.4. コンピューティング の作成](#434-コンピューティング-の作成)
    - [4.4. モデルのトレーニング](#44-モデルのトレーニング)
      - [4.4.1. トレーニングジョブの送信](#441-トレーニングジョブの送信)
      - [4.4.2. ジョブの情報取得](#442-ジョブの情報取得)
    - [4.5. モデルの登録](#45-モデルの登録)
    - [4.6. リソースの削除](#46-リソースの削除)
      - [4.6.1. ワークスペースの削除](#461-ワークスペースの削除)
      - [4.6.2. リソースグループの削除](#462-リソースグループの削除)
  - [5. 無料のオンライン トレーニング](#5-無料のオンライン-トレーニング)
  - [6. 参考リンク](#6-参考リンク)


---


## 1. 概要

> [Azure CLI](https://learn.microsoft.com/ja-jp/cli/azure/what-is-azure-cli) に対する ml 拡張機能は、Azure Machine Learning の拡張インターフェイスです。 これにより、コマンド ラインからモデルをトレーニングおよびデプロイできます。また、モデルのライフサイクルを追跡しながらデータ サイエンスのスケールアップとスケールアウトを加速する機能もあります。


---


## 2. 特徴

* Azure CLI の拡張機能として動作する。そのため、Azure CLI とシームレスに使うことができる。
* 他のコマンドラインツールと組み合わせてスクリプトを作ることができる。
* リソースグループの削除も組み合わせることで、 [Infrastructure as Code](https://learn.microsoft.com/ja-jp/devops/deliver/what-is-infrastructure-as-code) を簡単に実現することができる。
* 複雑な処理やエラー処理をさせる場合は、プログラミング言語を使うことができる SDK の方が有利。


---


## 3. 前提

* Azure サブスクリプションがあること
* 利用する端末に Azure CLI >=2.15.0 が[インストール](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli)されていること
  * Azure CLI は [Windows](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli-windows?tabs=azure-cli), [macOS](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli-macos), [Linux](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli-linux?pivots=apt) ([WSL](https://learn.microsoft.com/ja-jp/windows/wsl/about)含む), [Docker コンテナー](https://learn.microsoft.com/ja-jp/cli/azure/run-azure-cli-docker), [Azure Cloud Shell](https://learn.microsoft.com/ja-jp/azure/cloud-shell/quickstart) で利用できます。


---


## 4. 使用例

### 4.1. 前提

* Windows の場合、PowerShell か コマンドプロンプトを使います。
* macOS および Linux の場合、ターミナルを使います。
* [Visual Studio Code](https://code.visualstudio.com/) の[ターミナル](https://code.visualstudio.com/docs/terminal/basics)を利用することも可能です。
* 利用する端末に git がインストールされていること
  * Windows の場合、[公式のインストーラー](https://git-scm.com/download/win)を使うか、[Git for Windows](https://gitforwindows.org/) を使ってください。
  * macOS の場合、[Homebrew](https://brew.sh/) を使うのが便利です。
  * Linux の場合、apt や yum 等、ディストリビューションごとのパッケージ管理を利用してください。
* git を使ってサンプルデータを入手していること
  * `git clone --depth 1 https://github.com/Azure/azureml-examples`


#### 4.1.1. 豆知識

コマンドライン初心者の方向けの情報です。慣れている方は読み飛ばしてください。

* `\` はエスケープ記号です。使い方の一つとして、コマンドラインやスクリプトにおいて、見た目上は改行しつつ、コマンドに対しては改行文字を無視させるために使われます。たとえば、以下の2つのコマンドは同等です。好みに応じて使い分けてください。
  * ```bash
    az group create \
        --name "<resource-group-name>" \
        --location "<location>"
    ```
  * ```bash
    az group create --name "<resource-group-name>" --location "<location>"
    ```

* コマンドには多くの場合オプションがあり、あるオプションの表記の仕方として、ロングオプションとショートオプションがあります。両方ある場合もありますし、片方しかない場合もあります。たとえば、以下の4つのコマンドは同等です。好みに応じて使い分けてください。
  * ```bash
    az group create \
        --name "<resource-group-name>" \
        --location "<location>"
    ```
  * ```bash
    az group create \
        -n "<resource-group-name>" \
        -l "<location>"
    ```
  * ```bash
    az group create \
        --name "<resource-group-name>" \
        --l "<location>"
    ```
  * ```bash
    az group create \
        --n "<resource-group-name>" \
        --location "<location>"
    ```

### 4.2. [インストールと設定](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-configure-cli?tabs=public)

```bash
az extension add -n ml
```

```bash
az account set -s "<subscription-name-or-id>"
```

```bash
az login
```


### 4.3. リソースの作成

#### 4.3.1. 参考: リソースグループの作成

```bash
az group create \
    --name "<resource-group-name>" \
    --location "<location>"
```

#### 4.3.2. 参考: [Azure Blob Storage の作成](https://learn.microsoft.com/ja-jp/azure/storage/blobs/blob-cli#create-a-container)

```bash
az storage container create \
    --name "<container-name>" \
    --account-name "<storage-account-name>" \
    --auth-mode login
```

#### 4.3.3. [ワークスペースの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-workspace-cli?tabs=createnewresources#create-a-workspace)

```bash
az ml workspace create \
    -n "<workspace-name>" \
    -g "<resource-group-name>"
```

```bash
az configure --defaults \
    workspace="<workspace-name>" \
    group="<resource-group-name>"
```

#### 4.3.4. [コンピューティング の作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-train-model?tabs=azurecli#2-create-a-compute-resource-for-training)

```bash
az ml compute create \
    -n cpu-cluster \
    --type amlcompute \
    --min-instances 0 \
    --max-instances 4
```

### 4.4. [モデルのトレーニング](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-train-model?tabs=azurecli#4-submit-the-training-job)

#### 4.4.1. トレーニングジョブの送信

教師データには、git コマンドでクローンしたリポジトリのコピーの中に含まれる `azureml-examples/cli/jobs/single-step/scikit-learn/iris/job.yml` を使用します。([ソース](https://github.com/Azure/azureml-examples/blob/main/cli/jobs/single-step/scikit-learn/iris/job.yml))

```bash
run_id=$(az ml job create -f azureml-examples/cli/jobs/single-step/scikit-learn/iris/job.yml --query name -o tsv)
```

#### 4.4.2. ジョブの情報取得

```bash
az ml job show \
    -n $run_id \
    --web
```

### 4.5. [モデルの登録](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-train-model?tabs=azurecli#register-the-trained-model)

```bash
az ml model create \
    -n sklearn-iris-example \
    -v 1 \
    -p runs:/$run_id/model \
    --type mlflow_model
```

### 4.6. リソースの削除

#### 4.6.1. [ワークスペースの削除](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-workspace-cli?tabs=createnewresources#delete-a-workspace)

```bash
az ml workspace delete \
    -n "<workspace-name>" \
    -g "<resource-group-name>"
```

#### 4.6.2. リソースグループの削除

```bash
az group delete -g "<resource-group-name>"
```

---


## 5. 無料のオンライン トレーニング

| #   | モジュール | 所要時間 |
| --- | -------- | ------- |
| 1 | [CLI を使用して Azure Machine Learning リソースを作成する (v2)](https://learn.microsoft.com/ja-jp/training/modules/create-azure-machine-learning-resources-cli-v2/) | 40 分 |
| 2 | [CLI (v2) を使用した Azure Machine Learning でのジョブの実行](https://learn.microsoft.com/ja-jp/training/modules/run-jobs-azure-machine-learning-cli-v2/) | 41 分 |
| 3 | [CLI (v2) で送信する Azure Machine Learning ジョブで MLflow を使用する](https://learn.microsoft.com/ja-jp/training/modules/use-mlflow-azure-machine-learning-jobs-submitted-cli-v2/) | 31 分 |
| 4 | [CLI を使用して Azure Machine Learning モデルをマネージド エンドポイントにデプロイする (v2)](https://learn.microsoft.com/ja-jp/training/modules/deploy-azure-machine-learning-model-managed-endpoint-cli-v2/) | 29 分 |
| 5 | [CLI (v2) を使用した Azure Machine Learning でのコンポーネントベースのパイプラインの実行](https://learn.microsoft.com/ja-jp/training/modules/run-component-based-pipelines-azure-machine-learning-cli-v2/) | 35 分 |

または

| #   | ラーニング パス | 所要時間 |
| --- | ------------ | ------- |
| 1 | [CLI を使用した Azure Machine Learning でのモデルのトレーニング (v2)](https://learn.microsoft.com/ja-jp/training/paths/train-models-azure-machine-learning-cli-v2/) | 2 時間 56 分 |


---


## 6. 参考リンク

* [Azure CLI をインストールする方法](https://learn.microsoft.com/ja-jp/cli/azure/install-azure-cli)
* [az ml](https://learn.microsoft.com/ja-jp/cli/azure/ml?view=azure-cli-latest)
* [CLI (v2) のインストールと設定](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-configure-cli?tabs=public)
* [Azure CLI を使用して Azure Machine Learning ワークスペースを管理する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-workspace-cli?tabs=createnewresources)
* [CLI & SDK (v2) を使用して Azure Machine Learning 環境を管理する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-environments-v2?tabs=cli)
* [Azure Machine Learning CLI、SDK、REST API を使用してモデルをトレーニングする](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-train-model?tabs=azurecli)
* [Azure Machine Learning CLI でコンポーネントを使用して機械学習パイプラインを作成して実行する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-component-pipelines-cli)
