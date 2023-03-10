###### Azure Machine Learning 入門 (L100)

# 2. リソースの作成 (GUI)

- [2. リソースの作成 (GUI)](#2-リソースの作成-gui)
  - [1. リソースの作成 (ハンズオン)](#1-リソースの作成-ハンズオン)
    - [1.1. ワークスペースの作成](#11-ワークスペースの作成)
    - [1.2. コンピューティングの作成](#12-コンピューティングの作成)
      - [1.2.1. コンピューティング インスタンス](#121-コンピューティング-インスタンス)
        - [1.2.1.1. コンピューティング インスタンスの作成](#1211-コンピューティング-インスタンスの作成)
        - [1.2.1.2. コンピューティング インスタンスのスケジュール設定](#1212-コンピューティング-インスタンスのスケジュール設定)
        - [1.2.1.3. コンピューティング インスタンスのスケジュール変更](#1213-コンピューティング-インスタンスのスケジュール変更)
        - [1.2.1.4. コンピューティング インスタンスのスケジュール削除](#1214-コンピューティング-インスタンスのスケジュール削除)
        - [1.2.1.5. コンピューティング インスタンスの停止](#1215-コンピューティング-インスタンスの停止)
    - [1.3. データストアの作成](#13-データストアの作成)
      - [1.3.1. Blob ストレージ (コンテナー) の作成](#131-blob-ストレージ-コンテナー-の作成)
      - [1.3.2. データストアの作成](#132-データストアの作成)
  - [2. アセットの作成](#2-アセットの作成)
    - [2.1. モデルの登録](#21-モデルの登録)
  - [3. 参考リンク](#3-参考リンク)


---


## 1. [リソース](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2)の作成 (ハンズオン)

    リソースの作成 (ハンズオン)
    ├─ 1. ワークスペースの作成
    ├─ 2. コンピューティングの作成
    └─ 3. データストアの作成

_👋このチャプターではハンズオンを行います。不明点等ある場合は質問してください。(マイクをオンにし、画面共有をしてください。)_

### 1.1. [ワークスペース](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-workspace)の作成

Step 1 (Figure 1.1-1)
![ワークスペースの作成01](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00001.png)

Step 2 (Figure 1.1-2)
![ワークスペースの作成02](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00002.png)

Step 3 (Figure 1.1-3)
![ワークスペースの作成03](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00003.png)

Step 4 (Figure 1.1-4)
![ワークスペースの作成04](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00004.png)

Step 5 (Figure 1.1-5)
![ワークスペースの作成05](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00005.png)

Step 6 (Figure 1.1-6)
![ワークスペースの作成06](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00006.png)

Step 7 (Figure 1.1-7)
![ワークスペースの作成07](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00007.png)

Step 8 (Figure 1.1-8)
![ワークスペースの作成08](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00008.png)

Step 9 (Figure 1.1-9)
![ワークスペースの作成09](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00009.png)

Step 10 (Figure 1.1-10)
![ワークスペースの作成10](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00010.png)

Step 11 (Figure 1.1-11)
![ワークスペースの作成11](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00011.png)

Step 12 (Figure 1.1-12)
![ワークスペースの作成12](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00012.png)

Step 13 (Figure 1.1-13)
![ワークスペースの作成13](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00013.png)

Step 14 (Figure 1.1-14)
![ワークスペースの作成14](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00014.png)

Step 15 (Figure 1.1-15)
![ワークスペースの作成15](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00015.png)

Step 16 (Figure 1.1-16)
![ワークスペースの作成16](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00016.png)

Step 17 (Figure 1.1-17)
![ワークスペースの作成1y](./assets/images/AML-Workspace-Creation-via-Azure-Portal-00017.png)


### 1.2. [コンピューティング](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#compute)の作成

#### 1.2.1. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)

> Azure Machine Learning コンピューティング インスタンスは、データ サイエンティスト向けのマネージド クラウドベース ワークステーションです。

> コンピューティング インスタンスを使うと、Azure Machine Learning の開発を簡単に開始できます。

> コンピューティング インスタンスは、機械学習のためにクラウド内で完全に構成され管理される自分の開発環境として使用します。 また、開発やテストのためのトレーニングや推論のコンピューティング ターゲットとして使用することもできます。

> コンピューティング インスタンスの Jupyter 機能を動作させるには、Web ソケット通信が無効になっていないことを確認してください。 お使いのネットワークで、*. instances.azureml.net と *. instances.azureml.ms への WebSocket 接続が許可されていることを確認してください。

##### 1.2.1.1. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)の作成

Step 1 (Figure 1.2.1.1-1)
![コンピューティングインスタンスの作成01](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00001.png)

Step 2 (Figure 1.2.1.1-2)
![コンピューティングインスタンスの作成02](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00002.png)

Step 3 (Figure 1.2.1.1-3)
![コンピューティングインスタンスの作成03](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00003.png)

注意: コンピューティング名は Azure リージョン内でユニークである必要があります。

Step 4 (Figure 1.2.1.1-4)
![コンピューティングインスタンスの作成04](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00004.png)

Step 5 (Figure 1.2.1.1-5)
![コンピューティングインスタンスの作成05](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00005.png)

Step 6 (Figure 1.2.1.1-6)
![コンピューティングインスタンスの作成06](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00006.png)

Step 7 (Figure 1.2.1.1-7)
![コンピューティングインスタンスの作成07](./assets/images/AML-Computing-Instance-Creation-via-Azure-Portal-00007.png)

##### 1.2.1.2. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)のスケジュール設定

コンピューティング インスタンスは、スケジュールを指定してスタートアップとシャットダウンを自動実行することができます。
スケジュール設定はインスタンス作成時または作成後のいずれのタイミングでも実行可能です。
以下はインスタンス作成後にスケジュール設定をする例です。

Step 0 (Figure 1.2.1.2-0)
![コンピューティング インスタンスのスケジュール設定00](./assets/images/AML-Workspace-Home-Select-Compute.png)

Step 1 (Figure 1.2.1.2-1)
![コンピューティング インスタンスのスケジュール設定01](./assets/images/AML-Computing-Instance-Create-Schedule-00001.png)

Step 2 (Figure 1.2.1.2-2)
![コンピューティング インスタンスのスケジュール設定02](./assets/images/AML-Computing-Instance-Create-Schedule-00002.png)

Step 3 (Figure 1.2.1.2-3)
![コンピューティング インスタンスのスケジュール設定03](./assets/images/AML-Computing-Instance-Create-Schedule-00003.png)

Step 4 (Figure 1.2.1.2-4)
![コンピューティング インスタンスのスケジュール設定04](./assets/images/AML-Computing-Instance-Create-Schedule-00004.png)

Step 5 (Figure 1.2.1.2-5)
![コンピューティング インスタンスのスケジュール設定05](./assets/images/AML-Computing-Instance-Create-Schedule-00005.png)

Step 6 (Figure 1.2.1.2-6)
![コンピューティング インスタンスのスケジュール設定06](./assets/images/AML-Computing-Instance-Create-Schedule-00006.png)

Step 7 (Figure 1.2.1.2-7)
![コンピューティング インスタンスのスケジュール設定07](./assets/images/AML-Computing-Instance-Create-Schedule-00007.png)

##### 1.2.1.3. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)のスケジュール変更

Step 1 (Figure 1.2.1.3-1)
![コンピューティング インスタンスのスケジュール変更01](./assets/images/AML-Computing-Instance-Update-Schedule-00001.png)

Step 2 (Figure 1.2.1.3-2)
![コンピューティング インスタンスのスケジュール変更02](./assets/images/AML-Computing-Instance-Update-Schedule-00002.png)

Step 3 (Figure 1.2.1.3-3)
![コンピューティング インスタンスのスケジュール変更03](./assets/images/AML-Computing-Instance-Update-Schedule-00003.png)

Step 4 (Figure 1.2.1.3-4)
![コンピューティング インスタンスのスケジュール変更04](./assets/images/AML-Computing-Instance-Update-Schedule-00004.png)

##### 1.2.1.4. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)のスケジュール削除

Step 1 (Figure 1.2.1.4-1)
![コンピューティング インスタンスのスケジュール削除01](./assets/images/AML-Computing-Instance-Delete-Schedule-00001.png)

Step 2 (Figure 1.2.1.4-2)
![コンピューティング インスタンスのスケジュール削除02](./assets/images/AML-Computing-Instance-Delete-Schedule-00002.png)

Step 3 (Figure 1.2.1.4-3)
![コンピューティング インスタンスのスケジュール削除03](./assets/images/AML-Computing-Instance-Delete-Schedule-00003.png)

##### 1.2.1.5. [コンピューティング インスタンス](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance)の停止

Step 1 (Figure 1.2.1.5-1)
![コンピューティング インスタンスの停止01](./assets/images/AML-Computing-Instance-Stop-00001.png)

Step 2 (Figure 1.2.1.5-2)
![コンピューティング インスタンスの停止02](./assets/images/AML-Computing-Instance-Stop-00002.png)

Step 3 (Figure 1.2.1.5-3)
![コンピューティング インスタンスの停止03](./assets/images/AML-Computing-Instance-Stop-00003.png)

### 1.3. [データストア](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#datastore)の作成

#### 1.3.1. [Blob ストレージ](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-blobs-introduction) ([コンテナー](https://learn.microsoft.com/ja-jp/azure/storage/blobs/storage-blobs-introduction#containers)) の作成

Step 1 (Figure 1.3.1-1)
![Blobストレージの作成01](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00001.png)

Step 2 (Figure 1.3.1-2)
![Blobストレージの作成02](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00002.png)

Step 3 (Figure 1.3.1-3)
![Blobストレージの作成03](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00003.png)

Step 4 (Figure 1.3.1-4)
![Blobストレージの作成04](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00004.png)

Step 5 (Figure 1.3.1-5)
![Blobストレージの作成05](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00005.png)

Step 6 (Figure 1.3.1-6)
![Blobストレージの作成06](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00006.png)

Step 7 (Figure 1.3.1-7)
![Blobストレージの作成07](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00007.png)

Step 8 (Figure 1.3.1-8)
![Blobストレージの作成08](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00008.png)

Step 9 (Figure 1.3.1-9)
![Blobストレージの作成09](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00009.png)

Step 10 (Figure 1.3.1-10)
![Blobストレージの作成10](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00010.png)

Step 11 (Figure 1.3.1-11)
![Blobストレージの作成11](./assets/images/Azure-Storage-Blob-Container-Creation-via-Azure-Portal-00011.png)

#### 1.3.2. [データストア](https://learn.microsoft.com/ja-jp/azure/machine-learning/azure-machine-learning-glossary#datastore)の作成

Step 1 (Figure 1.3.2-1)
![データストアの作成01](./assets/images/AML-Datastore-Creation-via-Azure-Portal-00001.png)

Step 2 (Figure 1.3.2-2)
![データストアの作成02](./assets/images/AML-Datastore-Creation-via-Azure-Portal-00002.png)

Step 3 (Figure 1.3.2-3)
![データストアの作成03](./assets/images/AML-Datastore-Creation-via-Azure-Portal-00003.png)

Step 4 (Figure 1.3.2-4)
![データストアの作成04](./assets/images/AML-Datastore-Creation-via-Azure-Portal-00004.png)

Step 5 (Figure 1.3.2-5)
![データストアの作成05](./assets/images/AML-Datastore-Creation-via-Azure-Portal-00005.png)

## 2. [アセット](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-azure-machine-learning-v2)の作成

    アセットの作成
    └─ 1. モデルの登録

### 2.1. モデルの登録

Step 1 (Figure 2.1-1)
![モデルの登録01](./assets/images/AML-Model-Registration-via-Azure-Portal-00001.png)

Step 2 (Figure 2.1-2)
![モデルの登録02](./assets/images/AML-Model-Registration-via-Azure-Portal-00002.png)

Step 3 (Figure 2.1-3)
![モデルの登録03](./assets/images/AML-Model-Registration-via-Azure-Portal-00003.png)

Step 4 (Figure 2.1-4)
![モデルの登録04](./assets/images/AML-Model-Registration-via-Azure-Portal-00004.png)


---


## 3. 参考リンク

* [クイックスタート: ワークスペース リソースを作成する - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/quickstart-create-resources)
