# NOTE
###### 比賽頁面連結 : http://sakailab.com/dialeval1/

###### 官方Github : https://github.com/DialEval-1/LSTM-baseline

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
