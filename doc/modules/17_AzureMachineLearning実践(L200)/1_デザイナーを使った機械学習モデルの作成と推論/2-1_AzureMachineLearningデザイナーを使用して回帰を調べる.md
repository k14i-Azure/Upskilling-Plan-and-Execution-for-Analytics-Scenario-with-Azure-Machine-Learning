###### Azure Machine Learning 実践 (L200) > 1. デザイナーを使った機械学習モデルの作成と推論 > 2

# 1. Azure Machine Learning デザイナーを使用して回帰を調べる

## ヒント

### 推論時に `Enter Data manually` モジュールで使用するデータ

```csv
symboling,normalized-losses,make,fuel-type,aspiration,num-of-doors,body-style,drive-wheels,engine-location,wheel-base,length,width,height,curb-weight,engine-type,num-of-cylinders,engine-size,fuel-system,bore,stroke,compression-ratio,horsepower,peak-rpm,city-mpg,highway-mpg
3,NaN,alfa-romero,gas,std,two,convertible,rwd,front,88.6,168.8,64.1,48.8,2548,dohc,four,130,mpfi,3.47,2.68,9,111,5000,21,27
3,NaN,alfa-romero,gas,std,two,convertible,rwd,front,88.6,168.8,64.1,48.8,2548,dohc,four,130,mpfi,3.47,2.68,9,111,5000,21,27
1,NaN,alfa-romero,gas,std,two,hatchback,rwd,front,94.5,171.2,65.5,52.4,2823,ohcv,six,152,mpfi,2.68,3.47,9,154,5000,19,26
```

### `Web Service Output` モジュールが予測値のみを含むように加工する Python スクリプト

```python
import pandas as pd

def azureml_main(dataframe1 = None, dataframe2 = None):

    scored_results = dataframe1[['Scored Labels']]
    scored_results.rename(columns={'Scored Labels':'predicted_price'},
                        inplace=True)
    return scored_results
```

### テスト用 HTTP リクエストボディの例

```json
{
"Inputs": {
            "WebServiceInput0":
            [
                {
                    "symboling": 3,
                    "normalized-losses": 1.0,
                    "make": "alfa-romero",
                    "fuel-type": "gas",
                    "aspiration": "std",
                    "num-of-doors": "two",
                    "body-style": "convertible",
                    "drive-wheels": "rwd",
                    "engine-location": "front",
                    "wheel-base": 88.6,
                    "length": 168.8,
                    "width": 64.1,
                    "height": 48.8,
                    "curb-weight": 2548,
                    "engine-type": "dohc",
                    "num-of-cylinders": "four",
                    "engine-size": 130,
                    "fuel-system": "mpfi",
                    "bore": 3.47,
                    "stroke": 2.68,
                    "compression-ratio": 9,
                    "horsepower": 111,
                    "peak-rpm": 5000,
                    "city-mpg": 21,
                    "highway-mpg": 27
                }
            ]
        },
"GlobalParameters": {}
}
```

### テスト結果 (HTTP レスポンスボディ) の例

```json
{
  "Results": {
    "WebServiceOutput0": [
        "predicted_price": 14996.946628993359
    ]
  }
}
```


---


## ブループリント

### 学習パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-regression-model/evaluate.png">
</details>

### 推論パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-regression-model/inference-pipeline-lab.png">
</details>
