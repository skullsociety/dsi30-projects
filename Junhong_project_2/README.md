
# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2: Ames Housing Data and Kaggle Challenge

# Introduction  
Property prices have been increasing steadily throughout the years despite the pandemic.([*source*](https://www.globalpropertyguide.com/North-America/United-States/Price-History)). Inflation and a positive returns on investment in property,
([*source*](https://leaddeveloper.com/why-property-values-increase/)), could be a major cause of this. ([*source*](https://www.bbc.com/news/business-57090421))
  
As there is no accurate model to predict price of a property, problems such as cause property taxation problems ([*source*](https://www.nytimes.com/2021/04/03/opinion/sunday/property-taxes-housing-assessment-inequality.html)) and real estate agents inflating of prices of properties to consumers ([*source*](https://www.unbiased.co.uk/news/mortgages/how-to-spot-estate-agents-tricks)) do arrise. This poorly reflect the real estate industry as a whole. 
  
It is also said that property prises are inflated at this point and very well may be another bubble that might brought economical losses to many people. ([*source*](https://fortune.com/2022/05/31/is-housing-market-bubble-which-markets-overvalued-home-prices/))  

# Problem Statement  
Property valuators does not know the true market value of their homes. This results in a unfair payment of property tax based on valuation of property as different valuators would valuate a property different.  
  
In this project, we would be making three supervised machine learning models; Linear Regression model, Ridge Regression model and Lasso regression model, using train data to test the model against the test data to predict the property sale price. Success of the model is determined by the Root Mean squared error (RMSE), which is the standard deviation of the residuals (prediction errors). Lower RMSE would determine a better model.  
The main objective of this model is to set a predicted valuation/price of a property in line with the market perceived value of the property, allowing valuators to set a fair price for the property and hence fair property taxes for everyone who would be paying property tax.  
  
# Datasets  
  
* [`test.csv`](./datasets/test.csv): Test data for model  
* [`train.csv`](./datasets/train.csv): Train data for model  
  
# Data Dictionary  
  
VARIABLE DESCRIPTIONS:  
Tab characters are used to separate variables in the data file. The data has 82 columns which include 23 nominal, 23 ordinal, 14 discrete, and 20 continuous variables (and 2 additional observation identifiers).  
  
Order (Discrete): Observation number  
  
PID (Nominal): Parcel identification number  - can be used with city web site for parcel review.   
  
       020	1-STORY 1946 & NEWER ALL STYLES  
       030	1-STORY 1945 & OLDER  
       040	1-STORY W/FINISHED ATTIC ALL AGES  
       045	1-1/2 STORY - UNFINISHED ALL AGES  
       050	1-1/2 STORY FINISHED ALL AGES  
       060	2-STORY 1946 & NEWER  
       070	2-STORY 1945 & OLDER  
       075	2-1/2 STORY ALL AGES  
       080	SPLIT OR MULTI-LEVEL  
       085	SPLIT FOYER  
       090	DUPLEX - ALL STYLES AND AGES  
       120	1-STORY PUD (Planned Unit Development) - 1946 & NEWER  
       150	1-1/2 STORY PUD - ALL AGES  
       160	2-STORY PUD - 1946 & NEWER  
       180	PUD - MULTILEVEL - INCL SPLIT LEV/FOYER  
       190	2 FAMILY CONVERSION - ALL STYLES AND AGES  
  
MS Zoning (Nominal): Identifies the general zoning classification of the sale.  
		  
       A	Agriculture  
       C	Commercial  
       FV	Floating Village Residential  
       I	Industrial  
       RH	Residential High Density  
       RL	Residential Low Density  
       RP	Residential Low Density Park  
       RM	Residential Medium Density  
	  
Lot Frontage (Continuous): Linear feet of street connected to property  
  
Lot Area (Continuous): Lot size in square feet    
  
Street (Nominal): Type of road access to property  
  
       Grvl	Gravel	  
       Pave	Paved  
       	  
Alley (Nominal): Type of alley access to property  
  
       Grvl	Gravel  
       Pave	Paved  
       NA 	No alley access  
		  
Lot Shape (Ordinal): General shape of property  
  
       Reg	Regular	  
       IR1	Slightly irregular  
       IR2	Moderately Irregular  
       IR3	Irregular  
  
Land Contour (Nominal): Flatness of the property  
  
       Lvl	Near Flat/Level	  
       Bnk	Banked - Quick and significant rise from street grade to building  
       HLS	Hillside - Significant slope from side to side  
       Low	Depression  
		  
Utilities (Ordinal): Type of utilities available  
		  
       AllPub	All public Utilities (E,G,W,& S)	  
       NoSewr	Electricity, Gas, and Water (Septic Tank)  
       NoSeWa	Electricity and Gas Only  
       ELO	Electricity only	  
	  
Lot Config (Nominal): Lot configuration  
  
       Inside	Inside lot  
       Corner	Corner lot  
       CulDSac	Cul-de-sac  
       FR2	Frontage on 2 sides of property  
       FR3	Frontage on 3 sides of property  
	  
Land Slope (Ordinal): Slope of property  
		  
       Gtl	Gentle slope  
       Mod	Moderate Slope	  
       Sev	Severe Slope  
	  
Neighborhood (Nominal): Physical locations within Ames city limits (map available)  
  
       Blmngtn	Bloomington Heights  
       Blueste	Bluestem  
       BrDale	Briardale  
       BrkSide	Brookside  
       ClearCr	Clear Creek  
       CollgCr	College Creek  
       Crawfor	Crawford  
       Edwards	Edwards  
       Gilbert	Gilbert  
       Greens	Greens  
       GrnHill	Green Hills  
       IDOTRR	Iowa DOT and Rail Road  
       Landmrk	Landmark  
       MeadowV	Meadow Village  
       Mitchel	Mitchell  
       Names	North Ames  
       NoRidge	Northridge  
       NPkVill	Northpark Villa  
       NridgHt	Northridge Heights  
       NWAmes	Northwest Ames  
       OldTown	Old Town  
       SWISU	South & West of Iowa State University  
       Sawyer	Sawyer  
       SawyerW	Sawyer West  
       Somerst	Somerset  
       StoneBr	Stone Brook  
       Timber	Timberland  
       Veenker	Veenker  
			  
Condition 1 (Nominal): Proximity to various conditions  
	  
       Artery	Adjacent to arterial street  
       Feedr	Adjacent to feeder street	  
       Norm	Normal	  
       RRNn	Within 200' of North-South Railroad  
       RRAn	Adjacent to North-South Railroad  
       PosN	Near positive off-site feature--park, greenbelt, etc.  
       PosA	Adjacent to postive off-site feature  
       RRNe	Within 200' of East-West Railroad  
       RRAe	Adjacent to East-West Railroad  
	  
Condition 2 (Nominal): Proximity to various conditions (if more than one is present)  
		  
       Artery	Adjacent to arterial street    
       Feedr	Adjacent to feeder street	  
       Norm	Normal	  
       RRNn	Within 200' of North-South Railroad  
       RRAn	Adjacent to North-South Railroad  
       PosN	Near positive off-site feature--park, greenbelt, etc.  
       PosA	Adjacent to postive off-site feature  
       RRNe	Within 200' of East-West Railroad  
       RRAe	Adjacent to East-West Railroad  
	  
Bldg Type (Nominal): Type of dwelling  
		  
       1Fam	Single-family Detached	  
       2FmCon	Two-family Conversion; originally built as one-family dwelling  
       Duplx	Duplex  
       TwnhsE	Townhouse End Unit  
       TwnhsI	Townhouse Inside Unit  
	  
House Style (Nominal): Style of dwelling  
	  
       1Story	One story  
       1.5Fin	One and one-half story: 2nd level finished  
       1.5Unf	One and one-half story: 2nd level unfinished  
       2Story	Two story  
       2.5Fin	Two and one-half story: 2nd level finished  
       2.5Unf	Two and one-half story: 2nd level unfinished  
       SFoyer	Split Foyer  
       SLvl	Split Level  
	  
Overall Qual (Ordinal): Rates the overall material and finish of the house  
  
       10	Very Excellent  
       9	Excellent  
       8	Very Good  
       7	Good  
       6	Above Average  
       5	Average  
       4	Below Average  
       3	Fair  
       2	Poor  
       1	Very Poor  
	  
Overall Cond (Ordinal): Rates the overall condition of the house  
  
       10	Very Excellent  
       9	Excellent  
       8	Very Good  
       7	Good  
       6	Above Average	  
       5	Average  
       4	Below Average	  
       3	Fair  
       2	Poor  
       1	Very Poor  
		  
Year Built (Discrete): Original construction date  
  
Year Remod/Add (Discrete): Remodel date (same as construction date if no remodeling or additions)  
  
Roof Style (Nominal): Type of roof  
  
       Flat	Flat  
       Gable	Gable  
       Gambrel	Gabrel (Barn)  
       Hip	Hip  
       Mansard	Mansard  
       Shed	Shed  
		  
Roof Matl (Nominal): Roof material  
  
       ClyTile	Clay or Tile  
       CompShg	Standard (Composite) Shingle  
       Membran	Membrane  
       Metal	Metal  
       Roll	Roll  
       Tar&Grv	Gravel & Tar  
       WdShake	Wood Shakes  
       WdShngl	Wood Shingles  
		  
Exterior 1st (Nominal): Exterior covering on house  
  
       AsbShng	Asbestos Shingles  
       AsphShn	Asphalt Shingles  
       BrkComm	Brick Common  
       BrkFace	Brick Face  
       CBlock	Cinder Block  
       CemntBd	Cement Board  
       HdBoard	Hard Board  
       ImStucc	Imitation Stucco  
       MetalSd	Metal Siding  
       Plywood	Plywood  
       PreCast	PreCast	  
       Stone	Stone  
       Stucco	Stucco  
       VinylSd	Vinyl Siding  
       Wd Sdng	Wood Siding  
       WdShing	Wood Shingles  
	  
Exterior 2nd (Nominal): Exterior covering on house (if more than one material)  
  
       AsbShng	Asbestos Shingles  
       AsphShn	Asphalt Shingles  
       BrkComm	Brick Common  
       BrkFace	Brick Face  
       CBlock	Cinder Block  
       CemntBd	Cement Board  
       HdBoard	Hard Board  
       ImStucc	Imitation Stucco  
       MetalSd	Metal Siding  
       Other	Other  
       Plywood	Plywood  
       PreCast	PreCast  
       Stone	Stone  
       Stucco	Stucco  
       VinylSd	Vinyl Siding  
       Wd Sdng	Wood Siding  
       WdShing	Wood Shingles  
	  
Mas Vnr Type (Nominal): Masonry veneer type  
  
       BrkCmn	Brick Common  
       BrkFace	Brick Face  
       CBlock	Cinder Block  
       None	None  
       Stone	Stone  
	  
Mas Vnr Area (Continuous): Masonry veneer area in square feet  
  
Exter Qual (Ordinal): Evaluates the quality of the material on the exterior  
		  
       Ex	Excellent  
       Gd	Good  
       TA	Average/Typical  
       Fa	Fair  
       Po	Poor  
		  
Exter Cond (Ordinal): Evaluates the present condition of the material on the exterior  
		  
       Ex	Excellent  
       Gd	Good  
       TA	Average/Typical  
       Fa	Fair  
       Po	Poor  
		  
Foundation (Nominal): Type of foundation  
		  
       BrkTil	Brick & Tile  
       CBlock	Cinder Block  
       PConc	Poured Contrete	  
       Slab	Slab  
       Stone	Stone  
       Wood	Wood  
		  
Bsmt Qual (Ordinal): Evaluates the height of the basement  

       Ex	Excellent (100+ inches)	  
       Gd	Good (90-99 inches)  
       TA	Typical (80-89 inches)  
       Fa	Fair (70-79 inches)  
       Po	Poor (<70 inches)  
       NA	No Basement  
		  
Bsmt Cond (Ordinal): Evaluates the general condition of the basement  
  
       Ex	Excellent  
       Gd	Good  
       TA	Typical - slight dampness allowed  
       Fa	Fair - dampness or some cracking or settling  
       Po	Poor - Severe cracking, settling, or wetness  
       NA	No Basement  
	  
Bsmt Exposure	(Ordinal): Refers to walkout or garden level walls  
  
       Gd	Good Exposure  
       Av	Average Exposure (split levels or foyers typically score average or above)	  
       Mn	Mimimum Exposure  
       No	No Exposure  
       NA	No Basement  
	  
BsmtFin Type 1	(Ordinal): Rating of basement finished area  
  
       GLQ	Good Living Quarters  
       ALQ	Average Living Quarters  
       BLQ	Below Average Living Quarters	  
       Rec	Average Rec Room  
       LwQ	Low Quality  
       Unf	Unfinshed  
       NA	No Basement  
		  
BsmtFin SF 1 (Continuous): Type 1 finished square feet  
  
BsmtFinType 2	(Ordinal): Rating of basement finished area (if multiple types)  
  
       GLQ	Good Living Quarters  
       ALQ	Average Living Quarters  
       BLQ	Below Average Living Quarters	  
       Rec	Average Rec Room  
       LwQ	Low Quality  
       Unf	Unfinshed  
       NA	No Basement  
  
BsmtFin SF 2 (Continuous): Type 2 finished square feet  
  
Bsmt Unf SF (Continuous): Unfinished square feet of basement area  
  
Total Bsmt SF (Continuous): Total square feet of basement area  
  
Heating	(Nominal): Type of heating  
		  
       Floor	Floor Furnace  
       GasA	Gas forced warm air furnace  
       GasW	Gas hot water or steam heat  
       Grav	Gravity furnace	  
       OthW	Hot water or steam heat other than gas  
       Wall	Wall furnace  
		  
HeatingQC (Ordinal): Heating quality and condition  
  
       Ex	Excellent  
       Gd	Good  
       TA	Average/Typical  
       Fa	Fair  
       Po	Poor  
		  
Central Air (Nominal): Central air conditioning  
  
       N	No  
       Y	Yes  
		  
Electrical (Ordinal): Electrical system  
  
       SBrkr	Standard Circuit Breakers & Romex  
       FuseA	Fuse Box over 60 AMP and all Romex wiring (Average)	  
       FuseF	60 AMP Fuse Box and mostly Romex wiring (Fair)  
       FuseP	60 AMP Fuse Box and mostly knob & tube wiring (poor)  
       Mix	Mixed  
		  
1st Flr SF (Continuous): First Floor square feet  
   
2nd Flr SF (Continuous)	: Second floor square feet  
  
Low Qual Fin SF (Continuous): Low quality finished square feet (all floors)  
  
Gr Liv Area (Continuous): Above grade (ground) living area square feet  
  
Bsmt Full Bath (Discrete): Basement full bathrooms  
  
Bsmt Half Bath (Discrete): Basement half bathrooms  
  
Full Bath (Discrete): Full bathrooms above grade  
  
Half Bath (Discrete): Half baths above grade  
  
Bedroom ABVGR (Discrete): Bedrooms above grade (does NOT include basement bedrooms)  
  
Kitchen ABVGR (Discrete): Kitchens above grade  
  
KitchenQual (Ordinal): Kitchen quality  
  
       Ex	Excellent  
       Gd	Good  
       TA	Typical/Average  
       Fa	Fair  
       Po	Poor  
       	  
TotRmsAbvGrd	(Discrete): Total rooms above grade (does not include bathrooms)  
  
Functional (Ordinal): Home functionality (Assume typical unless deductions are warranted)  
  
       Typ	Typical Functionality  
       Min1	Minor Deductions 1  
       Min2	Minor Deductions 2  
       Mod	Moderate Deductions  
       Maj1	Major Deductions 1  
       Maj2	Major Deductions 2  
       Sev	Severely Damaged  
       Sal	Salvage only  
		  
Fireplaces (Discrete): Number of fireplaces  
  
FireplaceQu (Ordinal): Fireplace quality  
  
       Ex	Excellent - Exceptional Masonry Fireplace  
       Gd	Good - Masonry Fireplace in main level  
       TA	Average - Prefabricated Fireplace in main living area or Masonry Fireplace in basement  
       Fa	Fair - Prefabricated Fireplace in basement  
       Po	Poor - Ben Franklin Stove  
       NA	No Fireplace  
		  
Garage Type (Nominal): Garage location  
		  
       2Types	More than one type of garage  
       Attchd	Attached to home  
       Basment	Basement Garage  
       BuiltIn	Built-In (Garage part of house - typically has room above garage)  
       CarPort	Car Port  
       Detchd	Detached from home  
       NA	No Garage  
		  
Garage Yr Blt (Discrete): Year garage was built  
		  
Garage Finish (Ordinal)	: Interior finish of the garage  
  
       Fin	Finished  
       RFn	Rough Finished	  
       Unf	Unfinished  
       NA	No Garage  
		  
Garage Cars (Discrete): Size of garage in car capacity  
  
Garage Area (Continuous): Size of garage in square feet  
  
Garage Qual (Ordinal): Garage quality  
  
       Ex	Excellent  
       Gd	Good  
       TA	Typical/Average  
       Fa	Fair  
       Po	Poor  
       NA	No Garage  
		  
Garage Cond (Ordinal): Garage condition  
  
       Ex	Excellent  
       Gd	Good  
       TA	Typical/Average  
       Fa	Fair  
       Po	Poor  
       NA	No Garage  
		  
Paved Drive (Ordinal): Paved driveway  
  
       Y	Paved  
       P	Partial Pavement  
       N	Dirt/Gravel  
		  
Wood Deck SF (Continuous): Wood deck area in square feet  
  
Open Porch SF (Continuous): Open porch area in square feet  
  
Enclosed Porch (Continuous): Enclosed porch area in square feet  
  
3-Ssn Porch (Continuous): Three season porch area in square feet  
  
Screen Porch (Continuous): Screen porch area in square feet  
  
Pool Area (Continuous): Pool area in square feet  
  
Pool QC (Ordinal): Pool quality  
		  
       Ex	Excellent  
       Gd	Good  
       TA	Average/Typical  
       Fa	Fair  
       NA	No Pool  
		  
Fence (Ordinal): Fence quality  
		  
       GdPrv	Good Privacy  
       MnPrv	Minimum Privacy  
       GdWo	Good Wood  
       MnWw	Minimum Wood/Wire  
       NA	No Fence  
	  
Misc Feature (Nominal): Miscellaneous feature not covered in other categories  
		  
       Elev	Elevator  
       Gar2	2nd Garage (if not described in garage section)  
       Othr	Other  
       Shed	Shed (over 100 SF)  
       TenC	Tennis Court  
       NA	None  
		  
Misc Val (Continuous): $Value of miscellaneous feature  
  
Mo Sold (Discrete): Month Sold (MM)  
  
Yr Sold (Discrete): Year Sold (YYYY)  
  
Sale Type (Nominal): Type of sale  
		  
       WD 	Warranty Deed - Conventional  
       CWD	Warranty Deed - Cash  
       VWD	Warranty Deed - VA Loan  
       New	Home just constructed and sold  
       COD	Court Officer Deed/Estate  
       Con	Contract 15% Down payment regular terms  
       ConLw	Contract Low Down payment and low interest  
       ConLI	Contract Low Interest  
       ConLD	Contract Low Down  
       Oth	Other  
		  
  
SalePrice (Continuous): Sale price $$  
  
# Summary of analysis  
  
|Model|R2 train/val|CrossValScoreTrain|SqMSE train/val|Alpha|
|---|---|---|---|---|
|**Linear**|0.91/0.89|26426|22092/26887||
|**Ridge**|0.91/0.89|26346|22252/26927|93.2|
|**Lasso**|0.91/0.89|24617|22092/26885|1|
  
<span style="background-color: #FFFF00">Definitions:  </span> 
1. Coefficients; the values that multiply the predictor values.  
2. Coefficient of Determination, R2; determines the proportion of variance in the dependent variable that can be explained by the independent variable  
3. Root Mean squared error; standard deviation of the residuals (prediction errors)  
4. Alpha; is the learning rate parameter which has to be set in a gradient descent to get the desired outcome from a machine learning model. Alpha is a set amount of change in the coefficients on each update  
  
<span style="background-color: #FFFF00">Summary:  </span>   
From data from train.csv file, we cleaned the data by removing the rows or replacing all the nan values with zeros. We numurized some feature values by replacing the values based on the ranking of values and combined with similar features to give a new feature value that would have higher relavanceand would hence give a better representation as feature to predict the Sales Price.    


|Model|Mean|Mode|Median|
|---|---|---|---|
|**Baseline**|181469|130000|162500|
|**Linear**|181123|138163|165215|
|**Ridge**|181123|142319|166031|
|**Lasso**|138213|138213|165213|

  
<span style="background-color: #FFFF00">Models:</span>   
There are three regression models constructe; Linear, Ridge and Lasso. Linear regression model as the name suggests, is a linear model. It is a model that assumes a linear relationship between the input feature (X) and the single output variable (y), allowing y to be calculated from a linear combination of the input variables (x). Ridge regression model and Lasso regression puts a similar constraint on the coefficients by introducing a penalty factor. However, while lasso regression takes the magnitude of the coefficients, ridge regression takes the square.  
  
Out of the three models constructed, we pick the Lasso model for prediction of the Sales Price in the test data set in the test.csv file.  
Based on the table above, we can see that while the coefficient of determination; R2 are identical, the root mean squared error differs. Lasso model have scored the lowest in the root Mean squared error cross-validation tests. This test splits the data used to train the model;training data, into multiple folds, and evaluates the model based on the partition of the data. The score across all partitions are being averaged to give the value in the table. As root mean squared error is the standard deviation of the residuals; prediction errors, we would want this value to be as low as possible. _Lasso_ model have got the lowest score in both cross validation and train/test split.  
  
Baseline is formed using the mean, mode and median of train set, sale price. all models have lower mean than the baseline, which means the models are performing better than the baseline. Lasso model have done considerability better compared to the linear and ridge model.  
  
<span style="background-color: #FFFF00">Limitations of the lasso model:</span>  
If the number of predictors is greater than the number of observations, Lasso will pick at most predictors as non-zero, even if all predictors are relevant (or may be used in the test set).  
If there are two or more highly collinear variables then LASSO regression select one of them randomly which is not good for the interpretation of data.  
As the data is limited and there is insufficient data for some feature's variables, we cannot properly determine the feature correlation to the Sale Price and hence resulting in it not used in this model. Without these features added, the model would not be able to accurately determine the Sales Price of the property should there be any correlation between the feature's variable to the Sales Price.  
We would need more data in such feature in order to include and enhance future models.  

# Conclusions and recommendations  
  
The coefficient for a feature represents the change in the mean response associated with a change in that term, while the other features in the model are held constant.([*source*](https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/regression/how-to/fit-regression-model/interpret-the-results/all-statistics-and-graphs/coefficients-table/)).The coefficient tells us how much the dependent variable which is 'Sale Price' in our case, is expected to increase when that independent variable/feature, holding all the other independent variables/features constant. ([*source*](https://dss.princeton.edu/online_help/analysis/interpreting_regression.htm)).  
Based on the model, you can see that the biggest positive change in predicted sale price is when 1st floor square feet, 2nd floor square feet is high. Followed by overall quality and condition, garage and basement feature attributes would affect the Sale Price positively.  

Features that would greatly impact the Sales Price negatively would be the age of property, type of garage, MS subclass 90 (DUPLEX - ALL STYLES AND AGES),120 (1-STORY PUD (Planned Unit Development) - 1946 & NEWER) and 160 (2-STORY PUD - 1946 & NEWER).  

With this model, we can accurately predict and determine the property value for a fairer accessment of the property value for taxation. More data could be collected to refine the features used in the model to improve the model in the future. 