
# Problem Statement

A group of large investors is investigating the prospects of using Big Data to maximize their ability to flip homes nationally. They have contracted me to do an initial discovery of predictive modeling to find interesting and unique data that may help them gain an advantage over their competitors. 

The competition is fierce and fairly well established. The below companies use big data as a core strategy in their real estate business model. 

Zillow
www.zillow.com
Open Door
www.opendoor.com
Offerpad
www.offerpad.com

Even financial firms like Blackrock are gobbling up large swatchs of real estate using data to drive their decisions. 

Blackrock
https://www.blackrock.com/institutions/en-axj/strategies/alternatives/real-assets

# Conclusions

After conducting this preliminary study it is recommended that this group of investors invest further resources to refine and develop the predictive model developed in this report. 

This report showed feasability in identifying unique and obvious correlations (See summary of EDA below) that can combine to help reduce error in purchasing homes and even purchasing homes at scale. 

I recommend the further study focus on three main objectives:

1) Secure large and reliable real estate data sets for the purpose of training predictive models. 
2) Employ a team of data scientists to train a predictive model on the large data set. 
3) Secure relationships with key data providers to ensure easy access to large amounts of accurate real estate data providers/housers. 

If the commissioners of this report see it so fit I will consult on every aspect of the above named objectives. 


# Data Dictionary

can be found at this link:
http://jse.amstat.org/v19n3/decock/DataDocumentation.txt


# Outside Research
#### And Key Points From Research
#### Found in Notebook 'attempt5_EDA'

https://www.consumerreports.org/home-improvement/8-ways-to-boost-your-home-value/
##### Things that Increase Home Price
* Kitchen Quality is king
* Make Floor Plans work harder
* Energy Efficiency
* Keep it simple and stress-free
* homes that accomodate the elderly
* Paint
* Decks or patios
* outside curb appeal
* smart technology
* energy efficiency

https://www.daveramsey.com/blog/how-to-increase-home-value
##### Things that Increase Home Price
* siding replacement
* stone veneer
* deck addition
* grand entrance
* add space
* energy efficiency
* update systems and appliances
* add tech

https://www.hgtv.com/design/remodel/interior-remodel/30-tips-for-increasing-your-homes-value
##### Things that Increase Home Price
* low-maintenance landscaping
* clean outside
* visually increase square footage
* big return on bathroom updates
* energy efficient fixtures
* kitchen gets good returns
* replace worn carpets or rugs

https://www.opendoor.com/w/blog/factors-that-influence-home-value
##### Things that Increase Home Price
* Home size and usable space
* Age and condition
* Upgrades and updates
* Neighborhood/Location
* The local market (Maybe do outside research regarding the market)
* Economic indicators
* Interest rates

##### I had a question regarding whether I should scale before doing correlations. I found my answer here. 
https://www.researchgate.net/post/Do_we_need_to_standardize_variables_with_different_scales_before_doing_correlation_analysis#:~:text=No%20no%20need%20to%20standardize,alter%20the%20value%20of%20correlation.



 

## EDA and Compendium of Findings

#### Correlations on Ordinals
* Using outside research and a correlation matrix to guide my direction I will look at potential relationships between feature variables and ordinal values. 

#### Overall Quality and Price
* The "overall material and finish of the house" makes a big difference in the sale price. Bigger than all other factors other than sf. 

#### Exterior Quality
* This rating evaluates the quality of the material on the exterior. There is a strong positive relationship between having high end materials on the exterior of the home and selling a home for higher prices. 

#### Kitchen Quality
* Kitchen quality was mentioned in a number of outside sources as being a top source for increasing home value. This is notion is supported by the correlation analysis as kitchen ranks high among correlated featurs as having the most positive relationship with saleprice. 

#### Basement Quality
* There are three ordinal metrics that have a fairly strong correlation with sale price. Based on the regression plot and the correlation matrix the Basement Quality Rating (Which actually measures basement height) appears to be strongest among the three correlated basement ratings. 
* The Basement Exposure Rating which measures the amount of exposure the basement has to the outside sees sales pricing rise as exposure to the outside increases. This could be partially explained by many homeshoppers interests in natural light in their living spaces. 
* The latter rating is based on finish type (which measures livability). Homes that have a basement that are completely livable can be sold for higher prices than homes that have either no basement or are unfinished. 
* If you are looking to find a selling feature in a home look for features that include high basement ceilings, exposure to the outside and livable space. This follows the heuristic that people generally like open floor plans and spaces in their homes. 

#### Garage Finish and Price
* Garage finish and price also has a fairly strong positive correlation. People in Ames, Iowa are able to garner more from a sale of their home if their garage is finished. 

#### Heating Quality and Condition
* There is a fairly strong upward based correlation with Heating Quality and Condition rating and price. It appears that homes with a better heating rating in Ames, Iowa are able to command higher prices for their homes. 

#### Lot Shape and Size
* There is a positive relationship with lot shape and price. 
* As lot shape becomes more irregular the baseline sale price increases. If a lot becomes too irregular, however, then the topline sale price is capped out around the mean. 
* This could indicate that larger and more costly homes have larger lots that are more irregular than standard, efficiently parceled lots. 

### Total Square Feet and Sale Price
* The relationship that everyone expected also happens to be the most obvious. The bigger the home the better.

### Garage Area and Number of Cars a Garage Can Fit Are Highly Correlated To Each Other. 
* I will remove the number of cars feature from the dataframe. It is too highly correlated to garage area and features should not be correlated to each other. 
* There is a strong correlation for both measure in relation to sale price but I will include Garage Area because I feel it to be a more precise measure of garage size and has less risk to subjective measurement.

### Total Baths and Sale Price
*Strong correlation to bathrooms and sale price. There are some outliers that stick to the lower end of sale price and those may be miscategorized single family homes that are actually multi-units or something along those lines. 

### Year Built and Year Remodeled and its Relation to Sale Price
* Another somewhat obvious strong correlation. The younger a home, the more value it will get when all else is considered. 
* Not quite as strong of a relation but still fairly strong with positive correlation is year remodeled and sale price. 

### Masonry Veneer Area and Sale Price
* Another very strong relationship. People love stone and masonry on the outside of a house. 
* One caution is that this may correlate with exterior quality. 

### Garage Year Built and Correlation to Year House Built
* There is alot of overlap here. I am going to drop the column garage_yr_blt

### Fireplaces and Sale Price
Positive relationship between fireplaces and Sale Price. It's not quite as densely correlated as some of the previous examples but there is an obvious positive relationship
* [ ] Notice some negative values in this category. How is that possible? going to investigate. 
* Note: the jitter effect is what creates the negative x ticks. It is spreading the values out so they're more noticable. 

### Affect of Year on Sale price
* I expected there to me a larger relationship between year sold and saleprice. The great recession heavily affected housing prices nationally as liquidity dried up and supply flooded the market but in Ames, Iowa this does not seem to be the case at least until 2010. It is possibly that the recession took longer to reach Ames and it would require further data beyond 2010 to examine this relationship. But for the sake of this current study the housing prices are relatively stable and for the sake of making assumptions I will rule out an outsized effect of macro forces affecting price. 

### Foundation Type
* It appears that foundation and sale price have a linear relationship.
* Poured Concrete Foundation has the strongest correlation with year. May consider removing it. 
* Upon further examination with a swarm plot it becomes apparent that most concrete foundations were put in place past 1980 and as a result the year built and foundation type become closely correlated. This could pose a problem for modeling as it violates line assumptions. 

### Sale Type and Sales Price
* Sale Type New is correlated highly with price but also has a high correlation to year built. 

### Garage Type and Sale Price
* Having an attached garage is an advantage for sale price. 
* According to the scatterplot there appears to be some relationship with year built but not strong enough to say they are closely correlated. 

### Having No Stone Veneer
* Having no stone veneer has a negative effect on price. 
* There is a small correlative effect on price as homes built earlier 1920 all were categorized in this way.
* That being said There seems to be a non-relevant correlation to time after that. 

### Garage Type Detached. 
* Has a negative correlation to sale price
* Once again there is some relationship with time but it is not strong based on swarmplot





# Data Cleaning

* In cleaning phase (found in attempt_5_clean notebook) I saved ordinals, numerics and nominal data in seperate csv for cleaning and analysis purposes. The three of them combined comprised the complete training data set (after cleaning and eliminating unuseful data). The ordinal data has been converted to numeric rankings. The nominal data has been converted to dummies. 

### Combine sf columns and delete columns that overlap in purpose
### Combine bathrooms and drop overlapping columns
### Drop totrmsabvgrnd because it is redundant with count of bedrooms and kitchens


### Rank Ordinals Numerically
* Ordinals were subjectively ranked based on domain knowledge. Most were just ordered by rank from worst to best with worst being 1 and best being a higher value at step 1 depending on n length of ordinal values. Some were subjectively decided to have higher than step 1 to achieve a greater magnitude of influence. I tried to do this sparingly but in some cases I thought this would make sense. Ordinals with NA were replaced with 0

### Square Feet and Sale Price Analysis
* There appear to be three identifiable outliers above 6000sf. 
* some of these very large homes do not seem to be selling for what they should selling for on a price per square feet basis. (possible sales to family members for values less than market price, fraud, or error in recording). 
* [X] I will remove these values.  

### Mean, Min., Max, and Standard Deviation for all Columns
* [X] Noticed that ms_subclass is a numerical column when it should be categorical. Change to string object. 
* [X] pid column is also included in the dataframe and is just a reference column used for externally access to individual records. I will remove this column. 

### Examining lot_area
* [X] seems to be a few large outliers in lot area. 471 has 159,000 and 694 has 115,149. The mean is only 10,000. I will run a box plot on this to further examine.
* The largest lot area home at 159,000sf was built in 1958 but remodeled 1 year before sale in 2006. It has large square footage and lot area in relation to sale price but I cannot rule out that other factors affect price. I will not remove this outlier. 
* The second largest lot area also seems legit and not unusual. larger square footage from home that was built in 1971 but remodeled in 2002 before sale in 2007. I will not remove this outlier either. 


### Examining mas_vnr_area
* [X] seems to be some large values in mas_vnr_area. mean is 98 and the five largest values are above 1000. Probably not that unusual for expensive homes but worth examing further. 
* Nothing out of the ordinary with 1600 value. 
* The lower values seem normal as well. I will leave this columns alone. 

### Examining garage_yr_blt
* [X] garage year built has a value pf 2207 which must be wrong. I am going to examine that record to see if there is housing year built or upgrade year data to confirm my suspicion that this is actually meant to say 2007. 
* [X] identified that the house was built in 2006 and year remodeled was 2007 so I am assuming garage year built was 2007 and the 2207 was actually a misprint. Changed the value. 

### Examining misc_val
* [X] largest value is significantly higher than all the rest and much higher than the mean. This is a column where there are also not very many values. I may consider deleting this column or perhaps eliminating the outlier. Need to examine further.
* [X] I have decided to eliminate the misc_val column due to large number of zero values. 

### Examining ttl_bath
* [X] I am deciding to do nothing with the outliers in ttl_bath. I do not think they are not too far, all things considered. 

### Examing saleprice 
* [X] Examine Sale Price. There doesn't seem to exist any unacounted for reasons for larger salesprices. All of the 52 homes that sold for saleprices that were 3 standard deviations above the mean had characteristics that would justify such a sale. There were no homes that sold for less than 3 standard deviations away from the mean. 

### Evaluating Year Sold
* [X] Evaluating year sold. There doesn't appear to be any outliers in year sold.
* NOTE: There is not a full year of data for 2010

### Fill Nulls in Ordinals with value of 1
* I chose 1 because I didn't want a value of zero to ruin any calculations in complex modeling. 

### Add 'saleprice' column to ordinals_df
* adding saleprice to ordinals because I am going to future analysis on just ordinals before dropping saleprice column and concatenating ordinals with other dfs to reform original dataframe





# INITIAL OUTLIER ANALYSIS
* The first outliers I will be targeting will be outliers regardins square footage. In the data dictionary the author mentioned 5 values that may want to be removed because of their outsized effect on the data. He mentioned a simple analysis between sale price and above ground living space would identify them. I have already combined all square footage columns including above ground living space so I will analyze total square feet and sale price. 
* I will then go through value counts, minimum and maximums, standard deviations and nlargest to find initially glaring outliers. There will some use of charts to further elucidate findings. 

### Compendium of Findings and Actions Performed During Outlier Analysis (below)

##### Square Feet and Sale Price Analysis
* There appear to be three identifiable outliers above 6000sf. 
* some of these very large homes do not seem to be selling for what they should selling for on a price per square feet basis. (possible sales to family members for values less than market price, fraud, or error in recording). 
* [X] I will remove these values.

##### Mean, Min., Max, and Standard Deviation for all Columns
* [X] Noticed that ms_subclass is a numerical column when it should be categorical. Change to string object. 
* [X] pid column is also included in the dataframe and is just a reference column used for externally access to individual records. I will remove this column.

##### Examining lot_area
* [X] seems to be a few large outliers in lot area. 471 has 159,000 and 694 has 115,149. The mean is only 10,000. I will run a box plot on this to further examine.
* The largest lot area home at 159,000sf was built in 1958 but remodeled 1 year before sale in 2006. It has large square footage and lot area in relation to sale price but I cannot rule out that other factors affect price. I will not remove this outlier. 
* The second largest lot area also seems legit and not unusual. larger square footage from home that was built in 1971 but remodeled in 2002 before sale in 2007. I will not remove this outlier either. 

##### Examining mas_vnr_area
* [X] seems to be some large values in mas_vnr_area. mean is 98 and the five largest values are above 1000. Probably not that unusual for expensive homes but worth examing further. 
* Nothing out of the ordinary with 1600 value. 
* The lower values seem normal as well. I will leave this columns alone. 

##### Examining garage_yr_blt
* [X] garage year built has a value pf 2207 which must be wrong. I am going to examine that record to see if there is housing year built or upgrade year data to confirm my suspicion that this is actually meant to say 2007. 
* [X] identified that the house was built in 2006 and year remodeled was 2007 so I am assuming garage year built was 2007 and the 2207 was actually a misprint. Changed the value. 

##### Examining misc_val
* [X] largest value is significantly higher than all the rest and much higher than the mean. This is a column where there are also not very many values. I may consider deleting this column or perhaps eliminating the outlier. Need to examine further.
* [X] I have decided to eliminate the misc_val column due to large number of zero values. 

##### Examining ttl_bath
* [X] I am deciding to do nothing with the outliers in ttl_bath. I do not think they are not too far, all things considered. 

##### Examing saleprice 
* [X] Examine Sale Price. There doesn't seem to exist any unacounted for reasons for larger salesprices. All of the 52 homes that sold for saleprices that were 3 standard deviations above the mean had characteristics that would justify such a sale. There were no homes that sold for less than 3 standard deviations away from the mean. 

##### Evaluating Year Sold
* [X] Evaluating year sold. There doesn't appear to be any outliers in year sold.
* NOTE: There is not a full year of data for 2010





# Directory Structure

```
project_2
|__ attempt_4 (folder)
    |__ attempt_4_null_test.ipynb   
    |__ datasets (folder)
        |__null_sub.csv
|__ attempt_5 (folder)
    |__ code (folder)
        |__attempt5_clean.ipynb
        |__attempt5_EDA.ipynb
        |__attempt5_linearmodel_final.ipynb
        |__attempt5_ridgemodel_final.ipynb
        |__attempt5_test_editing.ipynb
    |__ datasets(folder)
        |__a5_after_eda.csv
        |__a5_numerics.csv
        |__a5_ordinals.csv
        |__a5_str_dummy.csv
        |__a5_str_no_dummy.csv
        |__a5_sub_ridge.csv
        |__a5_test1.csv
        |__a5sub.csv
        |__a5test_ready_4_model.csv
        |__15train_ready_4_model.csv
        |__test_final.csv
        |__train_final.csv
|__starter_data (folder)
    |__ sample_sub_reg.csv
    |__ test.csv
    |__ train.csv
|__ flippin_facts_presentation.pdf
|__ houses.jpg
|__ README.md
```



# Summary of Linear Regression Model
### Located in notebook attempt5_linearmodel_final

* This notebook takes in cleaned data that has had EDA performed on it, does a final clean for the purpose of fitting to model and then performs a linear regression. 

* This regression went through standard scaling, was fit and transformed and fit you a linear regression. 


### Interpret OLS Regression Metrics

* almost 93% of the variation of y is explained by the feature variables according to the R-squared metric. The Adjusted version of R-squared, which accounts for additional variables and their positive or negative impact on the distance of errors only experienced a small drop which is positive for explaining the predictor variables effects on y.

* Prob(F-Statistic) this metric assesses the significance level of all variables together and whether or not all the regression coefficients are equal to zero. This number seems to indicate that there is a high probability that the coefficients are not equal to zero.  

* coef seems to indicate that for each unit of square feet the coefficient moves up about 71,000 dollars in sale price. 

* The P value indicates a greater than 90 percent probability that the results I am seeing in this regression would come up in a random distribution. 

* The Prob(JB) value of zero indicates that the errors of the regression are normally distributed. 

* The bottom of the OLS Summary gives a warning that states that there may be strong multicollinearity or numerical problems. 

THE RMSE SCORE SUBMITTED IN KAGGLE FOR THE OLS REGRESSION was 27,793 and was good enough for sixth place at time of writing this. This is the average distance in dollars the observed data points are from the model's predicted values. 


# Summary of Ridge Regression Model
### Located in notebook attempt5_ridgemodel_final

This notebook takes in a cleaned set of data for each of both training and test data sets. It then returns a RidgeCV regression model. 

### Interpret Ridge Regression Metrics

* The adjusted Coefficient of Determination only false slightly in this model indicating that the distances of the residuals squared is not too far from predicted values. 
* My RMSE score indicates a score of 22382 which would be an improvement upon the 28000 score submitted through Kaggle. This indicates that my training data is performing better than my testing data. Likely an overfit issue.  