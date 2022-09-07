# Project 4: West Nile Virus Prediction

## Contents:
- [Problem Statement](#problem-Statement)
- [Background](#Background)
- [Data Dictionary](#Data-Dictionary)
- [Data Processing](#Data-Processing)
- [Modelling](#Modelling)
- [Cost Benefit Analysis](#Cost-Benefit-Analysis)
- [Conclusion](#Conclusion)
- [Further Studies](#Further-Studies)
- [Recommendations](#Recommendations)



## Problem Statement
We are a team of data scientists from the Disease And Treatment Agency, division of Societal Cures In Epidemiology and New Creative Engineering (DATA-SCIENCE). <br>

Due to the recent epidemic of West Nile virus WNV) in Windy City, we have been tasked by Chicago Department of Public Health to predict the occurrence of mosquitos that would test positive for WNV, based on the data collected over time. 

With a more accurate prediction model, we could help the city to make more informed decisions on the deployment of resources towards preventing transmission of the virus. Given that pesticides are costly, harmful to human health and the environement but yet essential, we will also conduct a cost-benefit analysis regarding use of pesticides to manage the epidemic.

## Background

The West Nile virus (WNV) is the leading mosquito-borne disease in the United States ([source](https://www.cdc.gov/westnile/index.html)). It is most commonly spread to humans through infected mosquitos. Around 20% of people who become infected with the virus develop symptoms ranging from a persistent fever, to serious neurological illnesses that can result in death.

In 2002, the first human cases of West Nile virus were reported in Chicago ([source](https://dph.illinois.gov/topics-services/diseases-and-conditions/west-nile-virus.html)). By 2004 the City of Chicago and the Chicago Department of Public Health (CDPH) had established a comprehensive surveillance and control program that is still in effect today ([source](https://www.chicago.gov/city/en/depts/cdph/provdrs/healthy_living/news/2021/august/city-to-spray-insecticide-wednesday-to-kill-mosquitoes.html)).

Every week from late spring through the fall, mosquitos in traps across the city are tested for the virus. The results of these tests influence when and where the city will spray airborne pesticides to control adult mosquito populations.

Hot and dry weather conditions are favorable for mosquitos breeding ([source](https://www.preventivepestcontrol.com/weather-affect-mosquito-activity/)). The entire life cycle of a mosquito from an egg to an adult takes around 8-10 days ([source](https://www.cdc.gov/dengue/resources/factsheets/mosquitolifecyclefinal.pdf)). With such a short timeline, it is vital that we can predict potential clusters quickly and stop the transmission of WNV.


## Data Dictionary

|         Feature        |  Type  |       Dataset      |                 Description                 |   |
|:----------------------:|:------:|:------------------:|:-------------------------------------------:|---|
| Id                     | Int    | Test.csv           | ID number of record                         |   |
| Date                   | Object | Train.csv/Test.csv | Date and time when WNV test was carried out |   |
| Address                | Str    | Train.csv/Test.csv | Address for trap                            |   |
| Species                | Str    | Train.csv/Test.csv | Species of mosquitoes caught in trap        |   |
| Block                  | Int    | Train.csv/Test.csv | Block number                                |   |
| Street                 | Str    | Train.csv/Test.csv | Street name                                 |   |
| Trap                   | Str    | Train.csv/Test.csv | ID number of trap                           |   |
| AddressNumberAndStreet | Str    | Train.csv/Test.csv | Address                                     |   |
| Latitude               | Float  | Train.csv/Test.csv | Latitude from GeoCoder                      |   |
| Longitude              | Float  | Train.csv/Test.csv | Longitude from GeoCoder                     |   |
| AddressAccuracy        | Int    | Train.csv/Test.csv | Accuracy of info from GeoCoder              |   |
| NumMosquitos           | Int    | Train.csv          | Number of mosquitoes found in sample        |   |
| WnvPresent             | Int    | Train.csv          | Whether WNV is present (1:Present, 0:NA)    |   |
| Date                   | Object | Spray.csv          | Date of spray                               |   |
| Time                   | Object | Spray.csv          | Time of spray                               |   |
| Latitude               | Float  | Spray.csv          | Latitude of spray location                  |   |
| Longitude              | Float  | Spray.csv          | Longitude of spray location                 |   |
| Station                | Int    | Weather.csv        | Weather station (1 or 2)                    |   |
| Date                   | Object | Weather.csv        | Date of measurement                         |   |
| Tmax                   | Int    | Weather.csv        | Maximum daily temperature (F)               |   |
| Tmin                   | Int    | Weather.csv        | Minimum daily temperature (F)               |   |
| Tavg                   | Int    | Weather.csv        | Average daily temperature (F)               |   |
| Depart                 | Int    | Weather.csv        | Departure from normal temperature (F)       |   |
| Dewpoint               | Int    | Weather.csv        | Average dewpoint (F)                        |   |
| WetBulb                | Int    | Weather.csv        | Average wet bulb (F)                        |   |
| Heat                   | Int    | Weather.csv        | Heating degree days                         |   |
| Cool                   | Int    | Weather.csv        | Cooling degree days                         |   |
| Sunrise                | Int    | Weather.csv        | Calculated time of sunrise                  |   |
| Sunset                 | Int    | Weather.csv        | Calculated time of sunset                   |   |
| CodeSum                | Str    | Weather.csv        | Code for weather phenomena                  |   |
| Depth                  | Int    | Weather.csv        | Snow Depth (in.)                            |   |
| Water1                 | Int    | Weather.csv        | Amount of water from melted snow            |   |
| SnowFall               | Int    | Weather.csv        | Snowfall (in.)                              |   |
| PrecipTotal            | Str    | Weather.csv        | Total daily rainfall (in.)                  |   |
| StnPressure            | Int    | Weather.csv        | Average atmospheric pressure (in. Hg)       |   |
| SeaLevel               | Int    | Weather.csv        | Average sea level pressure (in. Hg)         |   |
| ResultSpeed            | Float  | Weather.csv        | Resultant wind speed (mph)                  |   |
| ResultDir              | Int    | Weather.csv        | Resultant wind direction (degrees)          |   |
| AveSpeed               | Int    | Weather.csv        | Average wind speed (mph)                    |   |

## Data Processing

Basic data cleaning for the four datasets provided are done to tackle the erroneous, outlier,  null and duplicated values. Columns that contain null values in excess of 50% and if deemed to have little impact on the modelling or helping us understand the problem are dropped from the datasets. Temperature range (Trange) and relative humidity columns have been created to help enchance to the model.Since we are working to reduce mosquito breeding in the city, we will also take into consideration the life cycle of a mosquito, and examine the weather conditions when the eggs are hatched and/or larvae are developing. Therefore, we have create 7-day and 14-day rolling weather features of the date for 13 of the weather features. Finally, weather data for Station 1 and Station 2 have been aggregated for each day before merging with the train dataset.

EDA was then conducted to provide more insight into the problem statement as well as to eliminate less useful features to reduce noise during our modelling process. 

Key findings from EDA:

1. Majority of mosquitos caught are Culex pipiens and Culex restuans.
2. The mosquito species found with WNV belongs to Culex pipiens and Culex restuans as well
3. It is believed that hot and dry conditions are more favorable for West Nile virus than cold and wet.
4. The number of cases seem to increase from July (week 27), peak in Aug (week 34) and decline by end Sep (week 40).
5. As the period between Jul to Sep is Summer in Chicago, the weather would become hotter and drier, which are favourable conditions for mosquitos to breed.
6. Comparing across the years, the surge would start from July, peak in Aug and decline after Sep.
7. Looking at Yearly WNV occurrence, the cases declined in 2009 but increased after, in spite of spraying efforts made in 2011 and 2013.
8. For 2011, the reduction of cases could be due to the end of season, as the spraying was conducted in Sep.
9. For 2013, the WNV clusters continued to increase despite the spraying efforts. More information would be required to determine whether spraying is ineffective or a change in strategy is required (e.g. targeted spraying).

After checking for mulitcollinearity, 15 features are dropped and one-hot-encoding was carried our for "Species" and "Month" before the modelling.

## Modelling

Modelling is done by contructing 4 modelling pipelines. For all the 4 pipelines, data are scaled, put through SMOTE to address the imbalanced dataset and lastly a classifier. GridsearchCV is conducted on all four pipeline to derive the best parameters for each model. A summary of the modelling results is compiled in the table below:

|   |      **Classifier** | **Train** | **Test** | **ROC_AUC CV** | **Train-Test** |
|--:|--------------------:|--------------|----------------|-----------------|------------|
| 1 | Random Forest       | 0.818        | 0.799          | 0.803           | **0.019**  |
| 2 | AdaBoost            | 0.856        | 0.818          | 0.831           | 0.038      |
| 3 | XGBoost             | 0.895        | 0.841          | **0.840**       | 0.054      |
| 4 | Logistic Regression | 0.851        | 0.829          | **0.836**       | **0.022**  |

From the above table, we observe that the Random Forest model suffers the least overfitting, with train score just 0.019 above the test score. This is closely followed by the Logistic Regression model of o.022 difference between the train and test scores.

However, the Random Forest model scored lowest for ROC_AUC metric while the Logistic Regression acheive the second highest score of 0.836, losing out marginally to the XGboost model which is also the most overfitted model.

Therefore, having considered both the ROC AUC score and how well the model fits, our group has choosen the Logistic Model in this case as our model of choice.

## Cost Benefit Analysis

Based on the weekly plot of spray area and Wnv present case in mosquito traps, it seems that the spray areas are mostly determined by the previous week's data of area where Traps contain Wnv positive mosquitos. However, not all Trap areas with Wnv positive case were being sprayed; hence, the spray strategy in 2013 is unknown and can be further improved.

Nevertheless, it is clear from the weekly plot above that the spraying worked in areas with Wnv positive; as mosquitos in the same area with Wnv positive disappear in the following week after spraying.

We observed that even though the spraying effort in 2013 increases by 7.57 times compared to 2011, the ratio of Wnv Mos:Human did not decrease by 7.57 (but by 0.86 instead).

This suggests that the spraying strategy has lots of room for improvement.

*Chicago West Nile Virus 2019 data brief

By visually inspect the number of traps which the spraying in 2013 were conducted because of Wnv positive case (Total: 14), we can calculate the average no. of spray per Wnv postive trap.

The CDPH uses Zenivex E4 for the Vector Control Program which is usually carried out from July to September each year. Based on the spray data, the spray night is carried out once a week. The product is sprayed by a truck-mounted fogger in a process known as Ultra Low Volume (ULV) fogging. The rate of application of the fogging product is 1.5 oz per acre (375 oz per sq km).

The price of a 55 gallon (7040 fluid oz) Zenivex E4 is estimated to be US$ 1045 based on 2021 value.

The cost of spraying per year is US$6100.22

The estimated weekly cost per surveillance unit for mosquito traps is about US$ 83 (in 2021 value) in California between 2004 to 2012. This includes expenses for field processing, lab processing and testing. We will use the same figure in our analysis. (source) Since there are 138 traps in the train dataset, the total trap surveillance cost per year is as follows:

The cost of trap surveillance per year is US$148902

The total cost of vector control and trap surveillance per year is US$155002.22

Sources: <br>

https://www.chicago.gov/content/dam/city/depts/cdph/Mosquito-Borne-Diseases/Zenivex.pdf

http://legacy.elpasotexas.gov/purchasing/docs/2016-741%20BID%20TAB.pdf?6/28/2021%209:39:13%20AM

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4340646/

## Conclusion

It was observed that about the virus is present in about 5.19% of the number of mosquitoes caught The mosquito species containing the virus are from the genus 'Culex' and species 'Restuans' and 'Pipiens', with crossbreed Culex Restauns/Pipiens These species are considered pests and they are likely to have very close similarities with each other. The virus are not found in the mosquitoes species 'Erraticus', 'Salinarus', 'Tarsalis' and 'Territans' which are caught, this means that it is unlikely that they would carry the virus however we would not rule out that possibility.

It was observed that across the years, 2007 to 2013 there are similar number of mosquitoes caught with the virus with the most cases recorded at July and eventually subside (decreasing trend) by November. This is due to the climate/season and temperature changes. Refering to the linegraph, temperature and rainfall peaks at July and generally decreases towards November in similar fashion/trend. This is reflected by the number of positive cases and the number of mosquitoes caught around July to October.

There is a slight upward trend in the presence of west nile virus. Hence We suggest that the local authorities to focus efforts on their preventive measures where areas are predicted to have at least 60% probability of having West Nile Virus.

The costs of any vector control program ideally should reduce the likelihood of citizens contracting WNV and therefore the ensuing the medical and economic costs of contracting the WNV. We will now attempt to quantify these costs.

Sources: <br>
https://www.ecdc.europa.eu/en/all-topics-z/disease-vectors/facts/mosquito-factsheets/culex-pipiens-factsheet-experts

https://vectorbio.rutgers.edu/outreach/species/rest.htm

## Further Studies

1) **The study of weather patterns on mosquito behaviour** As observed in our EDA section, the relationship between the weather features is still unclear. On top of this, it can be observed that the presence of WNV peaks around the approximately same few months, regardless of weather patterns. This could also indicate that there could be other influencing factors, for example dense human population in certain areas.

2) **Understanding mosquitos WNV transmission** As WNV is only transmitted by either Culex Restauns, Culex Pipiens and their crossbreed, by understanding this specific species behavoir and areas that breeds them would allow us to investigate where they get the virus from and perhaps curb the spread by curbing the root problem.

3) **More training data** Our model was trained on 10506 observations, but we were making predictions on 116293 observations. Our predictions may improve tremendously, if we can acquire more data for our model training.

4) **Targeted mosquito spraying and data collection efforts** To maximise city resources, all mosquito-borne disease statistics should be handled by a single dedicated department in the city council. That way appropriate steps can be taken quickly, eliminating administrative lag between testing and reporting. Regular mosquito pre-spraying efforts should also be undertaken in summer months at mosquito hotspots, where identified to have a higher probablity of the presence of the WNV virus.

Mosquitoes hotspots can be the places where the traps have captured most mosquitoes or streets found with virus present.

**Individual medical costs**
Depending on the age of the patients, the severity of the illness may vary from mild and self-limiting symptoms similar to influenza to severe conditions affecting the central nervous system.

We will use data from a similar study from California in 2005 to estimate the total medical costs incurred by each patient. In Sacramento, California, 71.8% of WNV cases were mild and influenza-like, while 28.2% of cases developed conditions affecting the central nervous systoem. On average, patients who developed serious conditions spent US$46551 on inpatient and outpatient treatment, while mild cases incurred US\\$ 167 in medical cost. Taking the weighted average, the amount spend on medical costs due to WNV is US\\$ 13247

**Economic Cost**

Patients who contracted the severe form of WNV missed about 50 days of workday on average, according to the same study from California in 2005 This translates to about US\\$14777 per case in 2021 value. Mild cases resulted in economic loss of US\\$1218 per case. Once again we take the weight average which is US$5042.

The cost of contracting WNV per case per year is US\\$ 18289
The cost of contracting WNV per year is US\\$ 1207074
The average WNV damages for 1 individual infected (average)against cost of prevention in a week is 1.59

## Recommendations

Based on our prediction model, the mosquitoes management team can plan the spray strategy for the upcoming mosquito season on a weekly basis.

For example, using the weather data and mosquito count of PIPIENS/RESTUANS this week to predict Wnv positive trap area for the following week.

|        | Option 1                                                                           | Option 2                                                                                   | Option 3                                                                                      | Option 4                                                                                                     |
|--------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Method** | Spray all Wnv Positive Areas                                                       | Spray based on community areas                                                             | Spray based on distance from 2 key points                                                    | Release genetically modified mosquitos                                                                       |
| **Pros**   | Wnv positive mosquito can be dramatically reduced, thereby reducing Wnv human case | Reduce Wnv positive mosquitos in area of high risk while saving cost of spraying           | Cost\-effective method that only target high risk Wnv positive area based on train datasets   | Long term solution that can address future mosquito problems, which are bound to worsen due to global warming |
| **Cons**   | Spraying all positive Wnv areas can be very costly                                 | Singular traps with only 1 Wnv positive mosquito will be missed out despite potential risk | Assume that most Wnv positive mosquitos came from these 2 areas while missing out other areas | Require a significant R&D investment cost & time to implement                                                |
| **Cost** | \$416,658 | \$$1,220,213 | \$1,056 |  \$3,599,880|

Based all the 10 weeks plot of spraying & Wnv positive trap of Chicago in 2013, we can conclude that spraying does have a positive effect on controlling Wnv human cases. However, as the spray strategy seems to be based on current week's trap data, the spraying areas are always lag by 1 week and made the spraying effort sometimes useless. 

Our logistic regression classification model is able to predict the presence of Wnv positive in each mosquito trap, with an accuracy of (score). Using the classification model, we can predict next week's Wnv presence based on this week's data and plan the spraying strategy with the 4 options given above. 

More information would be required to make the model more accurate at predicting, such as 

1) Number of mosquito in test dataset

2) Number of Wnv human cases and area of infection

3) More spray area data other than 2011 and 2013

Nevertheless, we conclude that our logistic regression classificaion model has performed up to expectation in predicting Wnv presence in Chicago. 

### Other References

https://www.cdc.gov/westnile/statsmaps/cumMapsData.html
https://chicagoflaneur.com/2016/06/20/a-different-way-of-looking-at-density-in-chicago/
https://www.sporcle.com/games/No1LesbroinChi/populated_chicago_neighborhoods/results
https://www.sciencedaily.com/releases/2014/02/140210184713.htm
http://www.cidrap.umn.edu/news-perspective/2004/07/west-nile-magnifies-need-mosquito-control