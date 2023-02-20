# Azure Machine Learning 概要

## 背景

1. 機械学習のシステム
2. 機械学習プロジェクトのプロセス

### 1. 機械学習のシステム

* 本当に重要なのは、機械学習モデルを支えるシステム構築・運用管理。
    - これらは今日非常に複雑になっている。

<details>
<summary>解説</summary>
<i>
機械学習のシステムを考えています。お客様で機械学習の取り組みが始まっていますがどうしてもモデル開発にフォーカスされがちですもちろん精度が高いモデルといったものが必要になってきますがそれ以外にも大事なピースが存在します。

スライドにありますようにモデル学習で使うためのデータを収集する機能であったりデータを検証する機能機器学習のプロセスを管理する機能モデルを提供する機能またそれをモニタリングする機能など数多くのモジュールが必要になってきます.

このようなモジュールがしっかり準備されていないやったり不十分であると機械学習のモデルの運用管理が煩雑になり結果としてモデルの精度が低下したり鳥が徐々に使われなくなったりしますまた機械学習のプロジェクトスケールさせることも難しいです

といった理由から西学習のモデルだけではなく、その周辺のシステムもしっかり考えていく必要が今後出てきます
</i>
</details>


#### 参考文献

* [“Hidden Technical Debt in Machine Learning Systems,” Google NIPS 2015  
](https://proceedings.neurips.cc/paper/2015/file/86df7dcfd896fcaf2674f757a2463eba-Paper.pdf)
    - [Hidden technical debt in machine learning systems（日本語資料）](https://www.slideshare.net/Gushi/hidden-technical-debt-in-machine-learning-systems)
    - [データ活用における課題と対策](https://www.bcm.co.jp/site/2019/08/ntt-com/1908-ntt-com-01-05.pdf)

### 2. 機械学習プロジェクトのプロセス

* 機械学習のライフサイクルを高速かつ効率的に回していくことが、市場競争において重要になっている。
    - 既存のしくみに乗っかることで、効率的に実現することができる。

<details>
<summary>解説</summary>
<i>
次に機械学習のプロセスについて見ていきます。モデルの運用管理まで考えると大きく3つのプロセスに分かれると考えています。実験、モデル開発、運用管理です。

実験においては試行錯誤するモデル開発を指しています。様々な特徴エンジニアリング、機械学習アルゴリズム、パラメータ、精度が高いモデルを探し出すプロセスになります。

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

#### 参考文献

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

## Azure Machine Learning とは

* 機械学習プロセスをエンドツーエンドでサポートするマネージドサービス
    - 必要なシステムモジュールをあらかじめビルトインしている
* 自動機械学習やパラメータチューニング機能による効率的なモデル開発
* 継続的なモデルのデプロイ & 運用管理をサポート
* スケーラブルな計算環境による並列分散処理 etc

<details>
<summary>解説</summary>
<i>
Azure Machine Learning は機械学習のプロセスをend-to-endでサポートするマネージドサービスになります機械学習のシステムに必要なモジュールはあらかじめビルトインされているため即座に機械学習のプロジェクトを始めることができます。

モデル開発においては自動車機械学モデル開発においては自動車機械学習やパラメーターチューニング機能によって高速に精度が高いモデルを構築できます。その後のモデル検証運用管理の仕組み機能もご提供しております。継続的なモデルのデプロイメント運用管理が可能になります。

またクラウドのメリットとしてスケーラブルな並列分散環境といったものが利用できます。自動機械学習やパラメーターチューリング機能によって高速に誰でも精度が高いモデルを構築できます。
</i>
</details>

---

## 4 つの特徴

1. For all skill levels
    - あらゆるスキルレベルに対応した機械学習の機能を提供
2. Industry leading MLOps
    - 機械学習のプロセスを効率的に回すための仕組みや機能を提供
3. Open & Interoperable
    - オープンなテクノロジーを採用＆あらゆる場所・デバイスで利用可能
4. Trusted
    - 透明性の高い責任のあるAIモデルの開発を支援

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

### 1. For all skill levels

* [自動機械学習 (AutoML)](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-automated-ml)
    - 機械学習の自動化による民主化・大規模 AI 開発の実現
* [デザイナー (ドラッグアンドドロップ ML)](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-designer)
    - マウスのドラッグ & ドロップで構築する機械学習パイプライン
* ノートブック (Python, R)
    - Python・R によるコードファーストアプローチ

<details>
<summary>解説</summary>
<i>
For all skill leves に関してはまず自動機械学習 Automated Mchine Learning が挙げられます。ユーザはデータを投入し簡単な設定を行うだけで機械学習のモデル開発を自動で行います。完成したモデルを速やかにマウス操作のみでデプロイして利用していくこともできるようになっています。

現在は分類回帰時系列予測などメジャーな機械学習のタスクをサポートしています。例えば分類であれば品質管理であったり設備保全でご利用になります。また需要予測に関しては時系列予測の機能を使うことで

デザイナーと呼ばれるドラッグアンドドロップで機械学習のモデル開発のフローを定義していく機能もご提供しています。自動機械学習よりもより柔軟にカスタマイズ可能な機械学習のフローをマウスの操作のみで作り上げることができるようになっています。この機能は表形式データに適用することもできますし画像認識のシナリオでdeepラーニングの機能もビルトインされています。

またPython や R を使う方ももちろんご利用になります。Azure Machine Learning が提供する Python・R の SDKを利用することで Azure Machine Learning の様々な便利な機能にアクセスし、これまでよりも効率的に高速にPythonアールによる機械学習パイプラインの実装が可能になります。
</i>
</details>

#### 参考文献

* [Azure Machine Learning の対象ユーザー | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#who-is-azure-machine-learning-for)
* [チームの全員の生産性 | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#productivity-for-everyone-on-the-team)
* [ニーズを満たすクロス互換プラットフォーム ツール | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#cross-compatible-platform-tools-that-meet-your-needs)
* [スタジオ | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#studio)
* [特徴量化とアルゴリズムの選択の自動化 (AutoML) | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#automated-featurization-and-algorithm-selection-automl)

### 2. Industry leading MLOps

エンドーツーエンドの機械学習ライフサイクルを実現

<details>
<summary>解説</summary>
<i>
2つめの特徴の Industry Leading MLOps は、End-to-endの機械学習ライフサイクルを実現する仕組みをご提供していると言うことです.。

アジュールマシンラーニングを利用することでモデル学習やモデルのパッケージか検証ディプロイモニタリングの仕組みを実装することができますがこれらの個々のプロセスを例えば自動化するなどの仕組みを作ることができます。またアプリケーションとの連携を行うような仕組み作りも可能になります。具体的には Azure DevOps や GitHub などのサービスと組み合わせることによってより、より効率的に機械学習のプロセスを回すことができるため大規模なモデルの運用管理が可能になります   
Azure DevOps や Github にはアジュールマシンラーニングと結合できる接続できる拡張機能がご提供されているため統合も容易です.
</i>
</details>

#### 参考文献

* [MLOps: 機械学習モデル管理 - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-model-management-and-deployment)

### 3. Open & Interoperable

オープンテクノロジーの採用による生産性の向上

<details>
<summary>解説</summary>
<i>
3つ目の特徴に入っていきます。 Open & Interoperatable は、オープンテクノロジーの採用による生産性の向上を意味します。

Azure Machine Learning は特定の技術にロックインされることなく様々なオープンのテクノロジーを利用することもできるようになっています。

機械学習のモデル開発で利用する様々なオープンソースの機械学習フレームワーク、PyTorchや Scikit-Learn などがご利用になれます。

またPython や R などのプログラミング言語を、普段使いなれた開発ツール、例えば Jupyter Notebook、VisualStudioコード上で利用していくこともできるようになっています。
</i>
</details>

#### 参考文献

* [オープン性と相互運用性 | Azure Machine Learning とは - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/overview-what-is-azure-machine-learning#open-and-interoperable)
* [オープンソースの機械学習 | Microsoft Azure](https://azure.microsoft.com/ja-jp/solutions/open-source/machine-learning/)

### 4. Trusted

モデルの透明性の向上とステークホルダーとの信頼構築

<details>
<summary>解説</summary>
<i>
最後 4 つめの特徴は Trusted になります。今日は特にモデル解釈機能 interpretML についてご説明させてください。

モデル解釈機能 InterpretML はブラックボックスになりがちな機械学習モデルを解釈説明するための機能をご提供しています。具体的には予測値に影響している変数の重要度貢献度を出力することができます。

例えば品質管理のシナリオにおいては品質不良に関連するセンサーデータなどの変数を特定することができ、品質改善の手助けとなります。
</i>
</details>

#### 参考文献

* [責任ある AI とは? - Azure Machine Learning | Microsoft Learn](https://learn.microsoft.com/ja-jp/azure/machine-learning/concept-responsible-ai)

<details>
<summary>解説</summary>
<i>
以上が大きな4つの特徴差別化要因になります。

自動機械学習などによる効率的なモデル開発のみならずモデルの運用管理や信頼性までを考慮したエンタープライズレベルの機械学習プラットホームになっています。
</i>
</details>

---

## まとめ

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
