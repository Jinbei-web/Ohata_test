# MLAPI-JINBEI WEB搭載用の推論API

## <動かすのに必要な手順> 

・環境のコピー pip install -r requirements.txt

・下記の関連ファイルを設置．（これらのファイル群は，重すぎるため，gdriveで共有[https://drive.google.com/drive/folders/1j8HZP2HVINoTHIZQ1ud5JKOLBET95SXJ?usp=sharing]）

　・./model_data/test_data/120class_model.pkl

　・./model_data/LabelEncoder_120class.pickle

　・./model_data/smoothing_ref_data_20221216.pickle

## <使い方> 

```
from jinbei_MLAPI_V1_2 import ApplyData #推論のクラス
from jinbei_MLAPI_V1_2 import jinbei_index #J指標算出の関数
```

### 推論

```
appleid_data = ApplyData(shutuba_table_df[DF], last_info_df[DF], past_calc_map[DF], race_class_df[DF])
appleid_data.predict_120class(output_count_120class = 10)
```

([‘1-2-3’, ‘1-3-2’, ‘1-4-3’, ‘1-4-2’, ‘1-2-4’, ‘3-1-6’, ‘1-3-5’, ‘2-3-1’, ‘2-3-5’, ‘3-1-5’], [6.574959879653965, 1.3990004064703248, 1.2545859936832704, 1.159618328426226, 1.0490993558618158, 1.02636447931112, 0.8917335281525699, 0.8577304700966253, 0.7722237598778535, 0.6847221126848473])


### J指標の算出

```
jinbei_index(shutuba_table_df[DF], past_calc_map[DF], date[str]<例；“2022-12-18”>)
```
array([98.5925135 , 86.43388291, 90.95085493, 97.94283453, 79.66665971, 98.90538408])