# BBCA Monthly Prediction

The goal of this repository is to find accurate prediction of BBCA future price in a scale of month

This goal will be achieved by using the following steps :

- Find the best **anual** prediction
- Find the best month _progress_ prediction

Word _progress_ could be used as the followings :
If the 2024 annual price value prediction is 10.000 and the 2024 Feb price value is 9900, then the price _progress_ in Feb 2024 is 0.99

The preceeding approach is used for it's _ability_ to account annual patern such as :

- BBCA revenue report release month
- BBCA dividend month
- BBCA market behavior pattern such as :
  - Sell in May and go away
  - Santa Claus rally
- BBCA monthly growth rate

### 1. Annual Price Prediction with Book Value Growth

Blue chip companies, including BBCA, are known for their stable growth, **including their book value**. With this stability assumption, the book value growth will be used as a predictor in this repository

As what can be seen from _/analysis/book-value-growth-to-price.ipynb_, it can infered that the 3 year book value growth is the best prediction with MAE of 8,1%

Therefore, with this foundings, **the 3 year book value growth will be used in this finding**

### 2. Monthly Progress Prediction with Past Mean

#### 2.1 The future price progress is equal to past data progress

As what can be seen from _/analysis/monthly-progress-by-book-value.ipynb/2.1_, **using the 3 years PBV prediction**, below error would be yield using below interval prediction

2 Error 0.082194
3 Error 0.074152
4 Error 0.073283
5 Error 0.069028

It could be seen that the future price progress deviates by noticable error from past years data

However, there is an important finding here. With the following data, It can be seen that the error has a **decent value of auto correlation**, giving the idea that the (n+1) month error could be lessen by using the n month error

- Auto-correlation at lag 1
  0.8107538057634408

- Auto-correlation at lag 2
  0.6505485578362517

- Auto-correlation at lag 3
  0.47869674654100686

#### 2.2 The future price progress is **proportionally** slower or faster to past data progress

As what can be seen from _/analysis/monthly-progress-by-book-value.ipynb/2.2_, below correlation would be yield

- Correlation between Progress and 2 Mean
  0.11281834412521277
- Correlation between Progress and 3 Mean
  0.1784384698247065
- Correlation between Progress and 4 Mean
  0.08513449202465924
- Correlation between Progress and 5 Mean
  0.32482617198880026

Explaining preceeding data, it could be inferred that **the future price progress has weak correlation with past years data**

With this findings, it could be infered that **prediction alone by book value growth is not enough to predict the future price progress**

### 3. Exchange Rate Impact to Prediction

The idea is the exchange rate, which is the USD to IDR exchange rate, could adjust the prediction so that the prediction could yield less error

As what can be seen from _/analysis/exchange-rate-impact-to-prediction.ipynb_, below correlation would be yield

The correlation between the price of the stock and the dollar
0.8569405888871475

Correlation between Dollar Difference and 2 Error
0.15188777387659264

Correlation between Dollar Difference and 3 Error
0.18525925742884466

Correlation between Dollar Difference and 4 Error
0.1522413961860319

Correlation between Dollar Difference and 5 Error
0.2092657170069175

With preceeding data, **it is true that the dollar price have decent impact on BBCA stock price**. Sadly, the dollar difference could not be used to adjust monthly progress prediction. In other word, **the dollar difference is not the primary cause of monthly progress**
