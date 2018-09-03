# 2018/08/28 – meeting4
### 1.DFD圖 (大約兩周內補上Lv2) –何佩瑜、徐慶崴
### 2.以後固定實體開會時間:每周三下午18:00
### 3.目前想法
1. 預測各地區預測人數y值(共25條公式)=<br/>
	日期x1+時間x2+氣溫x3+降雨量x4+相對濕度x5+氣壓x6+風速x7<br/>
	+海拔x8+商店x(9~?) (尚未取得)<br/>
2. 呈現方式:<br/>
	每區再細切10* 10(100格)，每一小格預測人數以區間顏色深淺顯示，即可顯示乘載人數預測範圍<br/>
※上述有想法可提出討論作新增刪減<br/>

### 4.工作事項
1. 海拔資料
2. 各地區商店(醫院,捷運站,KTV等)數量及座標
3. 資料彙整(資料檢查,清洗,補缺)
4. 原資料篩分成25* 100筆
5. 地圖視覺呈現(歷史資料-敘述統計)
6. 機器學習軟體應用(先有人學習,之後資料套入才有得問)
7. 研究天氣即時更新抓取(不過這個不急,可安排至下次工作)

以上7點開放認領,想要兩人一起的也可以,有問題或有其他要新增的提出來,預計9/12前完成。<br/>
<br/>
### 附件 : 2018/08/29 DFD
* Lv.0
![Alt text](https://github.com/WarrenLo/Project_Taxi_Data_Analysis/blob/master/image/DFD%20-%20Lv.0.jpg)
* Lv.1
![Alt text](https://github.com/WarrenLo/Project_Taxi_Data_Analysis/blob/master/image/DFD%20-%20Lv.1.jpg)
* * *
# 2018/08/21 – meeting3
### 1.預計分工
* **企劃整理**<br/>
何佩瑜<br/> 

* **資料查詢**<br/>
All<br/>

* **網站架設、機械學習**<br/>
羅文彥<br/>
何佩瑜<br/>
陳尹翊<br/>

* **統計分析**<br/>
徐慶崴<br/>
曾暉雅<br/>

* **爬蟲**<br/>
徐慶崴<br/>
吳湘嵐<br/>
葉韋祥<br/>
(可找人討論互相幫忙,各自精進或分享負責的部分,以便有效率共同學習成長 )<br/>

### 2.目標
1. 精準預測某時段、區域需載客數 (參考meeting-1)<br/>
   找出熱點區域、月份、週期延伸提高派車連續性、增加營收、尋找客群權重並與廣告或周邊商品連結
2. 最後以網頁or APP呈現<br/>
   4個input(降雨機率、日期、時間、區域)<br/>
   2個output (預測人數、預測區域乘客範圍)<br/>

### 3.需要工具(知道更多可使用工具或Know how的人請補充)
1. 爬蟲 Python (Hadoop, Spark)
2. 資料清洗 CSV, JSON
3. 資料庫建立 SQL
4. 機器學習 TensorFlow
5. 網頁架設 Java, Python


### 4.統計(依目前資料可完成)
* **第一階段**<br/>
<br/>
**依照區域分成25塊**<br/>
1. 統計每區域整年載客數(找出熱點區域)是否為市中心(捷運數特多?商圈區?)
2. 統計每區每個月載客數(找出熱點月份)是否為寒暑假或有活動的月份(季節影響?觀光季?)
3. 統計整年星期X載客數(找出熱點週期)平日or假日乘客居多(上班族?假日ktv族?)
4. 統計整年每星期X特定時間區段載客數(找出熱點時段)是否有固定客戶(客源?)
<br/>
**找出各項熱點意義** (可再多提影響熱點權重因子，以利增加欄位)<br/>
<br/>
1. 找出熱點區域可找出月/週/時上限與下限,思考派車路線連續性(減少空車時間)[需取得下車資料]、與其他交通運輸合作(提高營收)
	[與google map連結,熱點方圓散佈區可推薦大車隊與之合作,並找出熱點(捷運站,ktv等)權重]
2. 找出熱點月份可思考淡旺季派車分配(提高載客率)、針對特殊月份增加派車(增加特殊月份收益)[需與溫度做mapping,取得氣溫,降雨,風速等影響權重]
3. 找出熱點週期針對熱點週期找尋熱點時段,並推估客群(針對特定客群推出會員優惠方案,提高廣告效果,增加收益)[尋找客群權重]



* **第二階段**<br/>
機器學習(待討論)<br/>
依照區域分成25塊<br/>
1. 利用機器學習分類某降雨機率時,同星期X某時段同溫度區間[增加溫度欄位,採去二分或三分法]之下,平均人數,mapping降雨機率0時同星期X某時段同溫度區間之下的平均人數 
2.以週期計算,並以經緯度熱點產生預測乘客區域載點範圍(以類神經網路模擬出區域載點範圍)最後視覺化呈現建議預測人數及乘客產生範圍(再討論)

### 5.目前需要執行項目
1. 爬天氣資料並與車隊聯絡取得下車資料 -- 徐慶崴, 葉韋祥
2. 第一階段統計,並整合天氣與車隊資料 -- 曾暉雅, 吳湘嵐
3. 建立一系統地圖(與google map結合),輸入經緯度,即在頁面產生紅點--羅文彥,陳尹翊,何佩瑜 (待討論)
(後續可產生每一時段之乘客區間散佈圖,相連成一區塊後,經圖片區塊疊帶供機械學習預測乘客產生範圍有幾筆資料就會產生幾張圖片)

※請按照分配去討論規劃，以利下次開會效率


### 6.資料庫建立
* 欄位1 No. /日期 /星期 /時間區間 
* 欄位2 時間區間/ 時間 
* 欄位3 時間/ 區域 / 經度 /緯度 
* 欄位4 No. / 溫度 / 降雨機率/ 濕度/ 風速

> No./ 溫度/ 降雨機率/ 濕度/ 風速/ 日期/ 星期/ 時間區間/ 時間/ 區域 / 經度/ 緯度

### 7.整合
1. 所有權重整合預測目的
2. 架設網頁視覺呈現 

> 再建甘特圖、DFD(徐慶崴、曾暉雅)

* * *
