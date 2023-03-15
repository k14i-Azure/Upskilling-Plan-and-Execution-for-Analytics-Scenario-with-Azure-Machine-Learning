# Azure Machine Learning 実践 (L200)

## 1. デザイナーを使った機械学習モデルの作成と推論

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド | デザイナー サンプル # | デザイナー サンプル タイトル |
| ---:| --- | --- | --- | --- | --- | ---:| --- |
| 1 | Azure Machine Learning デザイナーで回帰を使用して車の価格を予測する | 回帰 | CPU | Automobile price data (Raw) | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/regression-automobile-price-prediction-basic.md | 4 | Regression - Automobile Price Prediction (Basic) |
| 2 | 複数の回帰モデルをトレーニングして比較し、Azure Machine Learning デザイナーで自動車の価格を予測する | 回帰 | CPU | Automobile price data (Raw) | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/regression-automobile-price-prediction-compare-algorithms.md | 5 | Regression - Automobile Price Prediction (Advanced) |
| 3 | ブーステッド デシジョン ツリーを使用して、Azure Machine Learning デザイナーでチャーンを予測する | 分類 | CPU | <li>CRM Dataset Shared<li>CRM Churn Labels Shared | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/binary-classification-customer-relationship-prediction.md | 8 | Binary Classification - Customer Relationship Prediction |
| 4 | 分類器を構築し、特徴選択を使用して Azure Machine Learning デザイナーで収入を予測する | 分類 | CPU | Adult Census Income Binary Classification dataset | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/binary-classification-feature-selection-income-prediction.md | 6 | Binary Classification with Feature Selection - Income Prediction |
| 5 | 分類器を構築し、Python スクリプトを使用して、Azure Machine Learning デザイナーを使用して信用リスクを予測する | 分類 | CPU | German Credit Card UCI dataset | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/binary-classification-python-credit-prediction.md | 7 | Binary Classification with custom Python script - Credit Risk Prediction |
| 6 | Azure Machine Learning デザイナーを使用して、会社のカテゴリを予測する分類器を構築する | 分類 | CPU | Wikipedia SP 500 Dataset | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/text-classification-wiki.md | 10 | Text Classification - Wikipedia SP 500 Dataset |
| 7 | 分類器を作成し、R を使用して Azure Machine Learning デザイナーでフライトの遅延を予測する | 分類 | CPU | <li>Flight Delays Data<li>Weather Dataset | https://github.com/k14i-Azure/MachineLearningDesigner-ja_jp/blob/master/articles/samples/r-script-flight-delay-prediction.md | 9 | Use custom R script - Flight Delay Prediction |

### 1.1. デザイナーを使った機械学習モデルの作成, 推論, デプロイ, テスト

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド | デザイナー サンプル # | デザイナー サンプル タイトル |
| ---:| --- | --- | --- | --- | --- | ---:| --- |
| 1 | Explore regression with Azure Machine Learning Designer | 回帰 | CPU | Automobile price data (Raw) | https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02a-create-regression-model.html | 4 | Regression - Automobile Price Prediction (Basic) |
| 2 | Explore classification with Azure Machine Learning Designer | 分類 | CPU | [diabetes-data](https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02b-create-classification-model.html) | https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02b-create-classification-model.html | - | - |
| 3 | Explore clustering with Azure Machine Learning Designer | クラスタリング | CPU | [penguin-data](https://aka.ms/penguin-data) | https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02c-create-clustering-model.html | - | - |


## 2. コードなし AutoML を使った機械学習モデルの作成

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド |
| ---:| --- | --- | --- | --- | --- |
| 1 | Azure Machine Learning スタジオでコードなし AutoML を使用して分類モデルをトレーニングする | 分類 | CPU | [bankmarketing_train.csv](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv) | https://learn.microsoft.com/ja-jp/azure/machine-learning/tutorial-first-experiment-automated-ml |
| 2 | Azure Machine Learning Studio でコードなし自動機械学習を使用して需要を予測する | 回帰(時系列) | CPU | [bike-no.csv](https://github.com/Azure/azureml-examples/blob/main/v1/python-sdk/tutorials/automl-with-azureml/forecasting-bike-share/bike-no.csv) | https://learn.microsoft.com/ja-jp/azure/machine-learning/tutorial-automated-ml-forecast |
| 3 | Explore Automated Machine Learning in Azure ML | 回帰 | CPU | [bike-rentals](https://aka.ms/bike-rentals?azure-portal=true) | https://microsoftlearning.github.io/AI-900-AIFundamentals/instructions/02-module-02.html |


## 3. ノートブックを使った機械学習モデルの作成と推論

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド |
| ---:| --- | --- | --- | --- | --- |
| 1 | Getting Started: training an image classification model | 分類 | CPU | [default_of_credit_card_clients.csv](https://azuremlexamples.blob.core.windows.net/datasets/credit_card/default%20of%20credit%20card%20clients.csv) | Notebooks > Samples > SDK v2 > tutorials > azureml-getting-started > [azureml-getting-started-studio.ipynb](https://github.com/Azure/azureml-examples/blob/main/tutorials/azureml-getting-started/azureml-getting-started-studio.ipynb) |
| 2 | AzureML in a Day | 分類 | CPU | [default_of_credit_card_clients.xls](https://archive.ics.uci.edu/ml/machine-learning-databases/00350/default%20of%20credit%20card%20clients.xls) | Notebooks > Samples > SDK v2 > tutorials > azureml-in-a-day > [azureml-in-a-day.ipynb](https://github.com/Azure/azureml-examples/blob/main/tutorials/azureml-in-a-day/azureml-in-a-day.ipynb) |
| 3 | Distributed PyTorch Image Classification | 分類 | CPU | [ImageNetDogs](http://vision.stanford.edu/aditya86/ImageNetDogs/images.tar) | Notebooks > Samples > SDK v2 > tutorials > e2e-distributed-pytorch-image > [e2e-object-classification-distributed-pytorch.ipynb](https://github.com/Azure/azureml-examples/blob/main/tutorials/e2e-distributed-pytorch-image/e2e-object-classification-distributed-pytorch.ipynb) |
| 4 | Tutorial: Create production ML pipelines with Python SDK v2 (preview) in a Jupyter notebook | 分類 | CPU | [default_of_credit_card_clients.xls](https://archive.ics.uci.edu/ml/machine-learning-databases/00350/default%20of%20credit%20card%20clients.xls) | Notebooks > Samples > SDK v2 > tutorials > e2e-ds-experience > [e2e-ml-workflow.ipynb](https://github.com/Azure/azureml-examples/blob/main/tutorials/e2e-ds-experience/e2e-ml-workflow.ipynb) |
| 5 | 自動機械学習 AutoML による与信管理モデル | 分類 | CPU | [hmeq.csv](./assets/data/hmeq.csv) from [Kaggle](https://www.kaggle.com/datasets/ajay1735/hmeq-data) | https://github.com/konabuta/azureml-workshop-2021/blob/main/day1/hmeq-automl.ipynb |
| 6 | LightGBM Model Train - Experiment Logging | 回帰 | CPU | [sklearn.datasets.load_boston](https://scikit-learn.org/0.15/modules/generated/sklearn.datasets.load_boston.html) | https://github.com/konabuta/azureml-workshop-2021/blob/main/day2/lgb-train-azureml-experiment.ipynb |


## 4. Python SDK を使った自動 ML - 機械学習モデルの作成と推論

### 4.1. Python SDK v2

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド |
| ---:| --- | --- | --- | --- | --- |
| 1 | AutoML と Python を使用して物体検出モデルをトレーニングする | Computer Vision (物体検出) | **GPU** | [odFridgeObjects.zip](https://cvbp-secondary.z19.web.core.windows.net/datasets/object_detection/odFridgeObjects.zip) | https://learn.microsoft.com/ja-jp/azure/machine-learning/tutorial-auto-train-image-models?tabs=python |

### 4.2. Python SDK v1

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド |
| ---:| --- | --- | --- | --- | --- |
| 1 | 自動機械学習 Automated Machine Learning による自動車価格予測モデリング & モデル解釈 (リモート高速実行) | 回帰 | CPU | [automobile.csv](./assets/data/automobile.csv) | https://github.com/konabuta/Automated-ML-Workshop/blob/master/Sample/Azure-Machine-Learning/Automobile-regression-explainer-remote.ipynb |
| 2 | 自動機械学習 Automated Machine Learning による離反予測モデリング & モデル解釈 (リモート高速実行) | 分類 | CPU | [CATelcoCustomerChurnTrainingSample.csv](https://amlgitsamples.blob.core.windows.net/churn/CATelcoCustomerChurnTrainingSample.csv) | https://github.com/konabuta/Automated-ML-Workshop/blob/master/Sample/Azure-Machine-Learning/Churn-classification-explainer-remote.ipynb |
| 3 | エネルギーの需要予測モデリング & モデル解釈 (リモート高速実行) | 回帰 | CPU | [nyc_energy.csv](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/nyc_energy.csv) | https://github.com/konabuta/Automated-ML-Workshop/blob/master/Sample/Azure-Machine-Learning/Energy-demand-forecasting-explainer-remote.ipynb |
| 4 | 自動機械学習 Automated Machine Learning による品質管理モデリング & モデル解釈 (リモート高速実行) | 分類 | CPU | [Factory.csv](./assets/data/Factory.csv) | https://github.com/konabuta/Automated-ML-Workshop/blob/master/Sample/Azure-Machine-Learning/FactoryQC-classification-explainer-remote.ipynb |


## 5. CLI を使った自動 ML - 機械学習モデルの作成と推論

| # | タイトル | タスク | CPU/GPU | サンプルデータ | ガイド |
| ---:| --- | --- | --- | --- | --- |
| 1 | AutoML と Python を使用して物体検出モデルをトレーニングする | Computer Vision (物体検出) | **GPU** | [odFridgeObjects.zip](https://cvbp-secondary.z19.web.core.windows.net/datasets/object_detection/odFridgeObjects.zip) | https://learn.microsoft.com/ja-jp/azure/machine-learning/tutorial-auto-train-image-models?tabs=cli |



<!-- ## 1. モデルのトレーニングとデプロイ

1. 画像分類モデルをトレーニングする
2. 画像分類モデルをデプロイする
3. 自動 ML と Python で物体検出モデルをトレーニングする
4. 暗号化された推論サービスをデプロイする
5. オンライン エンドポイントを使用して機械学習モデルをデプロイしてスコアリングを行う
6. オンライン エンドポイントへの安全なロールアウト
7. バッチエンドポイントを使用してバッチスコアリングを行う
8. 自動 ML を使用してタクシーの運賃を予測する
9. 画像分類モデルの実行, メトリックの追跡, モデルのデプロイ方法を10分で学ぶ
10. Power BI から Azure Machine Learning モデルを使用する
11. Python SDK を使用してバッチのジョブを実行する
12. 自動 ML を使用して不正行為を分類する
13. CLI (V2) を使用してモデルをトレーニングする

## 2. 責任ある AI (Responsible AI)

1. Responsible ML でモデルを解析する
2. InterpretML におけるモデルのインターオペラビリティ
3. Python SDK のインターオペラビリティパッケージを使用して機械学習モデルの翻訳と説明を行う
4. モデルの公平性
5. Python で機械学習モデルの公平性を評価する
6. 機械学習における差分プライバシー -->
