###### Azure Machine Learning 入門 (L100)

# 6. SDK (Azure Machine Learning Python SDK)

- [6. SDK (Azure Machine Learning Python SDK)](#6-sdk-azure-machine-learning-python-sdk)
  - [1. 概要](#1-概要)
  - [2. 特徴](#2-特徴)
  - [3. 前提](#3-前提)
  - [4. 使用例](#4-使用例)
    - [4.1. 前提](#41-前提)
    - [4.2. インストールと認証](#42-インストールと認証)
    - [4.3. リソースの作成](#43-リソースの作成)
      - [4.3.1. 参考: リソースグループの作成](#431-参考-リソースグループの作成)
      - [4.3.2. 参考: ストレージアカウントの作成](#432-参考-ストレージアカウントの作成)
      - [4.3.3. 参考: Azure Blob Storage の作成](#433-参考-azure-blob-storage-の作成)
      - [4.3.4. ワークスペースの作成](#434-ワークスペースの作成)
      - [4.3.5. コンピューティング の作成](#435-コンピューティング-の作成)
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

https://learn.microsoft.com/ja-jp/python/api/overview/azure/ml/?view=azure-ml-py

> データ サイエンティストと AI 開発者は、Python 用 Azure Machine Learning SDK を使用して、Azure Machine Learning service で機械学習のワークフローをビルドして実行します。 Jupyter Notebook、Visual Studio Code、お気に入りの Python IDE など、任意の Python 環境でサービスと対話できます。
> 
> SDK の主な領域は次のとおりです。
> * 機械学習の実験で使用されるデータセットのライフサイクルを調査、準備、管理します。
> * 機械学習の実験を監視、ログ記録、整理するためのクラウド リソースを管理します。
> * ローカルで、または GPU アクセラレーション モデルのトレーニングなどのクラウド リソースを使用して、モデルをトレーニングします。
> * 構成パラメーターとトレーニング データを受け入れる自動機械学習を使用します。 アルゴリズムとハイパーパラメーターの設定を自動的に反復処理して、予測を実行するための最適なモデルを見つけます。
> * Web サービスをデプロイして、トレーニング済みのモデルを任意のアプリケーションで使用できる RESTful サービスに変換します。

https://learn.microsoft.com/ja-jp/python/api/overview/azure/ai-ml-readme?view=azure-python#key-concepts

> Azure Machine Learning Python SDK v2 には、スタンドアロン ローカル ジョブ、パイプライン用の再利用可能なコンポーネント、マネージド オンライン/バッチ推論など、多くの新機能が用意されています。 SDK v2 は、プラットフォームのすべての資産で一貫性と使いやすさをもたらします。 Python SDK v2 には、次の機能があります。
> * スタンドアロン ジョブの実行 - 個別の ML アクティビティをジョブとして実行します。 このジョブは、ローカルまたはクラウドで実行できます。 現在、次の種類のジョブがサポートされています。
>   * コマンド - コマンド (Python、R、Windows コマンド、Linux シェルなど) を実行します
>   * スイープ - コマンドでハイパーパラメーター スイープを実行する
> * 改善されたパイプラインを使用して複数のジョブを実行する
>   * パイプラインに結合された一連のコマンドを実行する (新規)
>   * コンポーネント - 再利用可能なコンポーネントを使用してパイプラインを実行する (新規)
> * Managed Online 推論にモデルを使用する (新規)
> * マネージド バッチ推論にモデルを使用する
> * AML リソースの管理 - ワークスペース、コンピューティング、データストア
> * AML 資産の管理 - データセット、環境、モデル
> * AutoML - さまざまな ml タスクに対してスタンドアロンの AutoML トレーニングを実行します。
>   * 分類 (表形式データ)
>   * 回帰 (表形式データ)
>   * 時系列予測 (表形式データ)
>   * 画像分類 (複数クラス) (新規)
>   * 画像分類 (複数ラベル) (新規)
>   * 画像オブジェクト検出 (新規)
>   * イメージ インスタンスのセグメント化 (新規)
>   * NLP テキスト分類 (複数クラス) (新規)
>   * NLP テキスト分類 (複数ラベル) (新規)
>   * NLP Text Named Entity Recognition (NER) (新規)


---


## 2. 特徴

* SDK は Python で実装されたモジュールのパッケージであり、Python の外部ライブラリとして利用できる。
* Python のコードに `import` することができる。複雑な処理やエラー処理、オブジェクト指向の処理やデザインパターンに基づく処理も、Python で簡単に実装することができる。
* Python で実装されたアプリケーションやシステムと統合することが容易にできる。
* コードはソフトウェアとしてテストすることができる。
* MLflow との相性が良い。
* SDK を使用したコードを Python パッケージとして配布することができる。
* ターミナルでのワンライナー的な使い方には向いていない。
* 実行環境にインストールされている Python のバージョンを SDK がサポートしているか、注意する必要がある。(SDK v1, v2 ともに Python 3.7 以上をサポートしている。)


---


## 3. 前提

* Azure サブスクリプションがあること
* 利用する端末に Python >= 3.7 がインストールされていること
  * Python 3.10 までサポートされています。


---


## 4. 使用例

### 4.1. 前提

* pip は最新にアップデートしておきます。
  * `pip install -U pip`
* 別途 [Azure SDK for Python](https://learn.microsoft.com/ja-jp/azure/developer/python/sdk/azure-sdk-overview) を[インストール](https://learn.microsoft.com/ja-jp/azure/developer/python/sdk/examples/azure-sdk-example-resource-group#2-install-the-azure-library-packages)しておきます。
  * `pip install azure-mgmt-resource azure-identity azure-mgmt-storage azure-storage-blob`


### 4.2. [インストールと認証](https://learn.microsoft.com/ja-jp/python/api/overview/azure/ai-ml-readme?view=azure-python#install-the-package)

```bash
pip install azure-ai-ml
```

```python
from azure.ai.ml import MLClient
from azure.identity import DefaultAzureCredential

ml_client = MLClient(
    DefaultAzureCredential(), subscription_id, resource_group, workspace
)
```

### 4.3. リソースの作成

#### 4.3.1. 参考: [リソースグループの作成](https://learn.microsoft.com/ja-jp/azure/developer/python/sdk/examples/azure-sdk-example-resource-group#3-write-code-to-create-a-resource-group)

```python
import os
from azure.identity import AzureCliCredential
from azure.mgmt.resource import ResourceManagementClient

credential = AzureCliCredential()
subscription_id = os.environ["AZURE_SUBSCRIPTION_ID"]
resource_client = ResourceManagementClient(credential, subscription_id)

rg_result = resource_client.resource_groups.create_or_update(
    "PythonAzureExample-rg", {"location": "centralus"}
)
print(
    f"Provisioned resource group {rg_result.name} in \
        the {rg_result.location} region"
)

rg_result = resource_client.resource_groups.create_or_update(
    "PythonAzureExample-rg",
    {
        "location": "centralus",
        "tags": {"environment": "test", "department": "tech"},
    },
)
print(f"Updated resource group {rg_result.name} with tags")
```

#### 4.3.2. 参考: [ストレージアカウントの作成](https://learn.microsoft.com/ja-jp/azure/developer/python/sdk/examples/azure-sdk-example-storage?tabs=cmd#3-write-code-to-create-storage-resources)

```python
import os, random
from azure.identity import AzureCliCredential
from azure.mgmt.resource import ResourceManagementClient
from azure.mgmt.storage import StorageManagementClient

credential = AzureCliCredential()
subscription_id = os.environ["AZURE_SUBSCRIPTION_ID"]
resource_client = ResourceManagementClient(credential, subscription_id)

RESOURCE_GROUP_NAME = "PythonAzureExample-Storage-rg"
LOCATION = "centralus"

# Step 1: Provision the resource group.

rg_result = resource_client.resource_groups.create_or_update(RESOURCE_GROUP_NAME,
    { "location": LOCATION })

print(f"Provisioned resource group {rg_result.name}")

# Step 2: Provision the storage account, starting with a management object.

storage_client = StorageManagementClient(credential, subscription_id)

STORAGE_ACCOUNT_NAME = f"pythonazurestorage{random.randint(1,100000):05}"

availability_result = storage_client.storage_accounts.check_name_availability(
    { "name": STORAGE_ACCOUNT_NAME }
)

if not availability_result.name_available:
    print(f"Storage name {STORAGE_ACCOUNT_NAME} is already in use. Try another name.")
    exit()

poller = storage_client.storage_accounts.begin_create(RESOURCE_GROUP_NAME, STORAGE_ACCOUNT_NAME,
    {
        "location" : LOCATION,
        "kind": "StorageV2",
        "sku": {"name": "Standard_LRS"}
    }
)

account_result = poller.result()
print(f"Provisioned storage account {account_result.name}")

# Step 3: Retrieve the account's primary access key and generate a connection string.

keys = storage_client.storage_accounts.list_keys(RESOURCE_GROUP_NAME, STORAGE_ACCOUNT_NAME)

print(f"Primary key for storage account: {keys.keys[0].value}")

conn_string = f"DefaultEndpointsProtocol=https;EndpointSuffix=core.windows.net;AccountName={STORAGE_ACCOUNT_NAME};AccountKey={keys.keys[0].value}"

print(f"Connection string: {conn_string}")

# Step 4: Provision the blob container in the account (this call is synchronous)

CONTAINER_NAME = "blob-container-01"
container = storage_client.blob_containers.create(RESOURCE_GROUP_NAME, STORAGE_ACCOUNT_NAME, CONTAINER_NAME, {})

print(f"Provisioned blob container {container.name}")
```

#### 4.3.3. 参考: [Azure Blob Storage の作成](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-quickstart-blobs-python?tabs=managed-identity%2Croles-azure-portal%2Csign-in-azure-cli#create-a-container)

```python
from azure.identity import DefaultAzureCredential

try:
    account_url = "https://<storageaccountname>.blob.core.windows.net"
    default_credential = DefaultAzureCredential()

    blob_service_client = BlobServiceClient(account_url, credential=default_credential)

    container_name = str(uuid.uuid4())
    container_client = blob_service_client.create_container(container_name)
except Exception as e:
    raise Exception(e)
```

#### 4.3.4. [ワークスペースの作成](https://github.com/Azure/azureml-examples/blob/main/sdk/python/resources/workspace/workspace.ipynb)

```python
import datetime
from azure.ai.ml import MLClient
from azure.ai.ml.entities import Workspace
from azure.identity import DefaultAzureCredential

subscription_id = "<SUBSCRIPTION_ID>"
resource_group = "<RESOURCE_GROUP>"

ml_client = MLClient(DefaultAzureCredential(), subscription_id, resource_group)

basic_workspace_name = "mlw-basic-prod-" + datetime.datetime.now().strftime(
    "%Y%m%d%H%M"
)

ws_basic = Workspace(
    name=basic_workspace_name,
    location="eastus",
    display_name="Basic workspace-example",
    description="This example shows how to create a basic workspace",
    hbi_workspace=False,
    tags=dict(purpose="demo"),
)

ws_basic = ml_client.workspaces.begin_create(ws_basic).result()
print(ws_basic)
```

#### 4.3.5. [コンピューティング の作成](https://github.com/Azure/azureml-examples/blob/main/sdk/python/resources/compute/compute.ipynb)

```python
import datetime
from azure.ai.ml import MLClient
from azure.ai.ml.entities import ComputeInstance, AmlCompute
from azure.identity import DefaultAzureCredential

subscription_id = "<SUBSCRIPTION_ID>"
resource_group = "<RESOURCE_GROUP>"
workspace = "<AML_WORKSPACE_NAME>"

ml_client = MLClient(
    DefaultAzureCredential(), subscription_id, resource_group, workspace
)

ci_minimal_name = "min-ci" + datetime.datetime.now().strftime("%Y%m%d%H%M")

ci_minimal = ComputeInstance(name=ci_minimal_name)
ml_client.begin_create_or_update(ci_minimal).result()
```


### 4.4. [モデルのトレーニング](https://github.com/Azure/azureml-examples/blob/main/sdk/python/jobs/single-step/scikit-learn/iris/iris-scikit-learn.ipynb)

コンピューティングに実行させるコード (ここでは [main.py](https://github.com/Azure/azureml-examples/blob/main/sdk/python/jobs/single-step/tensorflow/mnist/src/main.py)) を別途用意します。

#### 4.4.1. トレーニングジョブの送信

```python
from azure.ai.ml import MLClient
from azure.ai.ml import command
from azure.identity import DefaultAzureCredential

subscription_id = "<SUBSCRIPTION_ID>"
resource_group = "<RESOURCE_GROUP>"
workspace = "<AML_WORKSPACE_NAME>"

ml_client = MLClient(
    DefaultAzureCredential(), subscription_id, resource_group, workspace
)

job = command(
    code="./src",
    command="python main.py",
    environment="AzureML-tensorflow-2.7-ubuntu20.04-py38-cuda11-gpu@latest",
    compute="gpu-cluster",
    display_name="tensorflow-mnist-example"
)

returned_job = ml_client.create_or_update(job)
```

#### 4.4.2. [ジョブの情報取得](https://github.com/Azure/azureml-examples/blob/main/sdk/python/jobs/single-step/debug-and-monitor/debug-and-monitor.ipynb)

コンピューティングに実行させるコード (ここでは [tfevents.py](https://github.com/Azure/azureml-examples/blob/main/sdk/python/jobs/single-step/debug-and-monitor/src/tfevents.py)) を別途用意します。

```python
from azure.ai.ml import MLClient
from azure.ai.ml import command
from azure.identity import DefaultAzureCredential
from azure.ai.ml.entities import JobService

subscription_id = "<SUBSCRIPTION_ID>"
resource_group = "<RESOURCE_GROUP>"
workspace = "<AML_WORKSPACE_NAME>"

ml_client = MLClient(
    DefaultAzureCredential(), subscription_id, resource_group, workspace
)

job = command(
    code="./src",
    command="python tfevents.py && sleep 2000",
    environment="AzureML-tensorflow-2.7-ubuntu20.04-py38-cuda11-gpu@latest",
    compute="cpu-cluster",
    display_name="debug-and-monitor-example",
    services={
        "My_jupyterlab": JobService(
            job_service_type="jupyter_lab",
        ),
        "My_vscode": JobService(
            job_service_type="vs_code",
        ),
        "My_tensorboard": JobService(
            job_service_type="tensor_board",
            properties={
                "logDir": "outputs/tblogs"
            },
        ),
    }
)

returned_job = ml_client.create_or_update(job)
```


### 4.5. [モデルの登録](https://github.com/Azure/azureml-examples/blob/main/sdk/python/assets/model/model.ipynb)

```python
from azure.ai.ml.entities import Model
from azure.ai.ml.constants import AssetTypes

job_name = "<JOB_NAME>"

run_model = Model(
    path=f"azureml://jobs/{job_name}/outputs/artifacts/paths/model/",
    name="run-model-example",
    description="Model created from run.",
    type=AssetTypes.MLFLOW_MODEL,
)
```


### 4.6. リソースの削除

#### 4.6.1. [ワークスペースの削除](https://github.com/Azure/azureml-examples/blob/main/sdk/python/resources/workspace/workspace.ipynb)

```python
ml_client.workspaces.begin_delete(name=ws_basic.name, delete_dependent_resources=True)
```

#### 4.6.2. リソースグループの削除

```python
import os
from azure.identity import AzureCliCredential
from azure.mgmt.resource import ResourceManagementClient

credential = AzureCliCredential()
subscription_id = os.environ["AZURE_SUBSCRIPTION_ID"]
resource_client = ResourceManagementClient(credential, subscription_id)
resource_group_name = "PythonAzureExample-rg"

resource_client.resource_groups.delete(resource_group_name)
```


---


## 5. 無料のオンライン トレーニング

| #   | モジュール | 所要時間 |
| --- | -------- | ------- |
| 1 | [Azure Machine Learning SDK の概要](https://learn.microsoft.com/ja-jp/training/modules/intro-to-azure-machine-learning-service/) | 60 分 |


---

## 6. 参考リンク

* [Python 用 Azure ML パッケージ クライアント ライブラリ - バージョン 1.4.0](https://learn.microsoft.com/ja-jp/python/api/overview/azure/ai-ml-readme?view=azure-python)
* [Azure Machine Learning 日本語版 - オープンソースの Azure Machine Learning チートシート](https://azure.github.io/azureml-cheatsheets/ja/)
* [Azure Machine Learning CLI、SDK、REST API を使用してモデルをトレーニングする](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-train-model?tabs=python)
* [CLI & SDK (v2) を使用して Azure Machine Learning 環境を管理する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-manage-environments-v2?tabs=python)
* [Azure Machine Learning SDK v2 でコンポーネントを使用して機械学習パイプラインを作成して実行する](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-create-component-pipeline-python)
* [azureml-examples/sdk/python at main · Azure/azureml-examples](https://github.com/Azure/azureml-examples/tree/main/sdk/python)
