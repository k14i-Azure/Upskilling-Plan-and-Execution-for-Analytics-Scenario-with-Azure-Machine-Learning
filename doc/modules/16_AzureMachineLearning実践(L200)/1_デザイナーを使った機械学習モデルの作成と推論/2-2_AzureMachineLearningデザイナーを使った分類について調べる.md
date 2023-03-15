###### Azure Machine Learning 実践 (L200) > 1. デザイナーを使った機械学習モデルの作成と推論> 2

# 2. Azure Machine Learning デザイナーを使った分類について調べる

## ヒント

### 推論時に `Enter Data manually` モジュールで使用するデータ

```csv
PatientID,Pregnancies,PlasmaGlucose,DiastolicBloodPressure,TricepsThickness,SerumInsulin,BMI,DiabetesPedigree,Age
1882185,9,104,51,7,24,27.36983156,1.350472047,43
1662484,6,73,61,35,24,18.74367404,1.074147566,75
1228510,4,115,50,29,243,34.69215364,0.741159926,59
```

### `Web Service Output` モジュールが予測値のみを含むように加工する Python スクリプト

```python
import pandas as pd

def azureml_main(dataframe1 = None, dataframe2 = None):

    scored_results = dataframe1[['Scored Labels', 'Scored Probabilities']]
    scored_results.rename(columns={'Scored Labels':'DiabetesPrediction',
                                'Scored Probabilities':'Probability'},
                        inplace=True)
    return scored_results
```

### テスト用 HTTP リクエストボディの例

```json
{
  "Inputs": {
    "input1":
      [
        { "PatientID": 1882185,
          "Pregnancies": 9,
          "PlasmaGlucose": 104,
          "DiastolicBloodPressure": 51,
          "TricepsThickness": 7,
          "SerumInsulin": 24,
          "BMI": 27.36983156,
          "DiabetesPedigree": 1.3504720469999998,
          "Age": 43 }
        ]
      },
  "GlobalParameters":  {}
}
```

### テスト結果 (HTTP レスポンスボディ) の例

```json
{
  "Results": {
    "WebServiceOutput0": [
      {
        "PatientID": 1882185,
        "DiabetesPrediction": 1,
        "Probability": 0.7034111544417699
      }
    ]
  }
}
```


---


## ブループリント

### 学習パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-classification-model/evaluate-pipeline.png">
</details>

### 推論パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-classification-model/visual-inference.png">
</details>
