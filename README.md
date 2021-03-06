# NOTE
###### 比賽頁面連結 : http://sakailab.com/dialeval1/ 

###### 官方Github : https://github.com/DialEval-1/LSTM-baseline   

###### 去年官方競賽Github : https://github.com/sakai-lab/stc3-dataset     

###### Leader Board : http://deepimagining.com/upload    
 
---

##### 2020-04-07

老師建議 : 

1. 可以用每一個順序最多的NUGGET直接下去訓練結果。
2. 搜尋sequence學習法

##### 2020-04-10

3. 找上一屆 DialEval 比賽資料與競賽方法來跑

##### 2020-04-15

老師建議 :

4. 將檔案切成7個，每個檔案代表一個標籤，每個檔案為二元分類，針對該標籤有無分別為 0,1 
5. 用每個不同的檔案分別跑10個基本模型(NB, kNN, DT, RF, LR, SVM, XGB, TextCNN, LSTM ,*BiLSTM*) 10-Fold 抓出最好的結果，並且統計哪一個標籤哪一種方法最好?分數?
6. 產出結果後結合起來，用來跟原始矩陣算相似度(JSD)

##### 2020-05-06

老師建議 :

7. 求出 baseline 資料集(七欄位版)
8. 依據round來看最適模型
9. JSD下周一定要出來 

##### 2020-05-13

老師建議 :
   
10. 試跑大會JSD & SciPy jsd，是否答案為零?         
11. Loss functoin Cross_entropy ->> JSD (how to implement our own loss function?)     

##### 2020-05-29

老師建議 :  

12. 整理文件參加程式設計比賽
13. 應用 RCNN 或 CRNN 方法

##### 2020-07-07
| method        | JSD       | RNSS      |
| ------------- | --------- | --------- |
| TextCNN       | 0.048     | 0.141     |
| LSTM          | 0.043     | 0.13      |
| BiLSTM        | 0.040 | 0.129 |
| Double-BiLSTM | 0.047     | 0.143     |
| Double-BiLSTM (Maxlen 350/ Dim 300) | 0.0422     | 0.131     |
| BiLSTM (Maxlen 350/ Dim 300/ Token 50000/ Epoch 50) | 0.049     | 0.144     |
| BiLSTM (Maxlen 350/ Dim 300/ Token 40000/ Epoch 50) | 0.048     | 0.140     |
| WikiWord2Vec Double-BiLSTM | 0.036     | 0.122    |
| BaiduWord2Vec Double-BiLSTM | 0.039     | 0.128     |
|  WikiWord2Vec Double-BiLSTM (Add Round_feature / Fix first round as mean of train data) | 0.036     | 0.120     |  
|  WikiWord2Vec Double-BiLSTM (Add Round_feature / Fix first round as mean of train data / add previous vector) | 0.037     | 0.121     |        
|  WikiWord2Vec Double-BiLSTM (Add Round_feature / Fix first round as mean of train data / add previous vector / Attention) | **0.035**     | **0.120**     |   
|  WikiWord2Vec Double-BiLSTM (Add Round_feature / Fix first round as mean of train data / add previous vector / Attention/ 2 vector input/ llr) | 0.059     | 0.162     |  
|  WikiWord2Vec Double-BiLSTM (Add Round_feature / Fix first round as mean of train data / add previous vector / Attention/ llr) | 0.102     | 0.197     |  
|  BERT vector BiLSTM (Add Round_feature / Fix first round as mean of train data / add previous vector / Attention) | 0.040     | 0.128     |  


##### 2020-07-17   

老師建議 :    
__1. 鎖定第一輪與最末輪對話的最大標籤，預測其餘標籤(E.g. Round 01 : Fix GNUG0, predict CNaN)。__         
2. 更改class Attention 為 tf.keras.attention，並且加入模型。            
3. attention + 針對每1輪的每一個標籤做關鍵字(LLR 提取關鍵字)。              
__4. 訓練時也要放入前1輪的對話內容。__              
__5. 新增特徵feature: 給兩個維度，總共有幾輪，現在是第幾輪(E.g. [1,7],[2,7]...)。__           


##### 2020-07-22  
   
老師建議 :    
最後一輪分成 customer & helpdesk 兩種下去 predict


# NTCIR-15 Dial Eval 研討會論文計畫

created by Weber Huang, 2020-8-7

### 一、論文結構

這篇論文是研討會小短文格式，撰寫篇幅以含參考資源 <u>7 頁為上限</u>，上傳截止日期為 <u>**9/20 (日本時間 UTC +9)**</u> ，不過我們須提前完成以增加潤飾、修改的時間。

論文內容須包含競賽介紹，例如動機和目標，還有我們嘗試的方法等。以下是這次論文結構概要(這部分還可以討論) :

**預估篇幅** : 摘要(半頁)、介紹(1-2頁)、方法(2-3頁)、結果與分析(1頁)、結論(半頁)、參考資源(半頁)

+ **摘要 Abstract**
+ **介紹 Introduction**
  + 競賽介紹
  + 過去相關研究介紹
+ **方法 Method**
  + 基礎方法
  + Run 0
  + Run 1
  + Run 2
+ **結果與分析 Result and Analysis**
  + 結果比較
  + 官方方法(Optional)
+ **結論 Conclusion**
  + 彙總所有結果
+ **參考資源 Reference**

預期使用線上論文編輯軟體 <u>[Overleaf](https://www.overleaf.com/)</u> 來共同編輯、追蹤論文內容，此軟體共同編輯者<u>上限為 2 人</u>。編輯者目前暫定為 **彥鈞、顗亘** (待討論決定)。

### 二、論文工作分配、流程

首先，我們需要先完成 **<u>介紹、方法</u>**，再撰寫 **摘要**。**結果與分析 **要等官方於 8/31 釋出競賽結果方能加上，最後再補上結論。

| 時程 / 工作內容 | 彥鈞                   | 顗亘、宇雅              |
| --------------- | ---------------------- | ----------------------- |
| 8/8 -14         | 方法 - 基礎方法        | 介紹 - 競賽介紹         |
| 8/15 -21        | 方法 - 基礎方法        | 介紹 - 過去相關研究介紹 |
| 8/22 - 28       | 方法 - (Run 0 - Run 2) | 摘要 & 整理格式         |
| 8/29 - 9/4      | 結果與分析             | 整理參考資源            |



### 三、外部參考資源

一開始可以先參考過去 DialEval 研討會參賽者文章，以及主辦教授之前的論文。就這些文章做滾雪球文獻檢索。

NTCIR-14 [STC -3] : http://research.nii.ac.jp/ntcir/workshop/OnlineProceedings14/NTCIR/toc_ntcir.html

主辦教授 : Zhaohao Zeng, Sosuke Kato and Tetsuya Sakai (Waseda University)

