# StockPred

*** Testing random changes

*** Testing another change to see if it workds

This project here is to create an ML model that can predict the stock price of NVIDIA using ARIMA. The python notebook file is the main file.

## PROJECT SUMMARY:

<br>

ARIMA model, the based model,  has been used to predict the future closing values of NVIDIA stock prices. The closing value has been selected as the price to predict because this price is the one that is set at the end of the day. The primary challenge of using ARIMA to forecast stock prices is the various factors can fluctuate and abruptly change the price. To compensate for that, it is required to decompose the data into trend, seasonal, and residual components. 

<br>

Classical multiplicative decomposition is used here as it has an exponential trend. Among these components, only the residual component is required to have ARIMA model to forecast values. A simple Exponential Smoothing can be used to predict the trend data. As for Seasonal data, it is not required for any model to predict it as the data is repeatitive in nature. 

<br>

ADF testing is an important part of ARIMA model selection. The testing is done for signifance testing as it is required to reject the null hypothesis, which is that the data is non-stationary. The alternate hypothesis is that the data is stationary. If the un-decomposed data was given in ADF testing, then it would have failed. So, the residual component is seperated and tested in ADF testing. The p value was 3.82032654342485e-14 so it passed the ADF test and thus the null hypothesis can be rejected.

<br>

Afterwards, the data is seperated into three parts: Trainig (60%), Validation (20%), and Teting (20%). However, the original data selection was for a date range between 2000-01-03 and 2023-12-31. The rest of the data is for side-by-side comparision of the predicted and actual close value.

<br>

The ACF and PACF graph is required to set the p and q hyper-parameters of the ARIMA. Since there is no differencing to account for, d = 0. 

<br>

After the model value has been decided, just as a precaution, auto ARIMA is used to get the best hyper-parameter value. With the appropriate values of p and q 3 models were trained and validated on the validation dataset. The MSE and MAE scores gives an idea if the model is properly able to forecast. For the model that has a high MSE and MAE value, should not be used to predict values. Also, with the very low AIC, BIC and MQIC, we can say that the model is not overfitting.

<br>

Among the 3 models, the ARIMA model with p = 5, d = 0, and q = 5 was selected as it showed low mean squre error. Also, it showed in the auto ARIMA suggestion. After all this, decomposition of the data needs to be reverted back by multiplying all the forecasted values. A 30 day forecast of the closing value was done  and compared with actual closing values. The starting date is 2024-01-01 and end date is 2024-01-30. The graph is attached here.


Limitation of the model:

1) This model is only applicable for NVIDIA stocks. For other stocks, model needs to be trained on new set of data.
2) The model does not take into account of other factors that could be responsible for drastic change in the closing price
3) It is sensible to outliers.
4) Without decomposing to several components trend, seasonal and residual, this model will not work.

Improvements of the model:

1) More fine-tuning is required and several other values of p and q needs to be tested.

![image](https://github.com/omi-akif/StockPred/assets/45337017/f39968fa-022a-4646-8fc7-7ab0a6a92cc8)


Code Running Screenshots

![image](https://github.com/omi-akif/StockPred/assets/45337017/084bc0ce-1330-4388-bacc-bdd17ec5706c)



<br>

The development of this code was in Linux environment. It is unclear for other environments as it has not been tested for those.

<br>

To use this, you need to create a virtual environment using the following command. Also, you need to have Python 3.10. 

<br>

First clone the repository. Then, open up a terminal, and go to the directory where you saved it. Run the following command to create a virtual enviroment:


```

python3 -m venv /home/test/stock

```

Make sure to activate the environment:

```
source /home/test/stock/bin/activate

```




<br>

Afterwards, you run the following command to install the requirements

<br>

```

pip install -r requirements.txt

```


This will install all the requirements to the environment to run the file. 


<br> 

And then, you just type the command in the directory where the git repository has been saved.


<br>


```

jupyter lab

```


You fire up a browswer tab and go to your localhost. You need to copy and paste this URL in your browswer.

![image](https://github.com/omi-akif/StockPred/assets/45337017/434d4dd9-32ff-4f4e-a7ac-a24590e8167d)





<b> In the python notebook file, you will see details of how the model was created. <b> 

