###### Azure Machine Learning 実践 (L200) > 2. コードなしAutoMLを使った機械学習モデルの作成

# 3. Azure ML の自動機械学習について調べる

## 手順

1. データ資産を作成する
2. ジョブを構成する
3. タスクの種類の選択と設定を行い、実験を実行する
4. モデルおよびテストされたアルゴリズムを確認する
5. 最適なモデルをデプロイする
6. デプロイされたサービスをテストする


---


## ヒント

### テスト用 HTTP リクエストボディの例

```json
{
  "Inputs": { 
    "data": [
      {
        "day": 1,
        "mnth": 1,   
        "year": 2022,
        "season": 2,
        "holiday": 0,
        "weekday": 1,
        "workingday": 1,
        "weathersit": 2, 
        "temp": 0.3, 
        "atemp": 0.3,
        "hum": 0.3,
        "windspeed": 0.3 
      }
    ]    
  },   
  "GlobalParameters": 1.0
}
```

### テスト結果 (HTTP レスポンスボディ) の例

```json
{
  "Results": [
    444.277099014669
  ]
}
```


