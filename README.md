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

