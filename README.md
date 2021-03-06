# imdb-rating
預測 IMDb 電影評分，並利用 embedding 比較演員之間相似度差異

## 任務介紹
- 預測 IMDb 電影評分
  - 使用年份、片長、風格、演員等等變數
- Actor Embedding Learning
  - 使用 Actor Embedding 來取代 One-hot Encoding
- 比較不同演員的性質異同
  - 使用 Actor Embedding 來計算相似度

## 資料集來源
- [Dataset](https://www.kaggle.com/datasets/ashirwadsangwan/imdb-dataset)
  - title.basics.tsv
  - title.ratings.tsv
  - title.principals.tsv

## 資料探索
透過 EDA 有以下觀察
- 資料分布情形
  - 大部分電影的平均分數落在 5 - 8 分之間
  ![rating](img/avg-rating.png)
  - 類型最多的電影為 Drama，第二為 Comedy
  ![genre](img/genre.png)
  - 近年越來越多電影上映，然而電影分數卻越來越低
  ![start-year](img/start-year.png)
  ![start-year-rating](img/start-year-rating.png)
- 部分欄位與平均分數關係
  - 平均分數最高的電影種類為 Western，最低為 Family
  ![genre-ratings](img/genre-ratings.png)
  - 平均分數最高的類型為電視劇(tvEpisode)，最低為電影(movie)
  ![title-rating](img/title-rating.png)
  - 票數越高的電影，平均分數也越高
  
  ![vote-rating](img/vote-rating.png)
  - 總長度在 4 小時以下、20 小時以上的電影，平均分數略低
  ![hours-rating](img/hours-rating.png)
- 演出人員
  - 演出前 10 高的演員平均分數都在 7 分以上且差異不大
  ![cast](img/cast.png)
  ![cast-rating](img/cast-rating.png)
 
## 預測模型
嘗試不同模型進行比較，同時嘗試不同資料集來比較演員資料是否對於電影評分預測有幫助
- 模型成效
  - 可以發現在原始資料集之下，加入演員以及幕後人員的資料欄位對於預測結果是有幫助的
  - XGBoost 在所有模型當中表現最佳
![model-result](img/model-result.png)

## 演員之間相似度計算
利用演員的 embedding，計算 cosine similarity，找出與某一演員最相關的其他演員
- Vin Diesel
  - 與 Vin Diesel 相關的主要都是動作片的演員，其中包含了出演『天能』的 John David Washington；我們熟悉的甄子丹，他與馮迪索共同主演『限制級戰警』；還有出演『搶救雷恩大兵』的 Barry Pepper
![vin](img/vin.png)
- Kevin Hart
  - 與 Vin Diesel 相關的主要都是動作片的演員，其中包含了出演『天能』的 John David Washington；我們熟悉的甄子丹，他與馮迪索共同主演『限制級戰警』；還有出演『搶救雷恩大兵』的 Barry Pepper
  - Kevin Hart 也曾經出演 J. Cole 的 MV 演出
![kevin](img/kevin.png)

## 結論
- 預測 IMDb 電影評分
  - RMSE 預測評分大約誤差正負 1
- Actor Embedding Learning
  - 節省大量運算資源和時間，且在分數上有更佳的表現
- 比較不同演員的性質異同
  - 成功使用 Actor Embedding 來計算相似度，能夠將演員特質量化並且放在一群


 
 
 
