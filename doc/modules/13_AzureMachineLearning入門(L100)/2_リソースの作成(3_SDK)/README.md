###### Azure Machine Learning 入門 (L100)

# 2. リソースの作成 (SDK)

- [2. リソースの作成 (SDK)](#2-リソースの作成-sdk)
  - [1. リソースの作成](#1-リソースの作成)
    - [1.1. ワークスペースの作成](#11-ワークスペースの作成)
    - [1.2. コンピューティングの作成](#12-コンピューティングの作成)
    - [1.3. データストアの作成](#13-データストアの作成)
  - [2. アセットの作成](#2-アセットの作成)
    - [2.1. モデルの作成](#21-モデルの作成)
  - [3. 参考資料](#3-参考資料)


---


## 1. リソースの作成

### 1.1. [ワークスペースの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=sdk#create-a-workspace)

```python
ws_basic = Workspace(
    name="my-workspace",
    location="eastus", # Azure region (location) of workspace
    display_name="Basic workspace-example",
    description="This example shows how to create a basic workspace"
)
ml_client.workspaces.begin_create(ws_basic) # use MLClient to connect to the subscription and resource group and create workspace
```

### 1.2. [コンピューティングの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=sdk#compute)

```python
cluster_basic = AmlCompute(
    name="basic-example",
    type="amlcompute",
    size="STANDARD_DS3_v2",
    location="westus",
    min_instances=0,
    max_instances=2,
    idle_time_before_scale_down=120,
)
ml_client.begin_create_or_update(cluster_basic)
```

### 1.3. [データストアの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=sdk#datastore)

```python
blob_datastore1 = AzureBlobDatastore(
    name="blob-example",
    description="Datastore pointing to a blob container.",
    account_name="mytestblobstore",
    container_name="data-container",
    credentials={
        "account_key": "XXXxxxXXXxXXXXxxXXXXXxXXXXXxXxxXxXXXxXXXxXXxxxXXxxXXXxXxXXXxxXxxXXXXxxxxxXXxxxxxxXXXxXXX"
    },
)
ml_client.create_or_update(blob_datastore1)
```


---


## 2. アセットの作成

### 2.1. [モデルの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=sdk#creating-a-model)

```python
my_model = Model(
    path="model.pkl", # the path to where my model file is located
    type="custom_model", # can be custom_model, mlflow_model or triton_model
    name="my-model",
    description="Model created from local file.",
)

ml_client.models.create_or_update(my_model) # use the MLClient to connect to workspace and create/register the model
```


---


## 3. 参考資料

* [Azure Machine Learning Python SDK v2 | CLI と SDK v2 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-v2#azure-machine-learning-python-sdk-v2)
* [Azure Machine Learning SDK for Python - Azure Machine Learning Python | Microsoft Learn](https://learn.microsoft.com/ja-jp/python/api/overview/azure/ml/?view=azure-ml-py)
* [Azure Machine Learning (v2) のしくみ - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=sdk)
