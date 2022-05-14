# Testing The Effectiveness of Foreign Aid
##By Nathan Moles, Konstantine Jalagonia, Peter Maria, John Paci

## Business Understanding

This project aims to assess the effectiveness of foreign aid in promoting growth, economic development, and prosperity. Investigating this question is important because despite the massive foreign aid flows from the west, developing countries remain extremely poor. By consolidating the knowledge from research done on this topic, it is possible to design a policy prescription that improves aid effectiveness.

For our project we decided to use per capita GDP growth as a measure of change in economic devevelopment. Other measure like total GDP can bias our results since they do not take into account the total population of the country. For example, nations with big population tend to have higher GDP levels but still suffer from poverty. On the other hand, per capita GDP shows the dollar amount of goods and services each citizen get on average. We acknowledge the fact that this is not a perfect measure. Least Develped Nations can have high inequality level; majority of the money is distributed among a small group of individuals with substantial political and financial power. We make a simplyfing assumption that countries don't suffere from high levels of inequality and the funds received as foreign aid are distributed approximately equally among the population.

There is a growing body of research showing that the effectiveness of aid in promoting prosperity depends on the quality of governance and proper allocation of funds between donors and recipients. Since the goal of our project is to assess the effectiveness of the way aid is distributed to developing countries, we will control for the quality of the governance in each country.

First, we will conduct exploratory data analysis to extract some non-obvious/actionable insights that aid distributing agencies can use in the future to improve the effectiveness of the aid. Finally, we will use a logistic regression to see if amount of foreign aid is a good predictor of the per capita GDP growth rate next year. We do not expect to get results implying that foreign aid does in fact promote economic prosperity in developing countries. We believe that the reasons why countries have low economic development levels are complex and just transfering funds to nations in not an effective method of solving those issues. Our project will contribute to the body of research trying to check the effectiveness of the steps taken by Western nations to combat hunger, underdevelopment, and economic destitution in poor countries.


## Data Understanding

All the datasets used in our analysis contain country level panel data. The data containing information about country's total GDP, per capita GDP growth rate, and the amount of foreign aid received each year comes from the World Bank's World Development Indicators dataset. The World Development Indicators is a compilation of relevant, high-quality, and internationally comparable statistics about global development and the fight against poverty. The database contains 1,400 time series indicators for 217 economies and more than 40 country groups, with data for many indicators going back more than 50 years. The data containing information about indices for different measure of quality of governance comes from the World Bank's Worldwide Governance Indicators project. WGI reports aggregate and individual governance indicators for over 200 countries and territories over the period 1996–2020, for six dimensions of governance: Voice and Accountability, Political Stability and Absence of Violence/Terrorism, Government Effectiveness,Regulatory Quality, Rule of Law, and Control of Corruption.

![newplot](https://user-images.githubusercontent.com/48035682/168406107-6fcadf9c-4c32-49fb-85a4-1a650157ebe2.png)
![newplot (2)](https://user-images.githubusercontent.com/48035682/168406827-227107d3-5892-447e-ba70-d205995de232.png)

## Data Preparation
Before starting the data analysis we prepare and clean the datasets. We uploaded the World Bank data to the Github repository. Economic data gets updated on a regular basis and we want to make sure that the data will be compatable with our project.

We clean the World Bank's Development Indicators data. We drop the unnecessary variables also make sure that all variables are numeric to ensure the correctness of our analysis.

Macroeconomic theory argues that there is a one year lag between two related events. The foreign aid recieved in a particular year will not be distributed until the following period. To account for this we lag the foreign aid by one period.

We merge all datasets together on year and the country code. We drop the rows that contain at least one missing value. We make a copy of the created dataframe. We will use the copy of the data to avoid changing the intial dataset.

Our merged dataframe contains information about total GDP for each country and the lagged amount of foreign aid recieved. Since we want to check the effect of foreign aid on the economic performance, we believe that it will be relevant to calculate the foreign aid as a percent of GDP and use it as our main independent variable.


## Exploratory Data Analysis

### Variable Distribution
![image](https://user-images.githubusercontent.com/48035682/168407096-145ceddf-2436-4b25-8601-61de2438f741.png)

The distribution of per capita GDP growth rates does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is equal to zero implying that we can not assert the normality of the distribution. The minimum per capita GDP growth rate in our data is -62.37% and a maximum value is 121.79%, with a mean of 2.31% and median of 2.61%.

![image](https://user-images.githubusercontent.com/48035682/168407123-396ed37c-d93d-47c6-b354-2d9f42c8d087.png)

The distribution of the foreign aid recieved by countries does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is equal to zero implying that we can not assert the normality of the distribution. The minimum foreign aid recieved by a country is -9.97 * 10^8. The negative value of foreign aid means that the country is giving foreign aid to others. The maximum value is 2.56 * 10^8, with a mean of 5.77 * 10^8 and median of 2.54 * 10^8.

![image](https://user-images.githubusercontent.com/48035682/168407130-3d5c9158-e955-44d6-8c7a-553572f1e7f0.png)

The distribution of Voice and Accountability index does not seem to be normally distributed. The distribution is skewed to left. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum Voice and Accountability index in our data is -2.26 and a maximum value is 1.37, with a mean of -0.3 and median of -0.24.

![image](https://user-images.githubusercontent.com/48035682/168407133-9afa2564-f305-401d-bf68-8fac2deaac91.png)

The distribution of Political Stability and Absence of Violence index does not seem to be normally distributed. The distribution is skewed to left. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum value of Political Stability and Absence of Violence index in our data is -3.18 and a maximum value is 1.60, with a mean of -0.27 and median of -0.23.

![image](https://user-images.githubusercontent.com/48035682/168407147-64ca79cd-dc28-4249-9f9f-441ab6a433a4.png)

The distribution of the Government Effectiveness index does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum value of the Government Effectiveness index in our data is -2.44 and a maximum value is 2.20, with a mean of -0.39 and median of -0.46.

![image](https://user-images.githubusercontent.com/48035682/168407173-94164122-3f86-4b10-8294-cec23fbb9d0a.png)

The distribution of the Regulatory Quality index does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum Regulatory Quality index in our data is -2.62 and a maximum value is 2.23, with a mean of -0.37 and median of -0.39.

![image](https://user-images.githubusercontent.com/48035682/168407193-7195d3b2-f795-4674-8987-c4099456fe9e.png)

The distribution of the Rule of Law index does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum value of the Rule of Law index in our data is -2.35 and a maximum value is 1.70, with a mean of -0.40 and median of -0.47.

![image](https://user-images.githubusercontent.com/48035682/168407196-48df650a-868a-4460-a8b4-0b0223f1e6d5.png)

The distribution of the Control of Corruption index does not seem to be normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is close to zero implying that we can not assert the normality of the distribution. The minimum value of the Control of Corruption index in our data is -1.81 and a maximum value is 2.32, with a mean of -0.39 and median of -0.48.

![image](https://user-images.githubusercontent.com/48035682/168407208-6cdd5989-739b-41e7-a98e-c318ef7b7a6e.png)

The distribution of the Foreign Aid as a Percent of GDP is not normally distributed. We conduct the Shapiro-Wilk normality test to check the validity of our assumption. P-value is zero implying that we can not assert the normality of the distribution. The minimum value of the Foreign Aid as a Percent of GDP in our data is -1.25% and a maximum value is 144.84%, with a mean of 4.32% and median of 2.00%.

### World Maps
We create the world maps for each year based on the per capita GDP growth rate and the level of the foreign aid received. We want to check if some interesting patterns emerge in data over time. We also want to check our hypothesis that there is no relationship between foreign aid and economic performace.

![image](https://user-images.githubusercontent.com/48035682/168407371-90d87303-e66c-4701-a97d-85c47061fe30.png)
![image](https://user-images.githubusercontent.com/48035682/168407373-18432af6-2df1-4d2f-8b54-ee5771f9b715.png)
![image](https://user-images.githubusercontent.com/48035682/168407379-24c5159d-a032-4ba6-a777-f1a5d1392105.png)
![image](https://user-images.githubusercontent.com/48035682/168407388-c5a444a1-5cc0-4546-adc3-713ba4419b7f.png)
![image](https://user-images.githubusercontent.com/48035682/168407396-fdd85061-78ed-4b83-9a64-4a6f90247d7d.png)
![image](https://user-images.githubusercontent.com/48035682/168407404-3cc58ad4-03c0-4db6-8deb-abbd7d0ba8c4.png)

Based on the maps we see several interesting patters. First, countries that are foreign aid recipients in one year are almost always receiving aid in the folloing period as well. This implies that poor countries stay poor and there is no improvement in their economic performance. Second, countries economic performance in one period has an important effect on the following year. For example, China has had high economic growth level in each year. Lastly, the maps support our hypothesis that there is no clearly defined relationship between foreign aid and per capita GDP growth rate.

### Scatterplot
We create a scatterplot of per capita GDP growth rate and the foreign aid as a percent of total GDP. We also plot a line of best fit. This scatterplot supports our findings from the world map visualizations. There seems to be no relatinship between the two variables.

![image](https://user-images.githubusercontent.com/48035682/168407283-3c7a73b9-bc87-4f13-b8cd-4d0197bcfc62.png)

### Heatmap
Since economic research shows there might be a relationship between the effectiveness of the foreign aid and the quality of governance in the country we create a correlation heatmap to find the variables that should we control for when testing for the relationship between foreign aid level and the economic performance.

![image](https://user-images.githubusercontent.com/48035682/168407438-255e7413-8f67-42b2-98f3-d02449d6e3f8.png)
![image](https://user-images.githubusercontent.com/48035682/168407461-a827baf8-7e78-4b29-ab49-c63ee6b12dbb.png)

The heatmaps look different for each year which implies that there are other factors that affect the relationship between these variables. There is near zero correlation between Foreign Aid and per capita GDP growth rates in most of the years. However, the correlation is stronger between governance indicators and both foreign aid and the ecnomi performance. Countries with worse quality of governance tend to get higher foreign aid levels which makes intuitive sense since they are more likely to have high poverty levels. On the other hand, countries with high level of quality of governance have better economic performances.


## Modeling & Evaluation
To test the effectiveness of the foreign aid in promoting growth, economic development, and prosperity we use softmax logistic regression. We divide countries into three groups based on their level of per capita GDP growth rate. We check how good of a predictor our model is for the economic performance of each country. We use a vector of governance indicators as control variables to ensure that we control for differences in the quality of political and economic institutions. 

![image](https://user-images.githubusercontent.com/48035682/168407505-3a351436-50c1-46e1-9cc2-ddf8341ab1cf.png)
![image](https://user-images.githubusercontent.com/48035682/168407507-fa9c0c8b-22cc-40d1-8d88-b06d53cd2dc6.png)

Based on the cofusion matrix above we see that our model does not do a great job at classifying the countries based on the per capita GDP growth rate. Each entry in the normalized confusion matrix is close to 0.33. This result is in line with our expectations. As we hypothesised, foreign aid is not effectiveness at promoting growth, economic development, and prosperity.


## Deployment
The goal of our project was to assess the effectiveness of foreign aid in promoting growth, economic development, and prosperity. We used the data from World Bank about each country’s quality of governance, economic performance, and the amount of foreign aid received. Based on our analysis we can make several conclusions.

First, the quality of governance in the country has an important effect on the performance of the economy. More specifically on the per capita GDP growth rate. This is an important finding, since per capita GDP is flawed but still the best measure of quality of life in a country. We see that to improve the quality and livelihood of people it is crucial to improve the quality of governance, lower the corruption rate, strengthen the rule of law, and make country more democratic. Without strengthening political and economic institutions it will be impossible to promote economic prosperity in the least developed countries.

Second, our logistic regression showed that foreign aid received as a percent of total GDP is not a good predictor of economic growth in the next period. This is still true after controlling for quality of governance indicators. Thus, the ineffectiveness of the foreign aid is not only due to high corruption level or low government accountability. The ineffectiveness of foreign aid should stem from the way it is distributed or the sector of the economy that is targeted.

The previous discussion suggests that foreign aid fails to stimulate growth because of reasons related to both recipient and donors. LDCs tend to have low-quality governance and weak institutions, which leads to improper allocation of funds, rent-seeking activities and lowers the incentives to solve collective action problems. On the other hand, donors are reluctant to admit the failure and adjust the aid policy to address the issues. However, a better understanding of both the demand and supply side of the aid can help us design remedial policies. Foreign aid is highly ineffective in the current form, but development organizations can resolve the problem by changing the way the aid is distributed or by making the aid conditional on future reforms. This will ensure that the aid is correctly distributed and also improve the quality of governance in developing nations which is crucial factor for the long-term sustained economic growth and prosperity.

Moving forward, the future research could expand the scale of the data and include more features. It is possible to use other regression methods that could identify important patterns in the data and try to find factors that are cause of the foreign aid's ineffectiveness. Most importantly, future research could use more granular data that contains information about different types of foreign aid that was distributed to least developed countries and the economic sectors that were targeted. This could enable the researchers to find the optimal method of providing foreign aid that promotes economic activity, alleviates provetry, and improves the quality of life of the destitiute.

### Resources
## YouTube Video Links
- [Code Walk-Through on Youtube](https://youtu.be/-tQ_Oe77FNk)
- [Presentation](https://youtu.be/BYlvw7F4xEw)

## Data Sources
- [World Governance Indicators](http://info.worldbank.org/governance/wgi)
- [World Development Indicators](https://databank.worldbank.org/source/world-development-indicators

## IO Page
- [Github IO Page] https://molesnathan1.github.io/Foreign-Aid-and-GPD-Growth/

## Google Colab



