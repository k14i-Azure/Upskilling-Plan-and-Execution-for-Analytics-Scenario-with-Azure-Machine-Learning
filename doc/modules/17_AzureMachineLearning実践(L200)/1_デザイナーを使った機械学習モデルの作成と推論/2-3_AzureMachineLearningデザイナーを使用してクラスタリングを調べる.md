###### Azure Machine Learning 実践 (L200) > 1. デザイナーを使った機械学習モデルの作成と推論 > 2

# 3. Azure Machine Learning デザイナーを使用してクラスタリングを調べる

## ヒント

### 推論時に `Enter Data manually` モジュールで使用するデータ

```csv
CulmenLength,CulmenDepth,FlipperLength,BodyMass
39.1,18.7,181,3750
49.1,14.8,220,5150
46.6,17.8,193,3800
```

### テスト用 HTTP リクエストボディの例

```json
{
    "Inputs": {
        "input1": [
            {
                "CulmenLength": 49.1,
                "CulmenDepth": 4.8,
                "FlipperLength": 1220,
                "BodyMass": 5150
            }
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
      "CulmenLength": 0.6181818181818182,
      "CulmenDepth": -0.9880952380952379,
      "FlipperLength": 17.76271186440678,
      "BodyMass": 0.6805555555555556,
      "Assignments": 1,
      "DistancesToClusterCenter no.0": 18.51597968495938,
      "DistancesToClusterCenter no.1": 17.951293093498048,
      "DistancesToClusterCenter no.2": 18.34733879503687
    ]
  }
}
```


---


## ブループリント

### 学習パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-clustering-model/evaluate-cluster.png">
</details>

### 推論パイプライン

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/MicrosoftLearning/AI-900-AIFundamentals.ja-JP/raw/main/instructions/media/create-clustering-model/inference-clusters.png">
</details>
