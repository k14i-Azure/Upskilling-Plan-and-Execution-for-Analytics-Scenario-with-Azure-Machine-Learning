###### Azure Machine Learning 実践 (L200) > 1. デザイナーを使った機械学習モデルの作成と推論 > 1

# 5. 分類器を構築し、Python スクリプトを使用して、Azure Machine Learning デザイナーを使用して信用リスクを予測する


## ヒント

### 使用する Python コード

```python
import pandas as pd

def azureml_main(dataframe1 = None, dataframe2 = None):

    df_label_1 = dataframe1[dataframe1.iloc[:, 20] == 1]
    df_label_2 = dataframe1[dataframe1.iloc[:, 20] == 2]

    result = df_label_1.append([df_label_2] * 5, ignore_index=True)
    return result,
```


---


## ブループリント

<details>
<summary>ネタバレ注意</summary>
<img src="https://github.com/k14i-Azure/MachineLearningDesigner_ja-jp/raw/master/articles/samples/media/binary-classification-python-credit-prediction/graph.png">
</details>