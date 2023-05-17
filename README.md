# Marketing-Mixed-Model
Build marketing mixed model to assess the success of promotions and marketing partnership of a beer brand with ACSE supermarket. Identify promotion and marketing activities that can drive significant incremental sales to continue in next year. 

# Convert GRPs to Reach
First, convert GRP to Adstock values by inputing GRP values and the Adstock half-life. The returned Adstock values represent the diminishing effect of past advertising exposures on current sales. Then, convert Adstock values to reach, which represents the estimated number of people who were exposed to the advertising campaign.


  def grp_adstock(grp, h):

    r = 1 - 0.5**(1/h)
    
    adstock = np.zeros(len(grp))
    
    adstock[0] = grp[0]
    
    for i in range(1,len(grp)):
    
        adstock[i] = r*grp[i] + (1-r)*adstock[i-1]
        
    return adstock
 
 
  def ads_reach(ads, a, b):

    reach = a*(1-np.exp(-b*ads))
    
    return reach
    
# Modeling
The marketing mix model is typically a linear regression model that includes the base variables(e.g., price, seasonality, holidays), marketing variables (e.g., advertising, promotions) as predictors, and sales as the outcome variable.

To capture the non-linear relationship between marketing features and sales, multiplicative models are more appropriate than additive models. The impact of each input on sales is multiplied together, resulting in an exponential additive relationship if the target variable is transformed using a logarithmic function.

To evaluate the model performance in terms of predicting accuracy and generalization on future sales, various metrics are applied, including R-squared, RMSE, MAPE, AIC, and VIF.

# Conclusions
1. For San Miguel Especial in 2019 and 2020, the flyer promotion had the highest ROI with a value of approximately 40%. The radio promotion followed with an ROI of 26.15%, while TV had an ROI of 20.57%. 
Also, the flyer promotion had the highest ROI with a value of approximately 40%. The radio promotion followed with an ROI of 26.15%, while TV had an ROI of 20.57%. The graph visually illustrates the effectiveness of different promotions and highlights the flyer promotion as the most successful in terms of ROI for both years analyzed. This information can be used to inform future marketing strategies for San Miguel Especial and allocate resources effectively to maximize ROI.
![alt text](https://github.com/zwxxx121/Marketing-Mixed-Model/blob/d2a3c1f1c079a9d6f835d9a55f80327120298fe6/MMM1.png)
![alt text](https://github.com/zwxxx121/Marketing-Mixed-Model/blob/3f26d50bed33e7822d35c6f3a923e9c5fc2de971/MMM3.png)
2. For San Miguel Especial 6pk in 2019 and 2020, Google paid search has the highest ROI with a value of 93.06%, followed by radio promotion at 77.21%, TV at 64.96%, and flyer at 57.15%. Based on our analysis of the San Miguel Especial 6 PK promotions, we recommend continuing the flyer, TV, radio, and Google paid search promotions in 2023. Specifically, we recommend increasing the emphasis on Google paid search and TV promotions.
![alt text](https://github.com/zwxxx121/Marketing-Mixed-Model/blob/3f26d50bed33e7822d35c6f3a923e9c5fc2de971/mmm2.png)
![alt text](https://github.com/zwxxx121/Marketing-Mixed-Model/blob/3f26d50bed33e7822d35c6f3a923e9c5fc2de971/MMM4.png)
