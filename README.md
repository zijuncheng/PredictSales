# Sales Prediction

This is the solution to the [Kaggle Competition: Predict Future Sales](Kaggle) where one is required to predict the next monthly sales for each shop and item.


### Installation
----------------------------------
##### Data 
  This is provided by Kaggle.
  

##### Install the Requirements
  Install the requirements using ```pip install -r requirements.txt```

### Models
----------------------------------
 - XGboost (xgb)
 - Random Forest (rf)
 - Multiple Layer Perceptron (MLP)
 - Long-Short Memory Model (LSTM)
 
### Features
----------------------------------
 - Monthly Sales by shop and item (cnt)
 - Monthly Sale Prices by shop and item (price)
 - Items' detailed categories (cat0)
 - Items' detailed categories (cat1)
 - Shops' id (shop_id)
 - Items' id (item_id)
 - Seasonal effect (season)
 - Block Averages of Sales for every 6 months (cnt_block)
 - Block Averages of Prices for every 6 months (price_block)
 
 
### Performance
----------------------------------

The baseline model offers a test rmse of 45 while the rmse for predictions restricted to [0,20] (which is the evaluation standard of this competition) is 4.19.

Please find below the results before any restriction:

|feature/model (rmse) | XGboost | RF | MLP      |LSTM |
|---- | --- | ---| --- | --- |
|cnt + price + cat0 + cat1 + shop_id + item_id (before transforming to one table with lag variable)| 9.7  | 9.6  | 9.8 | NA |
|cnt + price + cat0 + cat1 + shop_id + item_id (after transforming to one table with lag variable)| 3.59  | 5.07  | 3.6 | NA |
|cnt_block + price_block   | 3.58 | 5.27 | 3.6 | NA |
|cnt + price + season (12 month window)  | NA | NA |NA | 4.39|
|cnt + price + cat0 + cat1 + shop_id + item_id +season (3 month window)   | NA   | NA| NA | 4.37 
|cnt + price + cat1 + shop_id + season (4 month window)   | NA   | NA| NA | 4.39


Please find below the results clipped to [0,20]:

|feature/model (rmse) | XGboost | RF | MLP      |LSTM |
|---- | --- | ---| --- | --- |
|cnt + price + cat0 + cat1 + shop_id + item_id (before transforming to one table with lag variable)| 1.25  | 1.25  | 1.31 | NA |
|cnt + price + cat0 + cat1 + shop_id + item_id (after transforming to one table with lag variable)| 0.82  | 0.78  | 0.77 | NA |
|cnt_block + price_block   | 0.82 | 0.86 | 0.78 | NA |
|cnt + price + season (12 month window)  | NA | NA |NA | 0.75|
|cnt + price + cat0 + cat1 + shop_id + item_id +season (3 month window)   | NA   | NA| NA |  0.81
|cnt + price + cat1 + shop_id + season (4 month window)   | NA   | NA| NA | 0.78

##### Further Improvement

- Validation was not performed on any model except MLP due to time and memory constraint. More cloud resources is needed to perform hyper-parameter tuning on LSTM.

- Selective features or more in-depth feature engineering on the time series

- Other types of Neural Network models could be tested to improve results.


[//]: Citations

   [Kaggle]: https://www.kaggle.com/c/competitive-data-science-predict-future-sales

   