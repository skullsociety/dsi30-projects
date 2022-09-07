# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: Standardized Test Analysis
problem statement
intro
methods took
findings
recommendations

### Introduction
The ACT (American College Testing) test is a American standardize test administered by an non-profit organisation of the same name, ACT. It is used as a quality test of college applicants required for college admission process. The applicants portfolio would need to include ACT or SAT scores along with other materials to be considered for acceptance to the university.([*source*](https://www.act.org/))

The ACT consist of four sections : English, Mathematics, Reading, and Science, with an additional optional writing section ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html)). 

Scores for individual sections are scaled within range of 1 to 36. 1 for low score and 36 for a high score. Composite score would be calculated by the average of all section test scores, rounded to the nearest whole number. ([*source*](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html))

While ACT popularity as a standardized test have been increasing since 1940, ([*source*](https://www.minotdailynews.com/news/local-news/2017/04/a-brief-history-of-the-sat-and-act/)) there have been a increased supporters of these test, having a view that these tests are not a good measure to determine college admittance as these tests are not adequate to determine the ability.

### Problem Statement

The declining popularity of a standardized test is worrying as without it, colleges have nearly no means to differentiate a applicant's suitability with others especially if the course have a limited intake and there is overwhelming number of applicants for it. It would be unfair and unjust to rob the opportunity of the applicant because there is no common assessment and evaluate to quantify and qualify applicant's potential and ability with the others. 

While there is some states that have been using the ACT as a gold standard to measure the quality of their college applicants' quality. It is observed that there is a general decline of participating rates in many states in the US. We need to better address the ACT purpose and it's ability to allow college to accept, teach and develop potential applicants to express their ability to bring forth the American prowess to the world.

We need to promote and encourage the use of ACT as the standardized test in US states to allow colleges to find their right candidates from the pool of applicants. 


### Datasets


* [`act_2017.csv`](./data/act_2017.csv): 2017 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2018.csv`](./data/act_2018.csv): 2018 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2019.csv`](./data/act_2019.csv): 2019 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))


### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**state**|*object*|ACT_2017 ACT_2018 ACT_2019|All the states in the United States| 
|**participation17**|*float*|ACT_2017|The percent of participation rate of ACT examination for year 2017(units percent to zero decimal places 0.92 means 92%)|
|**participation18**|*float*|ACT_2018|The percent of participation rate of ACT examination for year 2018(units percent to zero decimal places 0.92 means 92%)|
|**participation19**|*float*|ACT_2019|The percent of participation rate of ACT examination for year 2019(units percent to zero decimal places 0.92 means 92%)|
|**composite17**|*float*|ACT_2017 |ACT score is out of 36, 5.12 means 5.12/36 Units is rounded off to one decimal place|
|**composite18**|*float*|ACT_2018|ACT score is out of 36, 5.12 means 5.12/36 Units is rounded off to one decimal place|
|**composite19**|*float*|ACT_2019|ACT score is out of 36, 5.12 means 5.12/36 Units is rounded off to one decimal place|


### Summary of analysis

It was found that the total number of participatition of ACT in the whole of US is decreasing over the years. There is 32 states shows the decreased participation, 4 states that shows an increase participation and 14 states that have no significant change in the ACT. The composite scores of these years are consistant, similar trend across the years. There is a positive correlation between participation rates across the years. This means that a state with high participation rate is more likely to have high participation rates the following year, vice versa. There is also a positive correlation between composite results across the years. This means that the test results from the following years are close to the following years. The test administered is consistant to the previous years to result in similar scores of participants each year. It was found that there was a drastic change in participation rate for states Colorado (1 to 0.27), Illinois (0.93 to 0.35) have dropped drastically. Potential states to invest resources to increase participation rates includes Hawaii (0.9 to 0.8), Kansas (0.73 to 0.72), Minnesota (1 to 0.95), Missouri (1 to 0.82), South dakota (0.8 to 0.75), South carolina (1 to 0.78) and North dakota (0.98 to 0.96).

Due to policy changes in Colorado that made standardized tests to be optional ([source](https://www.9news.com/article/news/education/act-sat-optional-colorado/73-74236f34-2c62-4461-87ce-4736412bd4a1) which subsequently led to removal of standardized test requirements for college ([source](https://www.npr.org/2021/05/27/1000868262/colorado-becomes-first-state-to-ban-legacy-college-admissions), Colorado participation rates have dropped drastically.
Illinois favors the SAT test which made ACT less popular.([source](https://chicago.chalkbeat.org/2018/7/27/21105418/illinois-has-embraced-the-sat-and-the-act-is-mad-about-it)) which subsequently led to a policy to make standardized test optional. ([source](https://www.washingtonexaminer.com/politics/standardized-tests-no-longer-required-for-illinois-public-college-admissions))

### Conclusions and recommendations
As there is a positive correlation between participation rate of past years to recent years, it is recommended to invest our limited resources into states that have high but not 100% participation rate in attempt to push it upwards to 100%. We could focus on states like Hawaii, Kansas, Minnesota, Missouri, South Dakota, South Carolina and North Dakota.
