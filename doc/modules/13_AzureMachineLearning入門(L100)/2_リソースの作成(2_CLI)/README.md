###### Azure Machine Learning 入門 (L100)

# 2. リソースの作成 (CLI)

- [2. リソースの作成 (CLI)](#2-リソースの作成-cli)
  - [1. YAML ファイルの作成](#1-yaml-ファイルの作成)
    - [1.1. ワークスペース YAML の作成](#11-ワークスペース-yaml-の作成)
      - [解説付きの例](#解説付きの例)
      - [解説コメント行無しの例](#解説コメント行無しの例)
      - [必須項目のみの例](#必須項目のみの例)
    - [1.2. コンピューティング YAML の作成](#12-コンピューティング-yaml-の作成)
      - [コンピューティング インスタンス](#コンピューティング-インスタンス)
      - [コンピューティング クラスター (AmlCompute)](#コンピューティング-クラスター-amlcompute)
      - [接続された仮想マシン](#接続された仮想マシン)
      - [アタッチされた Azure Arc 対応 Kubernetes (KubernetesCompute)](#アタッチされた-azure-arc-対応-kubernetes-kubernetescompute)
    - [1.3. データストア YAML の作成](#13-データストア-yaml-の作成)
      - [Azure BLOB](#azure-blob)
      - [Azure Data Lake Gen2](#azure-data-lake-gen2)
      - [Azure Files](#azure-files)
      - [Azure Data Lake Gen1](#azure-data-lake-gen1)
    - [1.4. モデル YAML の作成](#14-モデル-yaml-の作成)
  - [2. リソースの作成](#2-リソースの作成)
    - [2.1. ワークスペースの作成](#21-ワークスペースの作成)
    - [2.2. コンピューティングの作成](#22-コンピューティングの作成)
    - [2.3. データストアの作成](#23-データストアの作成)
  - [3. アセットの作成](#3-アセットの作成)
    - [3.1. モデルの作成](#31-モデルの作成)
  - [4. 参考リンク](#4-参考リンク)


---


## 1. YAML ファイルの作成

    YAML ファイルの作成
    ├─ 1. ワークスペース YAML の作成
    ├─ 2. コンピューティング YAML の作成
    ├─ 3. データストア YAML の作成
    └─ 4. モデル YAML の作成

### 1.1. [ワークスペース YAML](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-workspace) の作成

    YAML ファイルの作成
    └─ 1. ワークスペース YAML の作成

#### 解説付きの例

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/workspace.schema.json
# └ YAML スキーマ。 Azure Machine Learning 用 VS Code 拡張機能を使用して YAML ファイルを作成する場合は、ファイルの先頭に $schema を含めることで、スキーマとリソースの入力候補を呼び出すことができます。
#   Type: string
name: mlw-basic-prod
# └ 必須。 ワークスペースの名前。
#   Type: string
display_name: Basic workspace-example
# └ Studio UI のワークスペースの表示名。 リソース グループ内で一意でないことがあります。
#   Type: string
description: This example shows a YML configuration for a basic workspace. In case you use this configuration to deploy a new workspace, since no existing dependent resources are specified, these will be automatically created.
# └ ワークスペースの説明。
#   Type: string
tags:
# └ ワークスペースのタグの辞書。
#   Type: object
  purpose: demonstration
location: eastus
# └ ワークスペースの場所。 省略すると、既定でリソース グループの場所が設定されます。
#   Type: string
resource_group: rg-MyExistingWorkspace
# └ ワークスペースを含むリソース グループ。 リソース グループが存在しない場合は、新規に作成されます。
#   Type: string
hbi_workspace: false
# └ お客様のデータが、機密性の高いビジネス情報を含む High Business Impact (HBI) であるかどうか。 詳細については、保存時のデータの暗号化に関するページ https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data-encryption#encryption-at-rest を参照してください。
#   Type: boolean
#   既定値: false
storage_account: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.Storage/storageAccounts/<STORAGE_ACCOUNT>
# └ ワークスペースの既定のストレージ アカウントとして使う、既存の Azure Storage アカウントの完全修飾リソース ID。 Premium ストレージまたは階層型名前空間を持つストレージ アカウントを既定のストレージ アカウントとして使うことはできません。 省略すると、新しいストレージ アカウントが作成されます。
#   Type: string
container_registry: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.ContainerRegistry/registries/<CONTAINER_REGISTRY>
# └ ワークスペースの既定のコンテナー レジストリとして使う、既存の Azure コンテナー レジストリの完全修飾リソース ID。 Azure ML には、トレーニングとデプロイに使われるコンテナー イメージの管理に、Azure Container Registry (ACR) が使われます。 省略すると、新しいコンテナー レジストリが作成されます。 作成は遅延読み込みなので、トレーニングまたはデプロイのいずれかの操作でコンテナー レジストリが初めて必要になったときに作成されます。
#   Type: string
key_vault: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.KeyVault/vaults/<KEY_VAULT>
# └ ワークスペースの既定のキー コンテナーとして使う、既存の Azure キー コンテナーの完全修飾リソース ID。 省略すると、新しいキー コンテナーが作成されます。
#   Type: string
application_insights: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.insights/components/<APP_INSIGHTS>
# └ ワークスペースの既定のアプリケーション分析情報として使う、既存の Azure アプリケーション分析情報の完全修飾リソース ID。 省略すると、新しいアプリケーション分析情報が作成されます。
#   Type: string
customer_managed_key: 
# └ Azure Machine Learning では、メトリックとメタデータは Azure Cosmos DB インスタンスに格納されます。 既定では、データは Microsoft のマネージド キーを使って保存時に暗号化されます。 独自のカスタマー マネージド キーを暗号化に使うには、このセクションでカスタマー マネージド キーの情報を指定します。 詳細については、Azure Cosmos DB のデータ暗号化に関するページ https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-data-encryption#azure-cosmos-db を参照してください。
#   Type: object
  key_vault: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.KeyVault/vaults/<KEY_VAULT>
  # └ カスタマー マネージド キーを含むキー コンテナーの完全修飾リソース ID。 このキー コンテナーは、key_vault で指定した既定のワークスペースのキー コンテナーとは異なる場合があります。
  #   Type: string
  key_uri: https://<KEY_VAULT>.vault.azure.net/keys/<KEY_NAME>/<KEY_VERSION>
  # └ 保存データを暗号化するためのカスタマーマネージド キーのキー URI。 URI の形式は https://<keyvault-dns-name>/keys/<key-name>/<key-version> です。
  #   Type: string
image_build_compute: cpu-compute
# └ コンテナー レジストリが VNet の背後にある場合、環境 Docker イメージの構築に使うコンピューティング先の名前。 詳細については、VNet の背後にあるワークスペース リソースのセキュリティ保護に関するページ https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-secure-workspace-vnet#enable-azure-container-registry-acr を参照してください。
#   Type: string
public_network_access: Disabled
# └ ワークスペースに Private Link を使う場合、パブリック エンドポイントへのアクセスを許可するかどうかを指定します。 詳細については、VNet の背後でパブリック アクセスを有効にする方法に関するページ https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-configure-private-link#enable-public-access を参照してください。
#   Type: string
#   使用できる値: enabled, disabled
#   既定値: default
```

#### 解説コメント行無しの例

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/workspace.schema.json
name: mlw-basic-prod
display_name: Basic workspace-example
description: This example shows a YML configuration for a basic workspace. In case you use this configuration to deploy a new workspace, since no existing dependent resources are specified, these will be automatically created.
tags:
  purpose: demonstration
location: eastus
resource_group: rg-MyExistingWorkspace
hbi_workspace: false
storage_account: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.Storage/storageAccounts/<STORAGE_ACCOUNT>
container_registry: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.ContainerRegistry/registries/<CONTAINER_REGISTRY>
key_vault: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.KeyVault/vaults/<KEY_VAULT>
application_insights: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.insights/components/<APP_INSIGHTS>
customer_managed_key: 
  key_vault: /subscriptions/<SUBSCRIPTION_ID>/resourceGroups/<RESOURCE_GROUP>/providers/Microsoft.KeyVault/vaults/<KEY_VAULT>
  key_uri: https://<KEY_VAULT>.vault.azure.net/keys/<KEY_NAME>/<KEY_VERSION>
image_build_compute: cpu-compute
public_network_access: Disabled
```

#### 必須項目のみの例

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/workspace.schema.json
name: mlw-basic-prod
```


### 1.2. [コンピューティング YAML](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-overview#compute) の作成

    YAML ファイルの作成
    └─ 2. コンピューティング YAML の作成
        ├─ 1. コンピューティング インスタンス
        ├─ 2. コンピューティング クラスター (AmlCompute)
        ├─ 3. 接続された仮想マシン
        └─ 4. アタッチされた Azure Arc 対応 Kubernetes (KubernetesCompute)

#### [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-compute-instance)

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/computeInstance.schema.json
# └ YAML スキーマ。 Azure Machine Learning 用 VS Code 拡張機能を使用して YAML ファイルを作成する場合は、ファイルの先頭に $schema を含めることで、スキーマとリソースの入力候補を呼び出すことができます。
#   Type: string
type: computeinstance
# └ 必須。 コンピューティングの種類。
#   Type: string
#   使用できる値: computeinstance
name: basic-example-i
# └ 必須。 コンピューティングの名前。
#   Type: string
description: My description here.
# └ コンピューティングの説明。
#   Type: string
size: STANDARD_DS3_v2
# └ コンピューティング インスタンスに使用する VM サイズ。 詳細については、「サポートされている VM シリーズおよびサイズ」 https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-target#supported-vm-series-and-sizes をご覧ください。 すべてのリージョンですべてのサイズを使用できるわけではありません。
#   Type: string
#   使用できる値: 特定のリージョンでサポートされているサイズの一覧については、az ml compute list-sizes コマンドを使用してください。
#   既定値: Standard_DS3_v2
create_on_behalf_of:
# └ 別のユーザーの代理でコンピューティング インスタンスを作成するための設定。 割り当てられたユーザーに正しい RBAC アクセス許可があることを確認してください。
#   Type: object
  user_tenant_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
  # └ ロール割り当て済みユーザーの AAD テナント ID。
  #   Type: string
  user_object_id: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
  # └ ロール割り当て済みユーザーの AAD オブジェクト ID。
  #   Type: string
ssh_public_access_enabled: false
# └ コンピューティング インスタンスでパブリック SSH アクセスを有効にするかどうかを指定します。
#   Type: boolean
#   既定値: false
ssh_settings:
# └ コンピューティング インスタンスに接続するための SSH 設定。
#   Type: object
  ssh_key_value: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQCjZfvQ5un31DiGy62o+gZIv8ascvBxOstiz3akN1r/hTMKO61MCYvtxGquvkm5fMO3LeQniFdCcwHROFYXAzrnoWO2XlHGPJ7mdraxZEMthQoiEqgFbcy/r2cdKwxA4oE1FcwV0YHj9Hh90J9YgnLjtcvm2W6q6luiqE57WgaelQ== 
  # └ 管理者ユーザー アカウントの SSH 公開キー。
  #   Type: string
network_settings:
# └ ネットワークのセキュリティ設定。
#   Type: object
  vnet_name: vnet-MyNewOrExistingVNet
  # └ 新しい仮想ネットワーク (VNet) を作成するとき、または既存の仮想ネットワークを参照するときの、仮想ネットワークの名前。
  #   Type: string
  subnet: subnet-MyNewOrExistingSubnet
  # └ 新しい VNet を作成するとき、既存の VNet を参照するとき、または既存の VNet のサブネットの完全修飾リソース ID を参照するときの、サブネットの名前。 サブネット ID が指定されている場合は network_settings.vnet_name を指定しないでください。 サブネット ID は、別のリソース グループ内の VNet またはサブネットを参照できます。
  #   Type: string
identity:
# └ コンピューティングに割り当てるマネージド ID 構成。 AmlCompute クラスターは、システムによって割り当てられた 1 つの ID またはユーザーによって割り当てられた複数の ID のみをサポートします。両方同時にはサポートされません。
#   Type: object
  type: user_assigned
  # └ コンピューティングに割り当てるマネージド ID の種類。 型が user_assigned の場合は、identity.user_assigned_identities プロパティも指定する必要があります。
  #   Type: string
  #   使用できる値: system_assigned, user_assigned
  user_assigned_identities:
  # └ ユーザー割り当て ID の完全修飾リソース ID の一覧。
  #   Type: array
    - /subscriptions/[subscription ID]/resourcegroups/[resource group name]/providers/Microsoft.ManagedIdentity/userAssignedIdentities/[name of managed identity 1]
    - /subscriptions/[subscription ID]/resourcegroups/[resource group name]/providers/Microsoft.ManagedIdentity/userAssignedIdentities/[name of managed identity 2]
```

#### [コンピューティング クラスター (AmlCompute)](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-compute-aml)

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/amlCompute.schema.json 
# └ YAML スキーマ。 Azure Machine Learning 用 VS Code 拡張機能を使用して YAML ファイルを作成する場合は、ファイルの先頭に $schema を含めることで、スキーマとリソースの入力候補を呼び出すことができます。
#   Type: string
type: amlcompute
# └ 必須。 コンピューティングの種類。
#   Type: string
name: ssh-example
# └ 必須。 コンピューティングの名前。
#   Type: string
description: My description here.
# └ コンピューティングの説明。
#   Type: string
location: eastus
# └ コンピューティングの場所。 省略した場合、既定ではワークスペースの場所に設定されます。
#   Type: string
size: STANDARD_DS3_v2
# └ クラスターに使用する VM サイズ。 詳細については、「サポートされている VM シリーズおよびサイズ」 https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-target#supported-vm-series-and-sizes をご覧ください。 すべてのリージョンですべてのサイズを使用できるわけではありません。
#   Type: string
#   使用できる値: 特定のリージョンでサポートされているサイズの一覧については、az ml compute list-sizes を使用してください。
#   既定値: Standard_DS3_v2
tier: dedicated
# └ クラスターに使用する VM 優先度レベル。 優先順位の低い VM はプリエンプティブルですが、専用 VM と比較してコストが削減されます。
#   Type: string
#   使用できる値: dedicated, low_priority
#   既定値: dedicated
min_instances: 0
# └ クラスターで使用するノードの最小数。 ノードの最小数を 0 に設定すると、Azure ML はクラスターが使用されていないときに、クラスターをスケールダウンしてノードをゼロにすることができます。 0 よりも大きい値を指定すると、クラスターが使用されていない場合でも、指定した数のノードが実行され続けます。
#   Type: integer
#   既定値: 0
max_instances: 2
# └ クラスターで使用するノードの最大数。
#   Type: integer
#   既定値: 1
idle_time_before_scale_down: 120
# └ クラスターをスケールダウンするまでのノードのアイドル時間 (秒)。
#   Type: integer
#   既定値: 120
ssh_public_access_enabled: false
# └ クラスターのノードでパブリック SSH アクセスを有効にするかどうか。
#   Type: boolean
#   既定値: false
ssh_settings:
# └ クラスターに接続するための SSH 設定。
#   Type: object
  admin_username: example-user
  # └ ノードへの SSH 接続に使用できる管理者のユーザー アカウントの名前。
  #   Type: string
  admin_password: example-password
  # └ 管理者のユーザー アカウントのパスワード。 admin_password または ssh_key_value のいずれかが必須です。
  #   Type: string
  ssh_key_value: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQCjZfvQ5un31DiGy62o+gZIv8ascvBxOstiz3akN1r/hTMKO61MCYvtxGquvkm5fMO3LeQniFdCcwHROFYXAzrnoWO2XlHGPJ7mdraxZEMthQoiEqgFbcy/r2cdKwxA4oE1FcwV0YHj9Hh90J9YgnLjtcvm2W6q6luiqE57WgaelQ==
  # └ 管理者ユーザー アカウントの SSH 公開キー。 admin_password または ssh_key_value のいずれかが必須です。
  #   Type: string
network_settings:
# └ ネットワークのセキュリティ設定。
#   Type: object
  vnet_name: vnet-MyNewOrExistingVNet
  # └ 新しい仮想ネットワーク (VNet) を作成するとき、または既存の仮想ネットワークを参照するときの、仮想ネットワークの名前。
  #   Type: string
  subnet: subnet-MyNewOrExistingSubnet
  # └ 新しい VNet を作成するとき、既存の VNet を参照するとき、または既存の VNet のサブネットの完全修飾リソース ID を参照するときの、サブネットの名前。 サブネット ID が指定されている場合は network_settings.vnet_name を指定しないでください。 サブネット ID は、別のリソース グループ内の VNet またはサブネットを参照できます。
  #   Type: string
identity:
# └ コンピューティングに割り当てるマネージド ID 構成。 AmlCompute クラスターは、システムによって割り当てられた 1 つの ID またはユーザーによって割り当てられた複数の ID のみをサポートします。両方同時にはサポートされません。
#   Type: object
  type: user_assigned
  # └ コンピューティングに割り当てるマネージド ID の種類。 型が user_assigned の場合は、identity.user_assigned_identities プロパティも指定する必要があります。
  #   Type: string
  user_assigned_identities:
  # └ ユーザー割り当て ID の完全修飾リソース ID の一覧。
  #   Type: array
    - /subscriptions/[subscription ID]/resourcegroups/[resource group name]/providers/Microsoft.ManagedIdentity/userAssignedIdentities/[name of managed identity 1]
    - /subscriptions/[subscription ID]/resourcegroups/[resource group name]/providers/Microsoft.ManagedIdentity/userAssignedIdentities/[name of managed identity 2]
```

#### [接続された仮想マシン](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-compute-vm)

省略

#### [アタッチされた Azure Arc 対応 Kubernetes (KubernetesCompute)](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-compute-kubernetes)

省略



### 1.3. [データストア YAML](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-overview#datastore) の作成

    YAML ファイルの作成
    └─ 3. データストア YAML の作成
          ├─ 1. Azure BLOB
          ├─ 2. Azure Data Lake Gen2
          ├─ 3. Azure Files
          └─ 4. Azure Data Lake Gen1


#### [Azure BLOB](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-datastore-blob)

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/azureBlob.schema.json
# └ YAML スキーマ。 Azure Machine Learning 用 VS Code 拡張機能を使用して YAML ファイルを作成する場合は、ファイルの先頭に $schema を含めることで、スキーマとリソースの入力候補を呼び出すことができます。
#   Type: string
type: azure_blob
# └ 必須。 データストアの種類。
#   Type: string
#   使用できる値: azure_blob
name: blob_protocol_example
# └ 必須。 データストアの名前。
#   Type: string
description: Datastore pointing to a blob container using wasbs protocol.
# └ データストアの説明。
#   Type: string
tags:
# └ データストアのタグの辞書。
#   Type: object
  purpose: demonstration
account_name: mytestblobstore
# └ 必須。 Azure Storage アカウントの名前。
#   Type: string
container_name: data-container
# └ 必須。 コンテナーの名前。
#   Type: string
endpoint: blob.core.windows.net
# └ ストレージ アカウント名と endpoint を組み合わせてストレージ アカウント エンドポイント URL を作成するために使用される、ストレージ サービスのエンドポイント サフィックス。 ストレージ アカウント URL の例: https://<storage-account-name>.blob.core.windows.net。
#   Type: string
protocol: wasbs
# └ コンテナーへの接続に使用するプロトコル。
#   Type: string
#   使用できる値: https, wasbs
#   既定値: https
credentials:
# └ Azure ストレージ アカウントに接続するための資格情報ベースの認証資格情報。 アカウント キーまたは Shared Access Signature (SAS) トークンのいずれかを指定できます。 資格情報のシークレットは、ワークスペースのキー コンテナーに格納されます。
#   Type: object
  account_key: XXXxxxXXXxXXXXxxXXXXXxXXXXXxXxxXxXXXxXXXxXXxxxXXxxXXXxXxXXXxxXxxXXXXxxxxxXXxxxxxxXXXxXXX
  # └ ストレージ アカウントにアクセスするアカウント キー。 credentials.account_key または credentials.sas_token のいずれかは、credentials を指定した場合は必須です。
  #   Type: string
  sas_token: XXXxxxXXXxXXXXxxXXXXXxXXXXXxXxxXxXXXxXXXxXXxxxXXxxXXXxXxXXXxxXxxXXXXxxxxxXXxxxxxxXXXxXXX
  # └ ストレージ アカウントにアクセスする SAS トークン。 credentials.account_key または credentials.sas_token のいずれかは、credentials を指定した場合は必須です。
  #   Type: string
```

#### [Azure Data Lake Gen2](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-datastore-data-lake-gen2)

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/azureDataLakeGen2.schema.json
# └ YAML スキーマ。 Azure Machine Learning 用 VS Code 拡張機能を使用して YAML ファイルを作成する場合は、ファイルの先頭に $schema を含めることで、スキーマとリソースの入力候補を呼び出すことができます。
#   Type: string
type: azure_data_lake_gen2
# └ 必須。 データストアの種類。
#   Type: string
#   使用できる値: azure_data_lake_gen2
name: adls_gen2_example
# └ 必須。 データストアの名前。
#   Type: string
description: Datastore pointing to an Azure Data Lake Storage Gen2.
# └ データストアの説明。
#   Type: string
tags:
# └ データストアのタグの辞書。
#   Type: object
  purpose: demonstration
account_name: mytestdatalakegen2
# └ 必須。 Azure Storage アカウントの名前。
#   Type: string
filesystem: my-gen2-container
# └ 必須。 ファイル システムの名前。 ファイルとフォルダーを含む親ディレクトリ。 これは、Azure Blob Storage 内のコンテナーと同じです。
#   Type: string
endpoint: dfs.core.windows.net
# └ ストレージ アカウント名と endpoint を組み合わせてストレージ アカウント エンドポイント URL を作成するために使用される、ストレージ サービスのエンドポイント サフィックス。 ストレージ アカウント URL の例: https://<storage-account-name>.dfs.core.windows.net。
#   Type: string
#   既定値: core.windows.net
protocol: abfss
# └ ファイル システムへの接続に使用するプロトコル。
#   Type: string
#   使用できる値: https, abfss
#   既定値: https
credentials:
# └ Azure ストレージ アカウントに接続するためのサービス プリンシパルの資格情報。 資格情報のシークレットは、ワークスペースのキー コンテナーに格納されます。
#   Type: object
  tenant_id: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
  # └ サービス プリンシパルのテナント ID。 credentials を指定した場合は必須。
  #   Type: string
  client_id: XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
  # └ サービス プリンシパルのクライアント ID。 credentials を指定した場合は必須。
  #   Type: string
  client_secret: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
  # └ サービス プリンシパルのクライアント シークレット。 credentials を指定した場合は必須。
  #   Type: string
  resource_url: https://storage.azure.com/
  # └ Azure Data Lake Storage Gen2 アカウントで実行される操作を決定するリソース URL。
  #   Type: string
  #   既定値: https://storage.azure.com/
  authority_url: https://login.microsoftonline.com
  # └ ユーザーの認証に使用される機関 URL。
  #   Type: string
  #   既定値: https://login.microsoftonline.com
```

#### [Azure Files](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-datastore-files)

省略

#### [Azure Data Lake Gen1](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-datastore-data-lake-gen1)

省略


### 1.4. [モデル YAML](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-model) の作成

    YAML ファイルの作成
    └─ 4. モデル YAML の作成

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/model.schema.json
# └ YAML スキーマ。
#   Type: string
name: local-file-example
# └ 必須。 モデルの名前。
#   Type: string
version: 1
# └ モデルのバージョン。 省略した場合、Azure ML によってバージョンが自動生成されます。
#   Type: integer
description: Model created from local file.
# └ モデルの説明。
#   Type: string
tags:
# └ モデルのタグの辞書。
#   Type: object
  purpose: demonstration
path: mlflow-model/model.pkl
# └ モデル ファイルへのローカル パス、またはモデル ファイルへのクラウド パスの URI のいずれかです。 これは、ファイルまたはディレクトリのいずれかを指します。
#   Type: string
#   使用できる値: custom_model, mlflow_model, triton_model
flavors:
# └ モデルのフレーバー。 各モデル ストレージ形式の種類には、1 つまたは複数のサポートされているフレーバーを含めることができます。 コードをデプロイしない場合に適用されます。
#   Type: object
#   参考: https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-mlflow-models#the-models-flavors
  fastai:
    data: model.fastai
    fastai_version: 2.4.1
  python_function:
    data: model.fastai
    env: conda.yaml
    loader_module: mlflow.fastai
    python_version: 3.8.12
```


---


## 2. リソースの作成

    リソースの作成
    ├─ 1. ワークスペースの作成
    ├─ 2. コンピューティングの作成
    └─ 3. データストアの作成

### 2.1. [ワークスペースの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=cli#workspace)

```bash
az ml workspace create --file my_workspace.yml
```

### 2.2. [コンピューティングの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=cli#compute)

```bash
az ml compute --file my_compute.yml
```

### 2.3. [データストアの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=cli#datastore)

```bash
az ml datastore create --file my_datastore.yml
```


---


## 3. アセットの作成

    アセットの作成
    └─ 1. モデルの作成

### 3.1. [モデルの作成](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=cli#model)

```bash
az ml model create --file my_model.yml
```


---


## 4. 参考リンク

* [Azure Machine Learning CLI v2 | CLI と SDK v2 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-v2#azure-machine-learning-cli-v2)
* [Azure Machine Learning (v2) のしくみ - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2?tabs=cli)
* [CLI (v2) YAML スキーマの概要 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/reference-yaml-overview)
