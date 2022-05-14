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

```HTML
<head><meta charset="utf-8" /></head>
<body>
    <div>            <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-AMS-MML_SVG"></script><script type="text/javascript">if (window.MathJax) {MathJax.Hub.Config({SVG: {font: "STIX-Web"}});}</script>                <script type="text/javascript">window.PlotlyConfig = {MathJaxConfig: 'local'};</script>
        <script src="https://cdn.plot.ly/plotly-2.8.3.min.js"></script>                <div id="0cbc29b0-e6b9-4a48-8381-ab44114bb89e" class="plotly-graph-div" style="height:525px; width:100%;"></div>            <script type="text/javascript">                                    window.PLOTLYENV=window.PLOTLYENV || {};                                    if (document.getElementById("0cbc29b0-e6b9-4a48-8381-ab44114bb89e")) {                    Plotly.newPlot(                        "0cbc29b0-e6b9-4a48-8381-ab44114bb89e",                        [{"cells":{"align":["left"],"fill":{"color":[["white","lightgreen","white","lightgreen","white","lightgreen","white","lightgreen","white","lightgreen","white","lightgreen"]]},"font":{"color":"darkslategray","size":11},"line":{"color":"darkslategray"},"values":[["Country","Code","Year","Foreign Aid","GDP","GDP Growth","Foreign Aid %"],["Nominal","Nominal","Interval","Ratio","Ratio","Ratio","Ratio"],["No","No","No","Yes","Yes","Yes","Yes"],["Indicates country by name","Indicates the country by a unique code","Indicates the year that the data is collected from","The amount of foreign aid that a country recieved that year. This foreign aid is specifically the money that is given or lent to a country by another country.","GDP is the total monetary or market value of all the finished goods and services produced within in the borders of a country.","The GDP (Growth Domestic Product) per capita growth as an annual percentage. Per capita means the GDP is divided by the midyear population of the country.","The amount of foreign aid a country recieved in a year as a percentage of the country's gdp."]]},"columnorder":[1,2,3,4],"columnwidth":[70,50,50,350],"header":{"align":["left"],"fill":{"color":"green"},"font":{"color":"white","size":11},"line":{"color":"darkslategray"},"values":["<b>Attribute</b>","<b>Type</b>","<b>Nullable</b>","<b>Description</b>"]},"type":"table"}],                        {"template":{"data":{"bar":[{"error_x":{"color":"#2a3f5f"},"error_y":{"color":"#2a3f5f"},"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"bar"}],"barpolar":[{"marker":{"line":{"color":"#E5ECF6","width":0.5},"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"barpolar"}],"carpet":[{"aaxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"baxis":{"endlinecolor":"#2a3f5f","gridcolor":"white","linecolor":"white","minorgridcolor":"white","startlinecolor":"#2a3f5f"},"type":"carpet"}],"choropleth":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"choropleth"}],"contour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"contour"}],"contourcarpet":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"contourcarpet"}],"heatmap":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmap"}],"heatmapgl":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"heatmapgl"}],"histogram":[{"marker":{"pattern":{"fillmode":"overlay","size":10,"solidity":0.2}},"type":"histogram"}],"histogram2d":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2d"}],"histogram2dcontour":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"histogram2dcontour"}],"mesh3d":[{"colorbar":{"outlinewidth":0,"ticks":""},"type":"mesh3d"}],"parcoords":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"parcoords"}],"pie":[{"automargin":true,"type":"pie"}],"scatter":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter"}],"scatter3d":[{"line":{"colorbar":{"outlinewidth":0,"ticks":""}},"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatter3d"}],"scattercarpet":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattercarpet"}],"scattergeo":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergeo"}],"scattergl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattergl"}],"scattermapbox":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scattermapbox"}],"scatterpolar":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolar"}],"scatterpolargl":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterpolargl"}],"scatterternary":[{"marker":{"colorbar":{"outlinewidth":0,"ticks":""}},"type":"scatterternary"}],"surface":[{"colorbar":{"outlinewidth":0,"ticks":""},"colorscale":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"type":"surface"}],"table":[{"cells":{"fill":{"color":"#EBF0F8"},"line":{"color":"white"}},"header":{"fill":{"color":"#C8D4E3"},"line":{"color":"white"}},"type":"table"}]},"layout":{"annotationdefaults":{"arrowcolor":"#2a3f5f","arrowhead":0,"arrowwidth":1},"autotypenumbers":"strict","coloraxis":{"colorbar":{"outlinewidth":0,"ticks":""}},"colorscale":{"diverging":[[0,"#8e0152"],[0.1,"#c51b7d"],[0.2,"#de77ae"],[0.3,"#f1b6da"],[0.4,"#fde0ef"],[0.5,"#f7f7f7"],[0.6,"#e6f5d0"],[0.7,"#b8e186"],[0.8,"#7fbc41"],[0.9,"#4d9221"],[1,"#276419"]],"sequential":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]],"sequentialminus":[[0.0,"#0d0887"],[0.1111111111111111,"#46039f"],[0.2222222222222222,"#7201a8"],[0.3333333333333333,"#9c179e"],[0.4444444444444444,"#bd3786"],[0.5555555555555556,"#d8576b"],[0.6666666666666666,"#ed7953"],[0.7777777777777778,"#fb9f3a"],[0.8888888888888888,"#fdca26"],[1.0,"#f0f921"]]},"colorway":["#636efa","#EF553B","#00cc96","#ab63fa","#FFA15A","#19d3f3","#FF6692","#B6E880","#FF97FF","#FECB52"],"font":{"color":"#2a3f5f"},"geo":{"bgcolor":"white","lakecolor":"white","landcolor":"#E5ECF6","showlakes":true,"showland":true,"subunitcolor":"white"},"hoverlabel":{"align":"left"},"hovermode":"closest","mapbox":{"style":"light"},"paper_bgcolor":"white","plot_bgcolor":"#E5ECF6","polar":{"angularaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","radialaxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"scene":{"xaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"yaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"},"zaxis":{"backgroundcolor":"#E5ECF6","gridcolor":"white","gridwidth":2,"linecolor":"white","showbackground":true,"ticks":"","zerolinecolor":"white"}},"shapedefaults":{"line":{"color":"#2a3f5f"}},"ternary":{"aaxis":{"gridcolor":"white","linecolor":"white","ticks":""},"baxis":{"gridcolor":"white","linecolor":"white","ticks":""},"bgcolor":"#E5ECF6","caxis":{"gridcolor":"white","linecolor":"white","ticks":""}},"title":{"x":0.05},"xaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2},"yaxis":{"automargin":true,"gridcolor":"white","linecolor":"white","ticks":"","title":{"standoff":15},"zerolinecolor":"white","zerolinewidth":2}}}},                        {"responsive": true}                    ).then(function(){

var gd = document.getElementById('0cbc29b0-e6b9-4a48-8381-ab44114bb89e');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })                };                            </script>        </div>
</body>

```

```python
#@title World Wide Governance Indicators
import plotly.graph_objects as go

# colors of the rows
headerColor = 'blue'
rowEvenColor = 'lightblue'
rowOddColor = 'white'

# create a table figure
fig = go.Figure(data=[go.Table(
  # size and order of columns
  columnorder = [1,2,3,4],
  columnwidth = [60,50,50,350],

  # header contents and appearance
  header=dict(
    values=['<b>Attribute</b>','<b>Type</b>','<b>Nullable</b>','<b>Description</b>'],
    line_color='darkslategray',
    fill_color=headerColor,
    align=['left'],
    font=dict(color='white', size=11)
  ),

  # content and appearance of the cells in the table
  cells=dict(
    values=[
      ['Country','Code','Year','Accountability','Stability','Effectiveneess','Quality','RuleLaw','Corruption'],
      ['Nominal','Nominal','Interval','Interval','Interval','Interval','Interval','Interval','Interval'],
      ['No','No','No','Yes','Yes','Yes','Yes','Yes','Yes'],
      ['Indicates country by name',
       'Indicates the country by a unique code', 
       'Indicates the year that the data is collected from',
       'Estimate perception of the extent to which a country\'s citizens are able to participate in selecting their government, as well as freedom of expression, freedom of association, and a free media. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.',
       'Estimate Political Stability and Absence of Violence/Terrorism measures perceptions of the likelihood of political instability and/or politically-motivated violence, including terrorism. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.',
       'Estimate perceptions of the quality of public services, the quality of the civil service and the degree of its independence from political pressures, the quality of policy formulation and implementation, and the credibility of the government\'s commitment to such policies. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.',
       'Estimate perceptions of the ability of the government to formulate and implement sound policies and regulations that permit and promote private sector development. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.',
       'Estimate perceptions of the extent to which agents have confidence in and abide by the rules of society, and in particular the quality of contract enforcement, property rights, the police, and the courts, as well as the likelihood of crime and violence. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.',
       'Estimate perceptions of the extent to which public power is exercised for private gain, including both petty and grand forms of corruption, as well as "capture" of the state by elites and private interests. Ranges from approximately -2.5 (weak) to 2.5 (strong) governance performance.']],
    line_color='darkslategray',
    fill_color = [[rowOddColor,rowEvenColor,rowOddColor, rowEvenColor]*3],
    align = ['left'],
    font = dict(color = 'darkslategray', size = 11)
    ))
])

# display the table
fig.show()
```



