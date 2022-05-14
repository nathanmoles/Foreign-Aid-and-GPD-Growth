# Foreign-Aid-and-GPD-Growth

## Business Understanding

This project aims to assess the effectiveness of foreign aid in promoting growth, economic development, and prosperity. Investigating this question is important because despite the massive foreign aid flows from the west, developing countries remain extremely poor. By consolidating the knowledge from research done on this topic, it is possible to design a policy prescription that improves aid effectiveness.

For our project we decided to use per capita GDP growth as a measure of change in economic devevelopment. Other measure like total GDP can bias our results since they do not take into account the total population of the country. For example, nations with big population tend to have higher GDP levels but still suffer from poverty. On the other hand, per capita GDP shows the dollar amount of goods and services each citizen get on average. We acknowledge the fact that this is not a perfect measure. Least Develped Nations can have high inequality level; majority of the money is distributed among a small group of individuals with substantial political and financial power. We make a simplyfing assumption that countries don't suffere from high levels of inequality and the funds received as foreign aid are distributed approximately equally among the population.

There is a growing body of research showing that the effectiveness of aid in promoting prosperity depends on the quality of governance and proper allocation of funds between donors and recipients. Since the goal of our project is to assess the effectiveness of the way aid is distributed to developing countries, we will control for the quality of the governance in each country.

First, we will conduct exploratory data analysis to extract some non-obvious/actionable insights that aid distributing agencies can use in the future to improve the effectiveness of the aid. Finally, we will use a logistic regression to see if amount of foreign aid is a good predictor of the per capita GDP growth rate next year. We do not expect to get results implying that foreign aid does in fact promote economic prosperity in developing countries. We believe that the reasons why countries have low economic development levels are complex and just transfering funds to nations in not an effective method of solving those issues. Our project will contribute to the body of research trying to check the effectiveness of the steps taken by Western nations to combat hunger, underdevelopment, and economic destitution in poor countries.

## Data Understanding

**Data Information:**

All the datasets used in our analysis contain country level panel data. The data containing information about country's total GDP, per capita GDP growth rate, and the amount of foreign aid received each year comes from the World Bank's World Development Indicators dataset. The World Development Indicators is a compilation of relevant, high-quality, and internationally comparable statistics about global development and the fight against poverty. The database contains 1,400 time series indicators for 217 economies and more than 40 country groups, with data for many indicators going back more than 50 years. The data containing information about indices for different measure of quality of governance comes from the World Bank's Worldwide Governance Indicators project. WGI reports aggregate and individual governance indicators for over 200 countries and territories over the period 1996–2020, for six dimensions of governance: Voice and Accountability, Political Stability and Absence of Violence/Terrorism, Government Effectiveness,Regulatory Quality, Rule of Law, and Control of Corruption.

![newplot](https://user-images.githubusercontent.com/48035682/168406107-6fcadf9c-4c32-49fb-85a4-1a650157ebe2.png)
![newplot (2)](https://user-images.githubusercontent.com/48035682/168406827-227107d3-5892-447e-ba70-d205995de232.png)

![image](https://user-images.githubusercontent.com/48035682/168406910-7398f823-4cb8-4b0a-a955-ba1307080047.png)


