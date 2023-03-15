# Azure Machine Learning 概要

- [Azure Machine Learning 概要](#azure-machine-learning-概要)
  - [1. 背景](#1-背景)
    - [1.1. 機械学習のシステム](#11-機械学習のシステム)
    - [1.2. 機械学習プロジェクトのプロセス](#12-機械学習プロジェクトのプロセス)
      - [1.2.1. 参考リンク](#121-参考リンク)
  - [2. Azure Machine Learning とは](#2-azure-machine-learning-とは)
  - [3. 4 つの特徴](#3-4-つの特徴)
    - [3.1. For all skill levels](#31-for-all-skill-levels)
      - [3.1.1. 自動機械学習 (AutoML)](#311-自動機械学習-automl)
      - [3.1.2. デザイナー (ドラッグアンドドロップ ML)](#312-デザイナー-ドラッグアンドドロップ-ml)
      - [3.1.3. Python SDK + ノートブック (Python 3.7+, R)](#313-python-sdk--ノートブック-python-37-r)
      - [3.1.4. 参考リンク](#314-参考リンク)
    - [3.2. Industry leading MLOps](#32-industry-leading-mlops)
      - [3.2.1. 参考リンク](#321-参考リンク)
    - [3.3. Open \& Interoperable](#33-open--interoperable)
      - [3.3.1. 参考リンク](#331-参考リンク)
    - [3.4. Trusted](#34-trusted)
      - [3.4.1. 参考リンク](#341-参考リンク)
  - [4. まとめ](#4-まとめ)
  - [5. 参考リンク](#5-参考リンク)


---


## 1. 背景

```
背景
├─ 1. 機械学習のシステム
└─ 2. 機械学習プロジェクトのプロセス
```


### 1.1. 機械学習のシステム

* 本当に重要なのは、機械学習モデルを支えるシステム構築・運用管理。
    - これらは今日非常に複雑になっている。

![今日複雑になるシステム](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00008.png)

* 参考: [“Hidden Technical Debt in Machine Learning Systems,” Google NIPS 2015  
](https://proceedings.neurips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf)
    - [Hidden technical debt in machine learning systems（日本語資料）](https://www.slideshare.net/Gushi/hidden-technical-debt-in-machine-learning-systems)
    - [データ活用における課題と対策](https://www.bcm.co.jp/site/2019/08/ntt-com/1908-ntt-com-01-05.pdf)

![ストレージ&DB](./assets/images/AzureML-Bootcamp-資料_1280x720px_00037.png)

![計算環境](./assets/images/AzureML-Bootcamp-資料_1280x720px_00038.png)

![コンテナ](./assets/images/AzureML-Bootcamp-資料_1280x720px_00039.png)

![セキュリティ](./assets/images/AzureML-Bootcamp-資料_1280x720px_00040.png)

![スクラッチで全部作る？？](./assets/images/AzureML-Bootcamp-資料_1280x720px_00042.png)

![AI成熟度](./assets/images/AzureML-Bootcamp-資料_1280x720px_00044.png)

![管理コストが次第に大きくなる問題](./assets/images/AzureML-Bootcamp-資料_1280x720px_00045.png)

![マネージドサービスによって、機械学習に集中](./assets/images/AzureML-Bootcamp-資料_1280x720px_00046.png)

<details>
<summary>解説</summary>
<i>
機械学習のシステムを考えています。お客様で機械学習の取り組みが始まっていますがどうしてもモデル開発にフォーカスされがちですもちろん精度が高いモデルといったものが必要になってきますがそれ以外にも大事なピースが存在します。

スライドにありますようにモデル学習で使うためのデータを収集する機能であったりデータを検証する機能機器学習のプロセスを管理する機能モデルを提供する機能またそれをモニタリングする機能など数多くのモジュールが必要になってきます.

このようなモジュールがしっかり準備されていないやったり不十分であると機械学習のモデルの運用管理が煩雑になり結果としてモデルの精度が低下したり鳥が徐々に使われなくなったりしますまた機械学習のプロジェクトスケールさせることも難しいです

といった理由から西学習のモデルだけではなく、その周辺のシステムもしっかり考えていく必要が今後出てきます
</i>
</details>


### 1.2. 機械学習プロジェクトのプロセス

* 機械学習のライフサイクルを高速かつ効率的に回していくことが、市場競争において重要になっている。
    - 既存のしくみに乗っかることで、効率的に実現することができる。

![機械学習プロジェクトのプロセス](./assets/images/AzureML-Bootcamp-資料_1280x720px_00030.png)

![ライフサイクルを早く回す](./assets/images/AzureML-Bootcamp-資料_1280x720px_00031.png)

![Model Lifecycle](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00041.png)

<details>
<summary>解説</summary>
<i>
次に機械学習のプロセスについて見ていきます。モデルの運用管理まで考えると大きく3つのプロセスに分かれると考えています。実験、モデル開発、運用管理です。

実験においては試行錯誤するモデル開発を指しています。様々な特徴量エンジニアリング、機械学習アルゴリズム、パラメータ、精度が高いモデルを探し出すプロセスになります。

最近ですと実験の次のプロセスのモデル検証・運用管理のフェーズに行っているお客様も非常に増えています。当然実験のプロセスの一定精度が高いモデルつまり業務に適応できるモデルといったものが作成できるのであればモデルの検証運用管理といったフェーズに入ってきます。

モデルの検証においては実験で利用した行動であったりデータのテストを行います。またモデル学習の再現性の確認を行っていきますモデルが再現できないと後々の再学習が難しかったりで信頼性の低いモデルと言うふうに判断されてしまいます。
モデルのパッケージ化においてはDockerなどでモデルが動ける状態にしていきます。以上が検証のプロセスになります。

最後の運用管理においては機械学習モデルのデプロイまた利用開始後のデータモデルシステムのモニタリングが必要になりますまた必要に応じて例えば精度が落ちてきた場合などにはモデルの再学習再作成が必要になります。

以上が機械学習に求められる基本的な 3 つプロセスになってきます。このプロセスを効率的に高速に回すことを考えていく必要があります。

これは様々な理由が挙げられます。

例えば、機械学習のモデルの精度は。データの特徴が変化するために一般的には徐々に低下してくると言うふうに言われています。
そのためいちどこの3つのプロセスを回しておしまいではなくて再度再学習をしますつまりもう一度この3つのプロセスを回す必要があると言うことです.

またデーターの質が向上したり量が増えてくると機械学習のモデルの精度の向上が期待されます。そのためいちど作っておしまいではなくて再度この3つのプロセスを回してモデルの精度を向上していくというアプローチも必要になります。

繰り返しになりますが、効率的に機械学習のプロセスを回す方法仕組みを考える必要があります。
</i>
</details>

#### 1.2.1. 参考リンク

* [機械学習プロジェクトのワークフロー | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#machine-learning-project-workflow)

<details>
<summary>解説</summary>
<i>
これまでのまとめをさせていただきます機械学習となるとモデル開発にフォーカスがあって機械学習モデルにフォーカスされがちですか実は型学習システム全体を見てみると非常に数多くのシステムモジュールといったことが必要になっています。

また、気合学習プロセスの話もさせていただきました。試行錯誤的なモデル開発を行う実験モデルの検証またそれを運用管理するほど大きく分けて3つのプロセスがあります。

データの量が増えたり質が改善されてくるとモデルの精度の向上が期待できます。また一般的にはデータの特徴というのは日々変化していくためいちど作ったモデルの精度は劣化していくことが想定されます。そのためモデルの運用管理済学士を見据えた機械学習のシステムといったものを考えておく必要があります。
</i>
</details>


---


<details>
<summary>解説</summary>
<i>
そこで本日は Azure Machine Learning がいかに皆様の機械学習プロジェクトを効率的に行うことができるのか、様々な機能であったり活用メリットについてお話をして参ります
</i>
</details>

## 2. Azure Machine Learning とは

* 機械学習プロセスをエンドツーエンドでサポートするマネージドサービス
    - 必要なシステムモジュールをあらかじめビルトインしている
* 自動機械学習やパラメータチューニング機能による効率的なモデル開発
* 継続的なモデルのデプロイ & 運用管理をサポート
* スケーラブルな計算環境による並列分散処理 etc

![機械学習プロセスをエンドツーエンドでサポートするマネージドサービス](./assets/images/AzureML-Bootcamp-資料_1280x720px_00049.png)

![必要なシステムモジュールをあらかじめビルトインしている](./assets/images/AzureML-Bootcamp-資料_1280x720px_00051.png)

![資産管理](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00033.png)

![モデル管理](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00037.png)

![実験管理 - 実験履歴](./assets/images/Azure-Machine-Learning-service-%E6%A6%82%E8%A6%81-JPN-asof-20190111_1280x720px-00011.png)

![実験メトリックは記録・管理される](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00051.png)

![各実験の履歴(メトリック、ログ)](./assets/images/データサイエンティストのためのAzure-Machine-Learning-サービスご紹介_full_1280x720px-00052.png)

![自動機械学習 Automated Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00009.png)

![機械学習をより扱いやすく - ハイパーパラメータ探索](./assets/images/Azure-Machine-Learning-%E3%81%A8-Cognitive-Search-%E6%A6%82%E8%A6%81_1280x720px-00012.png)

![Hyperparameters の探索手法](assets/images/Microsoft%20AIご紹介資料_V10_201911-00105.png)

![ハイパーパラメータチューニング "Hyperdrive"](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00024.png)

![ハイパーパラメータチューニング "Hyperdrive"](./assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00017.png)

![継続的なモデルのデプロイ & 運用管理をサポート](./assets/images/AzureML-Bootcamp-資料_1280x720px_00059.png)

![Azure Machine Learning Compute](./assets/images/Azure-Machine-Learning-service-%E6%A6%82%E8%A6%81-JPN-asof-20190111_1280x720px-00020.png)

![スケーラブルな計算環境による並列分散処理](./assets/images/AzureML-Bootcamp-資料_1280x720px_00060.png)

![大規模ワークロードに対応するテクノロジー](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00074.png)

![バッチ推論を高速に実行する ParallelRunStep](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00077.png)

![Azure Databricks との連携](./assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00021.png)

<details>
<summary>解説</summary>
<i>
Azure Machine Learning は機械学習のプロセスをend-to-endでサポートするマネージドサービスになります機械学習のシステムに必要なモジュールはあらかじめビルトインされているため即座に機械学習のプロジェクトを始めることができます。

モデル開発においては自動車機械学モデル開発においては自動車機械学習やパラメーターチューニング機能によって高速に精度が高いモデルを構築できます。その後のモデル検証運用管理の仕組み機能もご提供しております。継続的なモデルのデプロイメント運用管理が可能になります。

またクラウドのメリットとしてスケーラブルな並列分散環境といったものが利用できます。自動機械学習やパラメーターチューリング機能によって高速に誰でも精度が高いモデルを構築できます。
</i>
</details>


---


## 3. 4 つの特徴

```
1. For all skill levels
    - あらゆるスキルレベルに対応した機械学習の機能を提供
2. Industry leading MLOps
    - 機械学習のプロセスを効率的に回すための仕組みや機能を提供
3. Open & Interoperable
    - オープンなテクノロジーを採用＆あらゆる場所・デバイスで利用可能
4. Trusted
    - 透明性の高い責任のあるAIモデルの開発を支援
```

<details>
<summary>解説</summary>
<i>
Azure Machine Learning の4つの特徴・差別化要素についてご紹介させてください

- For all skill levels はいわゆる民主化を指していますが、あらゆるスキルレベルに対応した機械学習の機能をご提供していることです
- Industry Learning MLOps は先ほども説明しましたが先程の説明にもありましたがモデルの機械学習のプロセスを効率的に回すための仕組み機能をご提供していると言うことです.
オープン&インターオペレーターは進化し続ける機械学習のオープンテクノロジーを採用しているというところと機械学習モデルの相互運用性によってあらゆる場所クラウドデバイスで機械学習のモデルを利用できると言うことです。
トラスティーは透明性の高い責任のある機械学習ソリューションを構築する様々な機能を提供していることを指しています.

それではこれからこの4つの特徴それぞれについてどのような機能を提供しているのか見ていきましょう.
</i>
</details>


### 3.1. For all skill levels

* [自動機械学習 (AutoML)](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-automated-ml)
    - 機械学習の自動化による民主化・大規模 AI 開発の実現
* [デザイナー (ドラッグアンドドロップ ML)](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-designer)
    - マウスのドラッグ & ドロップで構築する機械学習パイプライン
* Python SDK + ノートブック (Python, R)
    - Python・R によるコードファーストアプローチ

![スキルレベルに応じた3つのインターフェース](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00008.png)

#### 3.1.1. 自動機械学習 (AutoML)

![自動機械学習 (AutoML)](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00009.png)

![Automated ML - 出力画面](assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00015.png)

#### 3.1.2. デザイナー (ドラッグアンドドロップ ML)

![デザイナー](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00011.png)

#### 3.1.3. Python SDK + ノートブック (Python 3.7+, R)
![Python SDK](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00012.png)

![Python Library](./assets/images/Azure-Machine-Learning-service-%E6%A6%82%E8%A6%81-JPN-asof-20190111_1280x720px-00006.png)

![ノートブック](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00014.png)

<details>
<summary>解説</summary>
<i>
For all skill leves に関してはまず自動機械学習 Automated Mchine Learning が挙げられます。ユーザはデータを投入し簡単な設定を行うだけで機械学習のモデル開発を自動で行います。完成したモデルを速やかにマウス操作のみでデプロイして利用していくこともできるようになっています。

現在は分類回帰時系列予測などメジャーな機械学習のタスクをサポートしています。例えば分類であれば品質管理であったり設備保全でご利用になります。また需要予測に関しては時系列予測の機能を使うことで

デザイナーと呼ばれるドラッグアンドドロップで機械学習のモデル開発のフローを定義していく機能もご提供しています。自動機械学習よりもより柔軟にカスタマイズ可能な機械学習のフローをマウスの操作のみで作り上げることができるようになっています。この機能は表形式データに適用することもできますし画像認識のシナリオでdeepラーニングの機能もビルトインされています。

またPython や R を使う方ももちろんご利用になります。Azure Machine Learning が提供する Python・R の SDKを利用することで Azure Machine Learning の様々な便利な機能にアクセスし、これまでよりも効率的に高速にPythonアールによる機械学習パイプラインの実装が可能になります。
</i>
</details>

#### 3.1.4. 参考リンク

* [Azure Machine Learning の対象ユーザー | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#who-is-azure-machine-learning-for)
* [チームの全員の生産性 | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#productivity-for-everyone-on-the-team)
* [ニーズを満たすクロス互換プラットフォーム ツール | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#cross-compatible-platform-tools-that-meet-your-needs)
* [スタジオ | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#studio)
* [特徴量化とアルゴリズムの選択の自動化 (AutoML) | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#automated-featurization-and-algorithm-selection-automl)


### 3.2. Industry leading MLOps

エンドーツーエンドの機械学習ライフサイクルを実現

![モニタリング](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00049.png)

![再学習のタイミング](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00050.png)

![MLOps なき機械学習プロジェクト](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00005.png)

![モデル精度変化](./assets/images/%E3%83%87%E3%83%BC%E3%82%BF%E3%82%B5%E3%82%A4%E3%82%A8%E3%83%B3%E3%83%86%E3%82%A3%E3%82%B9%E3%83%88%E3%81%AE%E3%81%9F%E3%82%81%E3%81%AEAzure-Machine-Learning-%E3%82%B5%E3%83%BC%E3%83%93%E3%82%B9%E3%81%94%E7%B4%B9%E4%BB%8B_full_1280x720px-00094.png)

![成熟度モデルの概要](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00013.png)

![MLOps = DevOps for AI](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00038.png)

![MLOps とは](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00004.png)

![MLOps を支える要素](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00010.png)

![MLOps を実現するための要素](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00011.png)

![MLOps の導入方法](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00012.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00041.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00042.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00043.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00044.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00045.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00046.png)

![MLops with Azure Machine Learning](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00047.png)

![MLOps Benefits](./assets/images/mlinsider_step_by_step_mlops_v1.01_1280x720px-00014.png)

<details>
<summary>解説</summary>
<i>
2つめの特徴の Industry Leading MLOps は、End-to-endの機械学習ライフサイクルを実現する仕組みをご提供していると言うことです.。

アジュールマシンラーニングを利用することでモデル学習やモデルのパッケージか検証ディプロイモニタリングの仕組みを実装することができますがこれらの個々のプロセスを例えば自動化するなどの仕組みを作ることができます。またアプリケーションとの連携を行うような仕組み作りも可能になります。具体的には Azure DevOps や GitHub などのサービスと組み合わせることによってより、より効率的に機械学習のプロセスを回すことができるため大規模なモデルの運用管理が可能になります   
Azure DevOps や Github にはアジュールマシンラーニングと結合できる接続できる拡張機能がご提供されているため統合も容易です.
</i>
</details>

#### 3.2.1. 参考リンク

* [MLOps: 機械学習モデル管理 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-model-management-and-deployment)


### 3.3. Open & Interoperable

オープンテクノロジーの採用による生産性の向上

![Python Library](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00013.png)

<details>
<summary>Compute Instance にプリインストールされているライブラリ一覧 (pip)</summary>
<pre>
$ pip list
Package                                 Version
--------------------------------------- -------------------
absl-py                                 0.13.0
adal                                    1.2.7
adlfs                                   2021.7.1
aiohttp                                 3.7.4.post0
ansiwrap                                0.8.4
antlr4-python3-runtime                  4.7.2
applicationinsights                     0.11.10
argcomplete                             1.12.3
argon2-cffi                             20.1.0
asgiref                                 3.4.1
astunparse                              1.6.3
async-timeout                           3.0.1
attrs                                   21.2.0
azure-appconfiguration                  1.1.1
azure-batch                             10.0.0
azure-cli                               2.26.1
azure-cli-core                          2.26.1
azure-cli-telemetry                     1.0.6
azure-common                            1.1.27
azure-core                              1.16.0
azure-cosmos                            3.2.0
azure-datalake-store                    0.0.52
azure-functions-devops-build            0.0.22
azure-graphrbac                         0.60.0
azure-identity                          1.6.0
azure-keyvault                          1.1.0
azure-keyvault-administration           4.0.0b3
azure-keyvault-certificates             4.3.0
azure-keyvault-keys                     4.4.0
azure-keyvault-secrets                  4.3.0
azure-loganalytics                      0.1.0
azure-mgmt-advisor                      9.0.0
azure-mgmt-apimanagement                0.2.0
azure-mgmt-appconfiguration             2.0.0
azure-mgmt-applicationinsights          1.0.0
azure-mgmt-authorization                0.61.0
azure-mgmt-batch                        15.0.0
azure-mgmt-batchai                      2.0.0
azure-mgmt-billing                      6.0.0
azure-mgmt-botservice                   0.3.0
azure-mgmt-cdn                          11.0.0
azure-mgmt-cognitiveservices            12.0.0
azure-mgmt-compute                      21.0.0
azure-mgmt-consumption                  2.0.0
azure-mgmt-containerinstance            1.5.0
azure-mgmt-containerregistry            8.0.0
azure-mgmt-containerservice             16.0.0
azure-mgmt-core                         1.2.2
azure-mgmt-cosmosdb                     6.4.0
azure-mgmt-databoxedge                  0.2.0
azure-mgmt-datalake-analytics           0.2.1
azure-mgmt-datalake-nspkg               3.0.1
azure-mgmt-datalake-store               0.5.0
azure-mgmt-datamigration                4.1.0
azure-mgmt-deploymentmanager            0.2.0
azure-mgmt-devtestlabs                  4.0.0
azure-mgmt-dns                          8.0.0
azure-mgmt-eventgrid                    9.0.0
azure-mgmt-eventhub                     4.1.0
azure-mgmt-extendedlocation             1.0.0b2
azure-mgmt-hdinsight                    8.0.0
azure-mgmt-imagebuilder                 0.4.0
azure-mgmt-iotcentral                   4.1.0
azure-mgmt-iothub                       2.0.0
azure-mgmt-iothubprovisioningservices   0.2.0
azure-mgmt-keyvault                     9.0.0
azure-mgmt-kusto                        0.3.0
azure-mgmt-loganalytics                 8.0.0
azure-mgmt-managedservices              1.0.0
azure-mgmt-managementgroups             0.2.0
azure-mgmt-maps                         0.1.0
azure-mgmt-marketplaceordering          1.1.0
azure-mgmt-media                        3.1.0
azure-mgmt-monitor                      2.0.0
azure-mgmt-msi                          0.2.0
azure-mgmt-netapp                       4.0.0
azure-mgmt-network                      19.0.0
azure-mgmt-nspkg                        3.0.2
azure-mgmt-policyinsights               0.5.0
azure-mgmt-privatedns                   1.0.0
azure-mgmt-rdbms                        8.1.0
azure-mgmt-recoveryservices             1.0.0
azure-mgmt-recoveryservicesbackup       0.12.0
azure-mgmt-redhatopenshift              0.1.0
azure-mgmt-redis                        7.0.0
azure-mgmt-relay                        0.1.0
azure-mgmt-reservations                 0.6.0
azure-mgmt-resource                     13.0.0
azure-mgmt-search                       8.0.0
azure-mgmt-security                     0.6.0
azure-mgmt-servicebus                   6.0.0
azure-mgmt-servicefabric                0.5.0
azure-mgmt-servicefabricmanagedclusters 1.0.0
azure-mgmt-signalr                      1.0.0b2
azure-mgmt-sql                          0.29.1
azure-mgmt-sqlvirtualmachine            0.5.0
azure-mgmt-storage                      18.0.0
azure-mgmt-synapse                      2.0.0
azure-mgmt-trafficmanager               0.51.0
azure-mgmt-web                          2.0.0
azure-multiapi-storage                  0.6.2
azure-nspkg                             3.0.2
azure-storage-blob                      12.8.1
azure-storage-common                    1.4.2
azure-storage-queue                     12.1.6
azure-synapse-accesscontrol             0.5.0
azure-synapse-artifacts                 0.6.0
azure-synapse-spark                     0.2.0
azureml-accel-models                    1.32.0
azureml-automl-core                     1.32.0
azureml-cli-common                      1.32.0
azureml-contrib-dataset                 1.32.0
azureml-contrib-fairness                1.32.0
azureml-contrib-notebook                1.32.0
azureml-contrib-pipeline-steps          1.32.0
azureml-contrib-reinforcementlearning   1.32.0
azureml-contrib-server                  1.32.0
azureml-contrib-services                1.32.0
azureml-core                            1.32.0
azureml-datadrift                       1.32.0
azureml-dataprep                        2.18.0
azureml-dataprep-native                 36.0.0
azureml-dataprep-rslex                  1.16.1
azureml-dataset-runtime                 1.32.0
azureml-defaults                        1.32.0
azureml-explain-model                   1.32.0
azureml-interpret                       1.32.0
azureml-mlflow                          1.32.0.post1
azureml-model-management-sdk            1.0.1b6.post1
azureml-opendatasets                    1.32.0
azureml-pipeline                        1.32.0
azureml-pipeline-core                   1.32.0
azureml-pipeline-steps                  1.32.0
azureml-sdk                             1.32.0
azureml-telemetry                       1.32.0
azureml-tensorboard                     1.32.0
azureml-train                           1.32.0
azureml-train-automl-client             1.32.0
azureml-train-core                      1.32.0
azureml-train-restclients-hyperdrive    1.32.0
azureml-widgets                         1.32.0
backcall                                0.2.0
backports.tempfile                      1.0
backports.weakref                       1.0.post1
bcrypt                                  3.2.0
beautifulsoup4                          4.9.3
bleach                                  3.3.1
blinker                                 1.4
blis                                    0.4.1
bokeh                                   2.3.3
boto                                    2.49.0
boto3                                   1.15.18
botocore                                1.18.18
Bottleneck                              1.3.2
brotlipy                                0.7.0
cached-property                         1.5.2
cachetools                              4.2.2
catalogue                               2.0.4
certifi                                 2021.5.30
cffi                                    1.14.6
chardet                                 4.0.0
charset-normalizer                      2.0.3
click                                   8.0.1
cloudpickle                             1.6.0
colorama                                0.4.4
configparser                            3.7.4
contextlib2                             0.6.0.post1
contextvars                             2.4
coremltools                             2.1.0
cramjam                                 2.3.2
cryptography                            3.4.7
cycler                                  0.10.0
cymem                                   2.0.5
Cython                                  0.29.21
dask                                    2021.7.0
dask-sql                                0.3.6
databricks-cli                          0.14.3
dataclasses                             0.8
datasets                                1.8.0
debugpy                                 1.3.0
decorator                               5.0.9
defusedxml                              0.7.1
Deprecated                              1.2.12
dice-ml                                 0.6.1
dill                                    0.3.4
distributed                             2021.7.0
distro                                  1.5.0
docker                                  4.4.4
dotnetcore2                             2.1.21
dowhy                                   0.6
econml                                  0.12.0b4
encrypted-inference                     0.9
entrypoints                             0.3
enum34                                  1.1.10
erroranalysis                           0.1.11
fabric                                  2.6.0
fairlearn                               0.7.0
fastai                                  1.0.61
fastapi                                 0.66.1
fastparquet                             0.7.0
fastprogress                            1.0.0
filelock                                3.0.12
fire                                    0.4.0
Flask                                   1.0.3
Flask-Cors                              3.0.10
flatbuffers                             1.12
fsspec                                  2021.7.0
fusepy                                  3.0.1
future                                  0.18.2
gast                                    0.3.3
gensim                                  3.8.3
gevent                                  21.1.2
gitdb                                   4.0.7
GitPython                               3.1.18
google-api-core                         1.30.0
google-auth                             1.34.0
google-auth-oauthlib                    0.4.4
google-pasta                            0.2.0
googleapis-common-protos                1.53.0
graphviz                                0.8.4
greenlet                                1.1.0
grpcio                                  1.38.1
gunicorn                                20.1.0
h11                                     0.12.0
h5py                                    2.10.0
HeapDict                                1.0.1
holidays                                0.9.11
horovod                                 0.22.1
huggingface-hub                         0.0.14
humanfriendly                           9.2
idna                                    3.1
immutables                              0.15
importlib-metadata                      4.6.4
interpret-community                     0.18.1
interpret-core                          0.2.4
invoke                                  1.6.0
ipykernel                               6.0.3
ipython                                 7.26.0
ipython-genutils                        0.2.0
ipywidgets                              7.6.3
isodate                                 0.6.0
itsdangerous                            2.0.1
javaproperties                          0.5.1
jedi                                    0.18.0
jeepney                                 0.6.0
Jinja2                                  2.11.2
jmespath                                0.10.0
joblib                                  1.0.1
JPype1                                  1.3.0
jsmin                                   2.2.2
json-logging-py                         0.2
jsondiff                                1.2.0
jsonpickle                              2.0.0
jsonschema                              3.2.0
jupyter-client                          6.1.12
jupyter-core                            4.7.1
jupyterlab-widgets                      1.0.0
Keras                                   2.3.1
Keras-Applications                      1.0.8
Keras-Preprocessing                     1.1.2
kiwisolver                              1.3.1
knack                                   0.8.2
liac-arff                               2.5.0
lightgbm                                2.3.0
llvmlite                                0.36.0
locket                                  0.2.1
lz4                                     3.1.3
Markdown                                3.3.4
MarkupSafe                              2.0.1
matplotlib                              3.4.2
matplotlib-inline                       0.1.2
mistune                                 0.8.4
mkl-fft                                 1.3.0
mkl-random                              1.2.2
mkl-service                             2.4.0
mlflow-skinny                           1.19.0
mpmath                                  1.2.1
msal                                    1.12.0
msal-extensions                         0.3.0
msgpack                                 1.0.2
msrest                                  0.6.21
msrestazure                             0.6.4
multidict                               5.1.0
multiprocess                            0.70.12.2
murmurhash                              1.0.5
mxnet                                   1.7.0.post1
nbconvert                               5.6.1
nbformat                                5.1.3
ndg-httpsclient                         0.5.1
nest-asyncio                            1.5.1
networkx                                2.5.1
notebook                                6.4.0
numba                                   0.53.1
numexpr                                 2.7.3
numpy                                   1.21.2
nvidia-ml-py3                           7.352.0
oauthlib                                3.1.1
olefile                                 0.46
opencensus                              0.7.13
opencensus-context                      0.1.2
opencensus-ext-azure                    1.0.8
opencv-python-headless                  4.5.3.56
opt-einsum                              3.3.0
packaging                               21.0
pandas                                  1.3.0
pandas-ml                               0.6.1
pandocfilters                           1.4.3
papermill                               1.2.1
paramiko                                2.7.2
parso                                   0.8.2
partd                                   1.2.0
pathlib2                                2.3.6
pathspec                                0.8.1
pathy                                   0.6.0
patsy                                   0.5.1
pexpect                                 4.8.0
pickleshare                             0.7.5
Pillow                                  8.3.1
pip                                     21.2.4
pkginfo                                 1.7.1
plac                                    1.1.3
pmdarima                                1.1.1
portalocker                             1.7.1
preshed                                 3.0.5
prometheus-client                       0.11.0
prompt-toolkit                          3.0.19
protobuf                                3.17.3
psutil                                  5.8.0
ptyprocess                              0.7.0
py-cpuinfo                              5.0.0
py4j                                    0.10.9
pyarrow                                 4.0.1
pyasn1                                  0.4.8
pyasn1-modules                          0.2.8
pycocotools                             2.0.2
pycparser                               2.20
pydantic                                1.8.2
pyDeprecate                             0.3.1
pydot                                   1.4.2
PyGithub                                1.55
Pygments                                2.9.0
PyJWT                                   2.1.0
PyNaCl                                  1.4.0
pyOpenSSL                               20.0.1
pyparsing                               2.4.7
pyrsistent                              0.18.0
PySocks                                 1.7.1
pyspark                                 3.1.2
python-dateutil                         2.8.2
python-snappy                           0.6.0
pytorch-lightning                       1.4.2
pytorch-transformers                    1.0.0
pytz                                    2019.1
pyu2f                                   0.1.5
PyYAML                                  5.4.1
pyzmq                                   22.2.1
rai-core-flask                          0.2.2
raiwidgets                              0.7.0
regex                                   2021.7.6
requests                                2.26.0
requests-oauthlib                       1.3.0
responsibleai                           0.7.0
rsa                                     4.7.2
ruamel.yaml                             0.17.4
ruamel.yaml.clib                        0.2.2
s3transfer                              0.3.7
sacremoses                              0.0.45
scikit-learn                            0.24.2
scipy                                   1.7.0
scp                                     0.13.6
seaborn                                 0.11.1
SecretStorage                           3.3.1
semver                                  2.13.0
Send2Trash                              1.7.1
sentencepiece                           0.1.96
seqeval                                 1.2.2
setuptools                              50.3.0.post20201006
setuptools-git                          1.2
shap                                    0.39.0
six                                     1.16.0
sklearn                                 0.0
sklearn-pandas                          2.2.0
slicer                                  0.0.7
smart-open                              5.1.0
smmap                                   4.0.0
sortedcontainers                        2.4.0
soupsieve                               2.2.1
spacy                                   3.1.1
spacy-legacy                            3.0.8
sparse                                  0.12.0
srsly                                   2.4.1
sshtunnel                               0.1.5
starlette                               0.14.2
statsmodels                             0.12.2
sympy                                   1.8
tabulate                                0.8.9
tblib                                   1.7.0
tenacity                                8.0.1
tensorboard                             2.6.0
tensorboard-data-server                 0.6.1
tensorboard-plugin-wit                  1.8.0
tensorflow                              2.4.1
tensorflow-estimator                    2.4.0
tensorflow-gpu                          2.3.0
termcolor                               1.1.0
terminado                               0.10.1
testpath                                0.5.0
textwrap3                               0.9.2
thinc                                   8.0.8
threadpoolctl                           2.2.0
thrift                                  0.13.0
tokenizers                              0.10.3
toolz                                   0.11.1
torch                                   1.9.0
torch-tb-profiler                       0.2.1
torchaudio                              0.9.0a0+33b2469
torchmetrics                            0.5.0
torchvision                             0.10.0
tornado                                 6.1
tqdm                                    4.62.1
traitlets                               5.0.5
transformers                            4.5.1
typer                                   0.3.2
typing-extensions                       3.10.0.0
tzlocal                                 2.1
urllib3                                 1.26.6
uuid                                    1.30
uvicorn                                 0.14.0
vsts                                    0.1.25
wasabi                                  0.8.2
wcwidth                                 0.2.5
webencodings                            0.5.1
websocket-client                        0.56.0
Werkzeug                                2.0.1
wheel                                   0.35.1
widgetsnbextension                      3.5.1
wrapt                                   1.12.1
xgboost                                 1.3.3
xmltodict                               0.12.0
xxhash                                  2.0.2
yarl                                    1.6.3
zict                                    2.0.0
zipp                                    3.5.0
zope.event                              4.5.0
zope.interface                          5.4.0
</pre>
</details>

<details>
<summary>Compute Instance にプリインストールされているライブラリ一覧 (anaconda)</summary>
<pre>
$ conda list
  packages in environment at /anaconda/envs/azureml_py38:

  Name                    Version                   Build  Channel
_libgcc_mutex             0.1                        main  
_openmp_mutex             4.5                       1_gnu  
_py-xgboost-mutex         2.0                       cpu_0  
_sysroot_linux-64_curr_repodata_hack 3                   haa98f57_10  
absl-py                   0.13.0             pyhd8ed1ab_0    conda-forge
adal                      1.2.7                    pypi_0    pypi
adlfs                     2021.7.1                 pypi_0    pypi
aiohttp                   3.7.4.post0      py38h497a2fe_0    conda-forge
ansiwrap                  0.8.4                    pypi_0    pypi
antlr4-python3-runtime    4.7.2                    pypi_0    pypi
applicationinsights       0.11.10                  pypi_0    pypi
argcomplete               1.12.3                   pypi_0    pypi
argon2-cffi               20.1.0                   pypi_0    pypi
asgiref                   3.4.1                    pypi_0    pypi
astunparse                1.6.3                    pypi_0    pypi
async-timeout             3.0.1                   py_1000    conda-forge
attrs                     21.2.0             pyhd8ed1ab_0    conda-forge
azure-appconfiguration    1.1.1                    pypi_0    pypi
azure-batch               10.0.0                   pypi_0    pypi
azure-cli                 2.26.1                   pypi_0    pypi
azure-cli-core            2.26.1                   pypi_0    pypi
azure-cli-telemetry       1.0.6                    pypi_0    pypi
azure-common              1.1.27                   pypi_0    pypi
azure-core                1.16.0                   pypi_0    pypi
azure-cosmos              3.2.0                    pypi_0    pypi
azure-datalake-store      0.0.52                   pypi_0    pypi
azure-functions-devops-build 0.0.22                   pypi_0    pypi
azure-graphrbac           0.60.0                   pypi_0    pypi
azure-identity            1.6.0                    pypi_0    pypi
azure-keyvault            1.1.0                    pypi_0    pypi
azure-keyvault-administration 4.0.0b3                  pypi_0    pypi
azure-keyvault-certificates 4.3.0                    pypi_0    pypi
azure-keyvault-keys       4.4.0                    pypi_0    pypi
azure-keyvault-secrets    4.3.0                    pypi_0    pypi
azure-loganalytics        0.1.0                    pypi_0    pypi
azure-mgmt-advisor        9.0.0                    pypi_0    pypi
azure-mgmt-apimanagement  0.2.0                    pypi_0    pypi
azure-mgmt-appconfiguration 2.0.0                    pypi_0    pypi
azure-mgmt-applicationinsights 1.0.0                    pypi_0    pypi
azure-mgmt-authorization  0.61.0                   pypi_0    pypi
azure-mgmt-batch          15.0.0                   pypi_0    pypi
azure-mgmt-batchai        2.0.0                    pypi_0    pypi
azure-mgmt-billing        6.0.0                    pypi_0    pypi
azure-mgmt-botservice     0.3.0                    pypi_0    pypi
azure-mgmt-cdn            11.0.0                   pypi_0    pypi
azure-mgmt-cognitiveservices 12.0.0                   pypi_0    pypi
azure-mgmt-compute        21.0.0                   pypi_0    pypi
azure-mgmt-consumption    2.0.0                    pypi_0    pypi
azure-mgmt-containerinstance 1.5.0                    pypi_0    pypi
azure-mgmt-containerregistry 8.0.0                    pypi_0    pypi
azure-mgmt-containerservice 16.0.0                   pypi_0    pypi
azure-mgmt-core           1.2.2                    pypi_0    pypi
azure-mgmt-cosmosdb       6.4.0                    pypi_0    pypi
azure-mgmt-databoxedge    0.2.0                    pypi_0    pypi
azure-mgmt-datalake-analytics 0.2.1                    pypi_0    pypi
azure-mgmt-datalake-nspkg 3.0.1                    pypi_0    pypi
azure-mgmt-datalake-store 0.5.0                    pypi_0    pypi
azure-mgmt-datamigration  4.1.0                    pypi_0    pypi
azure-mgmt-deploymentmanager 0.2.0                    pypi_0    pypi
azure-mgmt-devtestlabs    4.0.0                    pypi_0    pypi
azure-mgmt-dns            8.0.0                    pypi_0    pypi
azure-mgmt-eventgrid      9.0.0                    pypi_0    pypi
azure-mgmt-eventhub       4.1.0                    pypi_0    pypi
azure-mgmt-extendedlocation 1.0.0b2                  pypi_0    pypi
azure-mgmt-hdinsight      8.0.0                    pypi_0    pypi
azure-mgmt-imagebuilder   0.4.0                    pypi_0    pypi
azure-mgmt-iotcentral     4.1.0                    pypi_0    pypi
azure-mgmt-iothub         2.0.0                    pypi_0    pypi
azure-mgmt-iothubprovisioningservices 0.2.0                    pypi_0    pypi
azure-mgmt-keyvault       9.0.0                    pypi_0    pypi
azure-mgmt-kusto          0.3.0                    pypi_0    pypi
azure-mgmt-loganalytics   8.0.0                    pypi_0    pypi
azure-mgmt-managedservices 1.0.0                    pypi_0    pypi
azure-mgmt-managementgroups 0.2.0                    pypi_0    pypi
azure-mgmt-maps           0.1.0                    pypi_0    pypi
azure-mgmt-marketplaceordering 1.1.0                    pypi_0    pypi
azure-mgmt-media          3.1.0                    pypi_0    pypi
azure-mgmt-monitor        2.0.0                    pypi_0    pypi
azure-mgmt-msi            0.2.0                    pypi_0    pypi
azure-mgmt-netapp         4.0.0                    pypi_0    pypi
azure-mgmt-network        19.0.0                   pypi_0    pypi
azure-mgmt-nspkg          3.0.2                    pypi_0    pypi
azure-mgmt-policyinsights 0.5.0                    pypi_0    pypi
azure-mgmt-privatedns     1.0.0                    pypi_0    pypi
azure-mgmt-rdbms          8.1.0                    pypi_0    pypi
azure-mgmt-recoveryservices 1.0.0                    pypi_0    pypi
azure-mgmt-recoveryservicesbackup 0.12.0                   pypi_0    pypi
azure-mgmt-redhatopenshift 0.1.0                    pypi_0    pypi
azure-mgmt-redis          7.0.0                    pypi_0    pypi
azure-mgmt-relay          0.1.0                    pypi_0    pypi
azure-mgmt-reservations   0.6.0                    pypi_0    pypi
azure-mgmt-resource       13.0.0                   pypi_0    pypi
azure-mgmt-search         8.0.0                    pypi_0    pypi
azure-mgmt-security       0.6.0                    pypi_0    pypi
azure-mgmt-servicebus     6.0.0                    pypi_0    pypi
azure-mgmt-servicefabric  0.5.0                    pypi_0    pypi
azure-mgmt-servicefabricmanagedclusters 1.0.0                    pypi_0    pypi
azure-mgmt-signalr        1.0.0b2                  pypi_0    pypi
azure-mgmt-sql            0.29.1                   pypi_0    pypi
azure-mgmt-sqlvirtualmachine 0.5.0                    pypi_0    pypi
azure-mgmt-storage        18.0.0                   pypi_0    pypi
azure-mgmt-synapse        2.0.0                    pypi_0    pypi
azure-mgmt-trafficmanager 0.51.0                   pypi_0    pypi
azure-mgmt-web            2.0.0                    pypi_0    pypi
azure-multiapi-storage    0.6.2                    pypi_0    pypi
azure-nspkg               3.0.2                    pypi_0    pypi
azure-storage-blob        12.8.1                   pypi_0    pypi
azure-storage-common      1.4.2                    pypi_0    pypi
azure-storage-queue       12.1.6                   pypi_0    pypi
azure-synapse-accesscontrol 0.5.0                    pypi_0    pypi
azure-synapse-artifacts   0.6.0                    pypi_0    pypi
azure-synapse-spark       0.2.0                    pypi_0    pypi
azureml-accel-models      1.32.0                   pypi_0    pypi
azureml-automl-core       1.32.0                   pypi_0    pypi
azureml-cli-common        1.32.0                   pypi_0    pypi
azureml-contrib-dataset   1.32.0                   pypi_0    pypi
azureml-contrib-fairness  1.32.0                   pypi_0    pypi
azureml-contrib-notebook  1.32.0                   pypi_0    pypi
azureml-contrib-pipeline-steps 1.32.0                   pypi_0    pypi
azureml-contrib-reinforcementlearning 1.32.0                   pypi_0    pypi
azureml-contrib-server    1.32.0                   pypi_0    pypi
azureml-contrib-services  1.32.0                   pypi_0    pypi
azureml-core              1.32.0                   pypi_0    pypi
azureml-datadrift         1.32.0                   pypi_0    pypi
azureml-dataprep          2.18.0                   pypi_0    pypi
azureml-dataprep-native   36.0.0                   pypi_0    pypi
azureml-dataprep-rslex    1.16.1                   pypi_0    pypi
azureml-dataset-runtime   1.32.0                   pypi_0    pypi
azureml-defaults          1.32.0                   pypi_0    pypi
azureml-explain-model     1.32.0                   pypi_0    pypi
azureml-interpret         1.32.0                   pypi_0    pypi
azureml-mlflow            1.32.0.post1             pypi_0    pypi
azureml-model-management-sdk 1.0.1b6.post1            pypi_0    pypi
azureml-opendatasets      1.32.0                   pypi_0    pypi
azureml-pipeline          1.32.0                   pypi_0    pypi
azureml-pipeline-core     1.32.0                   pypi_0    pypi
azureml-pipeline-steps    1.32.0                   pypi_0    pypi
azureml-sdk               1.32.0                   pypi_0    pypi
azureml-telemetry         1.32.0                   pypi_0    pypi
azureml-tensorboard       1.32.0                   pypi_0    pypi
azureml-train             1.32.0                   pypi_0    pypi
azureml-train-automl-client 1.32.0                   pypi_0    pypi
azureml-train-core        1.32.0                   pypi_0    pypi
azureml-train-restclients-hyperdrive 1.32.0                   pypi_0    pypi
azureml-widgets           1.32.0                   pypi_0    pypi
backcall                  0.2.0              pyhd3eb1b0_0  
backports-tempfile        1.0                      pypi_0    pypi
backports-weakref         1.0.post1                pypi_0    pypi
bcrypt                    3.2.0                    pypi_0    pypi
beautifulsoup4            4.9.3                    pypi_0    pypi
binutils_impl_linux-64    2.35.1               h27ae35d_9  
binutils_linux-64         2.35.1              h454624a_30  
blas                      1.0                         mkl  
bleach                    3.3.1                    pypi_0    pypi
blinker                   1.4                        py_1    conda-forge
blis                      0.4.1                    pypi_0    pypi
bokeh                     2.3.3                    pypi_0    pypi
boto                      2.49.0                   pypi_0    pypi
boto3                     1.15.18                  pypi_0    pypi
botocore                  1.18.18                  pypi_0    pypi
bottleneck                1.3.2                    pypi_0    pypi
brotlipy                  0.7.0           py38h497a2fe_1001    conda-forge
c-ares                    1.17.1               h27cfd23_0  
ca-certificates           2021.7.5             h06a4308_1  
cached-property           1.5.2                    pypi_0    pypi
cachetools                4.2.2              pyhd8ed1ab_0    conda-forge
catalogue                 2.0.4                    pypi_0    pypi
certifi                   2021.5.30        py38h06a4308_0  
cffi                      1.14.5                   pypi_0    pypi
chardet                   4.0.0            py38h578d9bd_1    conda-forge
charset-normalizer        2.0.3                    pypi_0    pypi
click                     7.1.2                    pypi_0    pypi
cloudpickle               1.6.0                    pypi_0    pypi
colorama                  0.4.4              pyh9f0ad1d_0    conda-forge
configparser              3.7.4                    pypi_0    pypi
contextlib2               0.6.0.post1              pypi_0    pypi
contextvars               2.4                      pypi_0    pypi
coremltools               2.1.0                    pypi_0    pypi
cramjam                   2.3.2                    pypi_0    pypi
cryptography              3.3.2                    pypi_0    pypi
cudatoolkit               10.2.89              hfd86e86_1  
cycler                    0.10.0                   pypi_0    pypi
cymem                     2.0.5                    pypi_0    pypi
cython                    0.29.21                  pypi_0    pypi
dask                      2021.7.0                 pypi_0    pypi
dask-sql                  0.3.6                    pypi_0    pypi
databricks-cli            0.14.3                   pypi_0    pypi
dataclasses               0.6                      pypi_0    pypi
datasets                  1.8.0                    pypi_0    pypi
debugpy                   1.3.0                    pypi_0    pypi
decorator                 5.0.9              pyhd3eb1b0_0  
defusedxml                0.7.1                    pypi_0    pypi
deprecated                1.2.12                   pypi_0    pypi
dice-ml                   0.6.1                    pypi_0    pypi
dill                      0.3.4                    pypi_0    pypi
distributed               2021.7.0                 pypi_0    pypi
distro                    1.5.0                    pypi_0    pypi
docker                    4.4.4                    pypi_0    pypi
dotnetcore2               2.1.21                   pypi_0    pypi
dowhy                     0.6                      pypi_0    pypi
econml                    0.12.0b4                 pypi_0    pypi
encrypted-inference       0.9                      pypi_0    pypi
entrypoints               0.3                      pypi_0    pypi
enum34                    1.1.10                   pypi_0    pypi
erroranalysis             0.1.11                   pypi_0    pypi
fabric                    2.6.0                    pypi_0    pypi
fairlearn                 0.7.0                    pypi_0    pypi
fastai                    1.0.61                   pypi_0    pypi
fastapi                   0.66.1                   pypi_0    pypi
fastparquet               0.7.0                    pypi_0    pypi
fastprogress              1.0.0                    pypi_0    pypi
filelock                  3.0.12                   pypi_0    pypi
fire                      0.4.0                    pypi_0    pypi
flask                     1.0.3                    pypi_0    pypi
flask-cors                3.0.10                   pypi_0    pypi
flatbuffers               1.12                     pypi_0    pypi
freetype                  2.10.4               h5ab3b9f_0  
fsspec                    2021.7.0           pyhd8ed1ab_0    conda-forge
fusepy                    3.0.1                    pypi_0    pypi
future                    0.18.2           py38h578d9bd_3    conda-forge
gast                      0.3.3                    pypi_0    pypi
gcc_impl_linux-64         9.3.0               h6df7d76_17  
gcc_linux-64              9.3.0               h1ee779e_30  
gensim                    3.8.3                    pypi_0    pypi
gevent                    21.1.2                   pypi_0    pypi
gitdb                     4.0.7                    pypi_0    pypi
gitpython                 3.1.18                   pypi_0    pypi
google-api-core           1.30.0                   pypi_0    pypi
google-auth               1.32.1                   pypi_0    pypi
google-auth-oauthlib      0.4.4                    pypi_0    pypi
google-pasta              0.2.0                    pypi_0    pypi
googleapis-common-protos  1.53.0                   pypi_0    pypi
greenlet                  1.1.0                    pypi_0    pypi
grpcio                    1.32.0                   pypi_0    pypi
gunicorn                  20.1.0                   pypi_0    pypi
gxx_impl_linux-64         9.3.0               hbdd7822_17  
gxx_linux-64              9.3.0               h7e70986_30  
h11                       0.12.0                   pypi_0    pypi
h5py                      2.10.0                   pypi_0    pypi
heapdict                  1.0.1                    pypi_0    pypi
holidays                  0.9.11                   pypi_0    pypi
horovod                   0.22.1                   pypi_0    pypi
huggingface-hub           0.0.14                   pypi_0    pypi
humanfriendly             9.2                      pypi_0    pypi
idna                      2.10                     pypi_0    pypi
immutables                0.15                     pypi_0    pypi
importlib-metadata        4.6.0                    pypi_0    pypi
intel-openmp              2021.3.0          h06a4308_3350  
interpret-community       0.18.1                   pypi_0    pypi
interpret-core            0.2.4                    pypi_0    pypi
invoke                    1.6.0                    pypi_0    pypi
ipykernel                 6.0.3                    pypi_0    pypi
ipython                   7.16.1                   pypi_0    pypi
ipython_genutils          0.2.0              pyhd3eb1b0_1  
ipywidgets                7.6.3                    pypi_0    pypi
isodate                   0.6.0                    pypi_0    pypi
itsdangerous              2.0.1                    pypi_0    pypi
javaproperties            0.5.1                    pypi_0    pypi
jedi                      0.17.2                   pypi_0    pypi
jeepney                   0.6.0                    pypi_0    pypi
jinja2                    2.11.2                   pypi_0    pypi
jmespath                  0.10.0                   pypi_0    pypi
joblib                    0.14.1                   pypi_0    pypi
jpeg                      9b                   h024ee3a_2  
jpype1                    1.3.0                    pypi_0    pypi
jsmin                     2.2.2                    pypi_0    pypi
json-logging-py           0.2                      pypi_0    pypi
jsondiff                  1.2.0                    pypi_0    pypi
jsonpickle                2.0.0                    pypi_0    pypi
jsonschema                3.2.0                    pypi_0    pypi
jupyter_client            6.1.12             pyhd3eb1b0_0  
jupyter_core              4.7.1            py38h06a4308_0  
jupyterlab-widgets        1.0.0                    pypi_0    pypi
keras                     2.3.1                    pypi_0    pypi
keras-applications        1.0.8                    pypi_0    pypi
keras-preprocessing       1.1.2                    pypi_0    pypi
kernel-headers_linux-64   3.10.0              h57e8cba_10  
kiwisolver                1.3.1                    pypi_0    pypi
knack                     0.8.2                    pypi_0    pypi
ld_impl_linux-64          2.35.1               h7274673_9  
liac-arff                 2.5.0                    pypi_0    pypi
libedit                   3.1.20210216         h27cfd23_1  
libffi                    3.3                  he6710b0_2  
libgcc-devel_linux-64     9.3.0               hb95220a_17  
libgcc-ng                 9.3.0               h5101ec6_17  
libgfortran-ng            7.5.0               ha8ba4b0_17  
libgfortran4              7.5.0               ha8ba4b0_17  
libgomp                   9.3.0               h5101ec6_17  
libpng                    1.6.37               hbc83047_0  
libprotobuf               3.17.2               h780b84a_1    conda-forge
libsodium                 1.0.18               h7b6447c_0  
libstdcxx-devel_linux-64  9.3.0               hf0c5c8d_17  
libstdcxx-ng              9.3.0               hd4cf53a_17  
libtiff                   4.2.0                h85742a9_0  
libuv                     1.40.0               h7b6447c_0  
libwebp-base              1.2.0                h27cfd23_0  
libxgboost                1.3.3                h2531618_0  
lightgbm                  2.3.0                    pypi_0    pypi
llvmlite                  0.36.0                   pypi_0    pypi
locket                    0.2.1                    pypi_0    pypi
lz4                       3.1.3                    pypi_0    pypi
lz4-c                     1.9.3                h295c915_1  
markdown                  3.3.4              pyhd8ed1ab_0    conda-forge
markupsafe                2.0.1                    pypi_0    pypi
matplotlib                3.4.2                    pypi_0    pypi
matplotlib-inline         0.1.2              pyhd3eb1b0_2  
mistune                   0.8.4                    pypi_0    pypi
mkl                       2021.3.0           h06a4308_520  
mkl-service               2.4.0            py38h7f8727e_0  
mkl_fft                   1.3.0            py38h42c9631_2  
mkl_random                1.2.2            py38h51133e4_0  
mlflow-skinny             1.19.0                   pypi_0    pypi
mpmath                    1.2.1                    pypi_0    pypi
msal                      1.12.0                   pypi_0    pypi
msal-extensions           0.3.0                    pypi_0    pypi
msgpack                   1.0.2                    pypi_0    pypi
msrest                    0.6.21                   pypi_0    pypi
msrestazure               0.6.4                    pypi_0    pypi
multidict                 5.1.0            py38h497a2fe_1    conda-forge
multiprocess              0.70.12.2                pypi_0    pypi
murmurhash                1.0.5                    pypi_0    pypi
mxnet                     1.7.0.post1              pypi_0    pypi
nbconvert                 5.6.1                    pypi_0    pypi
nbformat                  5.1.3                    pypi_0    pypi
ncurses                   6.2                  he6710b0_1  
ndg-httpsclient           0.5.1                    pypi_0    pypi
nest-asyncio              1.5.1                    pypi_0    pypi
networkx                  2.5.1                    pypi_0    pypi
ninja                     1.10.2               hff7bd54_1  
notebook                  6.4.0                    pypi_0    pypi
numba                     0.53.1                   pypi_0    pypi
numexpr                   2.7.3                    pypi_0    pypi
numpy                     1.21.2                   pypi_0    pypi
numpy-base                1.20.3           py38h74d4b33_0  
nvidia-ml-py3             7.352.0                  pypi_0    pypi
oauthlib                  3.1.1              pyhd8ed1ab_0    conda-forge
olefile                   0.46                       py_0  
opencensus                0.7.13                   pypi_0    pypi
opencensus-context        0.1.2                    pypi_0    pypi
opencensus-ext-azure      1.0.8                    pypi_0    pypi
opencv-python-headless    4.5.3.56                 pypi_0    pypi
openssl                   1.1.1k               h27cfd23_0  
opt-einsum                3.3.0                    pypi_0    pypi
packaging                 20.9                     pypi_0    pypi
pandas                    1.3.0                    pypi_0    pypi
pandas-ml                 0.6.1                    pypi_0    pypi
pandocfilters             1.4.3                    pypi_0    pypi
papermill                 1.2.1                    pypi_0    pypi
paramiko                  2.7.2                    pypi_0    pypi
parso                     0.8.2              pyhd3eb1b0_0  
partd                     1.2.0                    pypi_0    pypi
pathlib2                  2.3.6                    pypi_0    pypi
pathspec                  0.8.1                    pypi_0    pypi
pathy                     0.6.0                    pypi_0    pypi
patsy                     0.5.1                    pypi_0    pypi
pexpect                   4.8.0              pyhd3eb1b0_3  
pickleshare               0.7.5           pyhd3eb1b0_1003  
pillow                    8.3.1                    pypi_0    pypi
pip                       21.2.4                   pypi_0    pypi
pkginfo                   1.7.1                    pypi_0    pypi
plac                      1.1.3                    pypi_0    pypi
pmdarima                  1.1.1                    pypi_0    pypi
portalocker               1.7.1                    pypi_0    pypi
preshed                   3.0.5                    pypi_0    pypi
prometheus-client         0.11.0                   pypi_0    pypi
prompt-toolkit            3.0.19                   pypi_0    pypi
protobuf                  3.17.3                   pypi_0    pypi
psutil                    5.8.0                    pypi_0    pypi
ptyprocess                0.7.0              pyhd3eb1b0_2  
py-cpuinfo                5.0.0                    pypi_0    pypi
py-xgboost                1.3.3            py38h06a4308_0  
py4j                      0.10.9                   pypi_0    pypi
pyarrow                   4.0.1                    pypi_0    pypi
pyasn1                    0.4.8                      py_0    conda-forge
pyasn1-modules            0.2.8                    pypi_0    pypi
pycocotools               2.0.2                    pypi_0    pypi
pycparser                 2.20               pyh9f0ad1d_2    conda-forge
pydantic                  1.8.2                    pypi_0    pypi
pydeprecate               0.3.1              pyhd8ed1ab_0    conda-forge
pydot                     1.4.2                    pypi_0    pypi
pygithub                  1.55                     pypi_0    pypi
pygments                  2.9.0              pyhd3eb1b0_0  
pyjwt                     2.1.0              pyhd8ed1ab_0    conda-forge
pynacl                    1.4.0                    pypi_0    pypi
pyopenssl                 20.0.1             pyhd8ed1ab_0    conda-forge
pyparsing                 2.4.7              pyh9f0ad1d_0    conda-forge
pyrsistent                0.18.0                   pypi_0    pypi
pysocks                   1.7.1            py38h578d9bd_3    conda-forge
pyspark                   3.1.2                    pypi_0    pypi
python                    3.8.1                h0371630_1    anaconda
python-dateutil           2.8.2              pyhd3eb1b0_0  
python-graphviz           0.8.4                    pypi_0    pypi
python-snappy             0.6.0                    pypi_0    pypi
python_abi                3.8                      2_cp38    conda-forge
pytorch-lightning         1.4.2              pyhd8ed1ab_0    conda-forge
pytorch-transformers      1.0.0                    pypi_0    pypi
pytz                      2019.1                   pypi_0    pypi
pyu2f                     0.1.5              pyhd8ed1ab_0    conda-forge
pyyaml                    5.4.1                    pypi_0    pypi
pyzmq                     22.1.0                   pypi_0    pypi
rai-core-flask            0.2.2                    pypi_0    pypi
raiwidgets                0.7.0                    pypi_0    pypi
readline                  7.0                  h7b6447c_5  
regex                     2021.7.6                 pypi_0    pypi
requests                  2.25.1                   pypi_0    pypi
requests-oauthlib         1.3.0              pyh9f0ad1d_0    conda-forge
responsibleai             0.7.0                    pypi_0    pypi
rsa                       4.7.2              pyh44b312d_0    conda-forge
ruamel-yaml               0.17.4                   pypi_0    pypi
ruamel-yaml-clib          0.2.2                    pypi_0    pypi
s3transfer                0.3.7                    pypi_0    pypi
sacremoses                0.0.45                   pypi_0    pypi
scikit-learn              0.24.2           py38ha9443f7_0  
scipy                     1.7.0                    pypi_0    pypi
scp                       0.13.6                   pypi_0    pypi
seaborn                   0.11.1                   pypi_0    pypi
secretstorage             3.3.1                    pypi_0    pypi
semver                    2.13.0                   pypi_0    pypi
send2trash                1.7.1                    pypi_0    pypi
sentencepiece             0.1.96                   pypi_0    pypi
seqeval                   1.2.2                    pypi_0    pypi
setuptools                50.3.0           py38hb0f4dca_1    anaconda
setuptools-git            1.2                        py_1    anaconda
shap                      0.39.0                   pypi_0    pypi
six                       1.16.0             pyhd3eb1b0_0  
sklearn                   0.0                      pypi_0    pypi
sklearn-pandas            2.2.0                    pypi_0    pypi
slicer                    0.0.7                    pypi_0    pypi
smart-open                5.1.0                    pypi_0    pypi
smmap                     4.0.0                    pypi_0    pypi
sortedcontainers          2.4.0                    pypi_0    pypi
soupsieve                 2.2.1                    pypi_0    pypi
spacy                     3.1.1                    pypi_0    pypi
spacy-legacy              3.0.8                    pypi_0    pypi
sparse                    0.12.0                   pypi_0    pypi
sqlite                    3.33.0               h62c20be_0    anaconda
srsly                     2.4.1                    pypi_0    pypi
sshtunnel                 0.1.5                    pypi_0    pypi
starlette                 0.14.2                   pypi_0    pypi
statsmodels               0.12.2                   pypi_0    pypi
sympy                     1.8                      pypi_0    pypi
sysroot_linux-64          2.17                h57e8cba_10  
tabulate                  0.8.9                    pypi_0    pypi
tblib                     1.7.0                    pypi_0    pypi
tenacity                  8.0.1                    pypi_0    pypi
tensorboard               2.6.0              pyhd8ed1ab_0    conda-forge
tensorboard-data-server   0.6.1                    pypi_0    pypi
tensorboard-plugin-wit    1.8.0              pyh44b312d_0    conda-forge
tensorflow                2.4.1                    pypi_0    pypi
tensorflow-estimator      2.4.0                    pypi_0    pypi
tensorflow-gpu            2.3.0                    pypi_0    pypi
termcolor                 1.1.0                    pypi_0    pypi
terminado                 0.10.1                   pypi_0    pypi
testpath                  0.5.0                    pypi_0    pypi
textwrap3                 0.9.2                    pypi_0    pypi
thinc                     8.0.8                    pypi_0    pypi
threadpoolctl             2.2.0              pyhbf3da8f_0  
thrift                    0.13.0                   pypi_0    pypi
tk                        8.6.10               hbc83047_0  
tokenizers                0.10.3                   pypi_0    pypi
toolz                     0.11.1                   pypi_0    pypi
torch                     1.9.0                    pypi_0    pypi
torch-tb-profiler         0.2.1                    pypi_0    pypi
torchaudio                0.9.0                      py38    pytorch
torchmetrics              0.5.0              pyhd8ed1ab_0    conda-forge
torchvision               0.10.0                   pypi_0    pypi
tornado                   6.1              py38h27cfd23_0  
tqdm                      4.61.1                   pypi_0    pypi
traitlets                 4.3.3                    pypi_0    pypi
transformers              4.5.1                    pypi_0    pypi
typer                     0.3.2                    pypi_0    pypi
typing-extensions         3.10.0.0             hd3eb1b0_0  
typing_extensions         3.10.0.0           pyh06a4308_0  
tzlocal                   2.1                      pypi_0    pypi
urllib3                   1.26.6             pyhd8ed1ab_0    conda-forge
uuid                      1.30                     pypi_0    pypi
uvicorn                   0.14.0                   pypi_0    pypi
vsts                      0.1.25                   pypi_0    pypi
wasabi                    0.8.2                    pypi_0    pypi
wcwidth                   0.2.5                      py_0  
webencodings              0.5.1                    pypi_0    pypi
websocket-client          0.56.0                   pypi_0    pypi
werkzeug                  1.0.1                    pypi_0    pypi
wheel                     0.35.1                     py_0    anaconda
widgetsnbextension        3.5.1                    pypi_0    pypi
wrapt                     1.12.1                   pypi_0    pypi
xmltodict                 0.12.0                   pypi_0    pypi
xxhash                    2.0.2                    pypi_0    pypi
xz                        5.2.5                h7b6447c_0  
yaml                      0.2.5                h516909a_0    conda-forge
yarl                      1.6.3            py38h497a2fe_2    conda-forge
zeromq                    4.3.4                h2531618_0  
zict                      2.0.0                    pypi_0    pypi
zipp                      3.4.1                    pypi_0    pypi
zlib                      1.2.11               h7b6447c_3  
zope-event                4.5.0                    pypi_0    pypi
zope-interface            5.4.0                    pypi_0    pypi
zstd                      1.4.9                haebb681_0
</pre>
</details>

![Open Platform 連携](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00015.png)

![mlflow](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00016.png)

![モデル標準フォーマット "ONNX"](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00017.png)

![ONNX Partners](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00018.png)

![ONNX Runtime](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00019.png)

![ONNX 作成とデプロイ](./assets/images/onnx.png)

![モデルはあらゆる用途で活用可能](./assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00024.png)

![パワフルなAIチップ](./assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00023.png)

![Azure IoT Edge](./assets/images/Azure-Machine-Learning-service-概要-JPN-asof-20190111_1280x720px-00025.png)

![VoTT](./assets/images/AzureMachineLearningService2019May1.2_1280x720px-00067.png)

<details>
<summary>解説</summary>
<i>
3つ目の特徴に入っていきます。 Open & Interoperatable は、オープンテクノロジーの採用による生産性の向上を意味します。

Azure Machine Learning は特定の技術にロックインされることなく様々なオープンのテクノロジーを利用することもできるようになっています。

機械学習のモデル開発で利用する様々なオープンソースの機械学習フレームワーク、PyTorchや Scikit-Learn などがご利用になれます。

またPython や R などのプログラミング言語を、普段使いなれた開発ツール、例えば Jupyter Notebook、VisualStudioコード上で利用していくこともできるようになっています。
</i>
</details>

#### 3.3.1. 参考リンク

* [オープン性と相互運用性 | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#open-and-interoperable)
* [オープンソースの機械学習 | Microsoft Azure](https://azure.microsoft.com/ja-jp/solutions/open-source/machine-learning/)


### 3.4. Trusted

モデルの透明性の向上とステークホルダーとの信頼構築

![モデル解釈](./assets/images/AzureML-Bootcamp-資料_1280x720px_00101.png)

![Black Box モデルの弊害](./assets/images/AzureML-Bootcamp-資料_1280x720px_00102.png)

![モデル解釈のアプローチ方法](./assets/images/AzureML-Bootcamp-資料_1280x720px_00103.png)

![モデル解釈を支えるテクノロジー](./assets/images/AzureML-Bootcamp-資料_1280x720px_00104.png)

![モデル解釈を支えるテクノロジー](./assets/images/AzureML-Bootcamp-資料_1280x720px_00105.png)

![Interpretability Community](./assets/images/AzureML-Bootcamp-資料_1280x720px_00106.png)

![提供している Explainer](./assets/images/AzureML-Bootcamp-資料_1280x720px_00107.png)

<details>
<summary>解説</summary>
<i>
最後 4 つめの特徴は Trusted になります。今日は特にモデル解釈機能 interpretML についてご説明させてください。

モデル解釈機能 InterpretML はブラックボックスになりがちな機械学習モデルを解釈説明するための機能をご提供しています。具体的には予測値に影響している変数の重要度貢献度を出力することができます。

例えば品質管理のシナリオにおいては品質不良に関連するセンサーデータなどの変数を特定することができ、品質改善の手助けとなります。
</i>
</details>

#### 3.4.1. 参考リンク

* [責任ある AI とは? - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-responsible-ai)

<details>
<summary>解説</summary>
<i>
以上が大きな4つの特徴差別化要因になります。

自動機械学習などによる効率的なモデル開発のみならずモデルの運用管理や信頼性までを考慮したエンタープライズレベルの機械学習プラットホームになっています。
</i>
</details>


---


## 4. まとめ

* Azure ML は機械学習プラットフォームのマネージドサービス
    - 機械学習システムに必要なモジュールがビルトイン
* あらゆるスキルレベルに対応したインタフェース
    - [自動機械学習](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-automated-ml)、[デザイナー](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-designer)、Python & R SDK
* エンタープライズ対応の様々な機能を提供
    - [モデル解釈](https://learn.microsoft.com/ja-jp/azure/machine-learning/how-to-machine-learning-interpretability)、[MLOps](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-model-management-and-deployment)、[ONNX による相互運用性](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-onnx) etc

<details>
<summary>解説</summary>
<i>
最後、まとめに入ります。

冒頭、Azure AI の全体像やAzure Macine Learning の実績についてお話しをしました。機械学習のシステムの複雑さやプロセスを効率的に回すことの重要性もご説明させていただきました。

Azure Machine Learning は、複雑な機械学習システムがあらかじめビルトインされており、すぐにがエンタープライズレベルの機械学習プロジェクトを始めることができます。

移動機械学習やデザイナーなどのモデル開発を効率的に行うための様々なインターフェースをご提供すると同時にモデルの運用管理を行うための仕組みもご提供しておりますぜひ皆様の機械学習プロジェクトにおいてもご活用いただければ幸いです.

またこの後ご説明がありますがアイエスID様におかれましても Azure Machine Learning をフルに活用した製造業さまに向けた機械学習のソリューションをご提供しております。ぜひ、こちらも注目していただければ幸いです
</i>
</details>


---


## 5. 参考リンク

* [Machine Learng Practices and Tips - 機械学習プロジェクトを進めるためのガイドブック](https://azure.github.io/machine-learning-best-practices/#/)
