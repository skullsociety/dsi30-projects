# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Kaggle Competition - Starter

## Introduction

Due to the recent epidemic of West Nile Virus in the Windy City, we've had the Department of Public Health set up a surveillance and control system. We're hoping it will let us learn something from the mosquito population as we collect data over time. Pesticides are a necessary evil in the fight for public health and safety, not to mention expensive! We need to derive an effective plan to deploy pesticides throughout the city.  
  
To analyse weather, location, testing and spraying GIS data to build a statistical model for the **optimal prediction of the presence, time, location and species of West Nile Virus (WNV) in Chicago.**

Concurrently, The Chicago Municipality and Chicago Department of Public Health is interested in identifying the highest number of WNV cases possible (sensitivity) rather than avoid False Positives, (where WNV is predicted but there isn't a case). 

This is due to the high cost of an undetected WNV (due to health implications) as compared to the cost involved in spraying an area with presticide due to a false alarm.

Success is evaluated by ensuring that the model has the **highest Area Under the Curve score**, which signifies that the model is robust enough to allow flexible choice of thresholds. This can be verified on the Kaggle Website.

The Chicago Municipality and Chicago Department of Public Health can choose the model with the **highest sensitivity when WNV is pandemic** and subsequently, model with the **highest precision** when the number of incidences is lower.

## Dataset

The dataset, along with description, can be found here: [https://www.kaggle.com/c/predict-west-nile-virus/](https://www.kaggle.com/c/predict-west-nile-virus/).


## Summary

- West Nile Virus is most commmonly spread through infected mosquitos
- 20% of people who are infected, develop symptoms ranging from fever, to serious neurological illness and death.
- In 2002, first human cases of WNV	were reported in Chicago. By 2004 the City of Chicago and the Chicago Department of	Public Health (CDPH) had established a comprehensive surveillance and control program.
- Every week, mosquitos in traps across the city are tested for the virus. The results of these tests infludence when and where the city will spray pesticides.
- Given weather, location, testing, and spraying data, Chicago Municipality and CDPH 

## Recommendation and conclusion

It was observed that about the virus is present in about 5.19% of the number of mosquitoes caught
The mosquito species containing the virus are from the genus 'Culex' and species 'Restuans' and 'Pipiens', with crossbreed Culex Restauns/Pipiens
These species are considered pests and they are likely to have very close similarities with each other.
([*source*](https://www.ecdc.europa.eu/en/all-topics-z/disease-vectors/facts/mosquito-factsheets/culex-pipiens-factsheet-experts))
([*source*](https://vectorbio.rutgers.edu/outreach/species/rest.htm))
The virus are not found in the mosquitoes species 'Erraticus', 'Salinarus', 'Tarsalis' and 'Territans' which are caught, this 
means that it is unlikely that they would carry the virus however we would not rule out that possibility.  
  
It was observed that across the years, 2007 to 2013 there are similar number of mosquitoes caught with the virus with 
the most cases recorded at July and eventually subside (decreasing trend) by November. This is due to the climate/season
and temperature changes. Refering to the linegraph, temperature and rainfall peaks at July and generally decreases towards November in similar fashion/trend. This is reflected by the number of positive cases and the number of mosquitoes caught around July to October.  

There is a slight upward trend in the presence of west nile virus. Hence We suggest that the local authorities to focus efforts on their preventive measures where areas are predicted to have at least 60% probability of having West Nile Virus.

The costs of any vector control program ideally should reduce the likelihood of citizens contracting WNV and therefore the ensuing the medical and economic costs of contracting the WNV. We will now attempt to quantify these costs.

**Further studies** 

**1) The study of weather patterns on mosquito behaviour**
As observed in our EDA section, the relationship between the weather features is still unclear. On top of this, it can be observed that the presence of WNV peaks around the approximately same few months, regardless of weather patterns. This could also indicate that there could be other influencing factors, for example dense human population in certain areas.
  
**2) Understanding mosquitos WNV transmission**
As WNV is only transmitted by either Culex Restauns, Culex Pipiens and their crossbreed, by understanding this specific species behavoir and areas that breeds them would allow us to investigate where they get the virus from and perhaps curb the spread by curbing the root problem.
  
**3) More training data**
Our model was trained on *10506* observations, but we were making predictions on *116293* observations. Our predictions may improve tremendously, if we can acquire more data for our model training.

**4) Targeted mosquito spraying and data collection efforts**  
To maximise city resources, all mosquito-borne disease statistics should be handled by a single dedicated department in the city council. That way appropriate steps can be taken quickly, eliminating administrative lag between testing and reporting. Regular mosquito pre-spraying efforts should also be undertaken in summer months at mosquito hotspots, where identified to have a higher probablity of the presence of the WNV virus.  
Mosquitoes hotspots can be the places where the traps have captured most mosquitoes or streets found with virus present.

**Individual medical costs**  
Depending on the age of the patients, the severity of the illness may vary from mild and self-limiting symptoms similar to influenza to severe conditions affecting the central nervous system.

We will use data from a similar study from California in 2005 to estimate the total medical costs incurred by each patient. In Sacramento, California, 71.8% of WNV cases were mild and influenza-like, while 28.2% of cases developed conditions affecting the central nervous systoem. On average, patients who developed serious conditions spent US\\$ 46551 on inpatient and outpatient treatment, while mild cases incurred US\\$ 167 in medical cost. Taking the weighted average, the amount spend on medical costs due to WNV is US\$ 13247 ([*source:Table 2 and 4*](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3322011/#R5))

Patients who contracted the severe form of WNV missed about 50 days of workday on average, according to the same study from California in 2005 This translates to about US\\$ 14777 per case in 2021 value. Mild cases resulted in economic loss of US\\$ 1218 per case. Once again we take the weight average which is US\$ 5042 ([*source:Table 3 and 4*](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3322011/#R5))

The cost of contracting WNV per case per year is US$ 18289
The cost of contracting WNV per year is US$ 1207074
The average WNV damages for 1 individual infected (average)against cost of prevention in a week is 1.46

Option 1
Based on our prediction model, the mosquitoes management team can plan the spray strategy for the upcoming mosquito season on a weekly basis. 

For example, using the weather data and mosquito count of PIPIENS/RESTUANS this week to predict Wnv positive trap area for the following week. 

Option2
## Option 2
Using the prediction, spray can be conducted in all areas predicted to have at least 1 Wnv positive mosquito.

Using the prediciton model and the community areas as currently being used by Chicago, spray can be conducted when at least 2 traps in the same community are predicted to have Wnv positive in the following week.

|      |   |
|------|---|
| **Pros** | Reduce Wnv positive mosquitos in area of high risk while saving cost of spraying  |
| **Cons** | Singular traps with only 1 Wnv positive mosquito will be missed out despite potential risk|


For example, 9 traps should be sprayed in the plot above. In 10 week, there are a total 41 traps in the same community with more than 1 positive cases.

Option 3
2 of the top importance features in the random forest classification model uses Dist_0, Dist_1 to predict the presence of Wnv positive trap. These 2 features are the distances from point 0 and point 1, which are the top 2 points with the most Wnv positive trap in the train datasets. Hence, it means that the closer the traps are to these 2 point, the higher the probability of getting infected
  
Therefore, the spraying plan can be conducted within 5km radius of these 2 points to contain the most high risk Wnv positive Mosquitos from spreading to the rest of Chicago.
  
|      |   |
|------|---|
| **Pros** | Cost-effective method that only target high risk Wnv positive area based on train datasets  |
| **Cons** | Assume that most Wnv positive mosquitos came from these 2 areas while missing out other areas|
  
Option 4  
  
Release genetically modified mosquitos that prevent mosquito eggs from hatching after mating with existing mosquito. This eliminate the need for long term spraying plan, providing a long term solution with an one time R&D investment cost. Further information of such method can be obtained by contacting the National Environmental Agency of Singapore, which spent SGD 5 million (USD $ 3.6 million) to build a mosquito breeding facility in 2019. [Source](https://www.channelnewsasia.com/news/singapore/wolbachia-mosquitoes-new-facility-aedes-aegypti-dengue-12145012)
  
Summary
  
|      |   |
|------|---|
| **Pros** |Long term solution that can address future moquito problems, which are bound to worsen due to global warming  |
| **Cons** |Require a significant R&D investment cost & time to implement|

|        | Option 1                                                                           | Option 2                                                                                   | Option 3                                                                                      | Option 4                                                                                                     |
|--------|------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Method** | Spray all Wnv Positive Areas                                                       | Spray based on community areas                                                             | Spray based on distance from 2 key points                                                    | Release genetically modified mosquitos                                                                       |
| **Pros**   | Wnv positive mosquito can be dramatically reduced, thereby reducing Wnv human case | Reduce Wnv positive mosquitos in area of high risk while saving cost of spraying           | Cost\-effective method that only target high risk Wnv positive area based on train datasets   | Long term solution that can address future mosquito problems, which are bound to worsen due to global warming |
| **Cons**   | Spraying all positive Wnv areas can be very costly                                 | Singular traps with only 1 Wnv positive mosquito will be missed out despite potential risk | Assume that most Wnv positive mosquitos came from these 2 areas while missing out other areas | Require a significant R&D investment cost & time to implement                                                |
| **Cost** | \$416,658 | \$$1,220,213 | \$1,056 |  \$3,599,880|


Based all the 10 weeks plot of spraying & Wnv positive trap of Chicago in 2013, we can conclude that spraying does have a positive effect on controlling Wnv human cases. However, as the spray strategy seems to be based on current week's trap data, the spraying areas are always lag by 1 week and made the spraying effort sometimes useless. 

Our random forest classification model is able to predict the presence of Wnv positive in each mosquito trap, with an accuracy of (score). Using the classification model, we can predict next week's Wnv presence based on this week's data and plan the spraying strategy with the 4 options given above. 

More information would be required to make the model more accurate at predicting, such as 

1) Number of mosquito in test dataset

2) Number of Wnv human cases and area of infection

3) More spray area data other than 2011 and 2013

Nevertheless, we conclude that our random forest classificaion model has performed up to expectation in predicting Wnv presence in Chicago. 
  
 
