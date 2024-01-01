### ADORBOE PRINCE KWASI PHILPS

> ID : 11218951
 
>Department: CPEN 
### __*Report on  red_wine.csv.*__<hr>
#### Analysing Fixed Acidity
```py
df['fixed acidity'].plot.hist(grid=True)
```
The above code snippet, draws a histogram of most acids involved with wine or fixed or nonvolatile (do not evaporate readily)

#### Analysing Volatile Acidity
```py
wine['volatile acidity'].plot.hist(grid=True)
```
The above code snippet draws a histogram of volatile acidity. The amount of acetic acid in wine, which at too high of levels can lead to an unpleasant, vinegar taste.As we can see the volatile acidity have values between 0.12 and 1.58

#### Analysing Citric Acidity
```py
df['citric acid'].plot.hist(grid=True)
```
The above code snippet draws a histogram of Citric Acidity. Citric Acid was found in small quantities, it can add 'freshness' and flavor to the red wines. From the graph, we see that the citric acid quantity ranges from 0 to 1.

#### Analysing residual sugar
```py
df['residual sugar'].plot.hist(grid=True)
```
The amount of sugar remaining after fermentation stops. Residual Sugar (or RS) is from natural grape sugars leftover in a wine after the alcoholic fermentation finishes. It's measured in grams per liter. It is rare to find wines with less than 1 gram/liter of RS.

#### Cholrides
```py
df['chlorides'].plot.hist(grid=True)
```
the amount of salt in the wine is what is recorded as Cholrides. The chlorides have values between 0.012 and 0.611.

#### Sulfur Dioxide
```py
df['free sulfur dioxide'].plot.hist(grid=True)
```
The free form of sulfur dioxide exists in equilibrium between molecular SO2 (as a dissolved gas) and bisulfite ion; It is an antioxidant and antimicrobial agent to help stabilize wine through its duration.  It's values ranges from Min value 1.0 to Max value 72.0
####  Density
```py
df['density'].plot.hist(grid=True)
```
.the dThe density of water is close to that of wine. Generally, wines with higher density may feel more full-bodied and viscous, while wines with lower density might feel lighter on the palate. However, the perception of density in wine is also influenced by other factors such as alcohol content, residual sugar, and tannins.
Ranges from 0.99007 to 1.00369.

#### pH
```py
df['pH'].plot.hist(grid=True)
```
The pH of wine is a fundamental parameter that influences its taste, stability, and winemaking processes. It is an essential consideration for both winemakers and wine enthusiasts when assessing and appreciating different wine styles.
The pH has values between 2.74 to 4.01. 

#### Analysing Sulphates
```py
df['sulphates'].plot.hist(grid=True)
```
The Histogram from this prompt, gives vital infor mation which  plays a crucial role in winemaking by helping to maintain the quality and stability of wine. While their use is common and generally considered safe. this graphs shows that sulpates fron the wines ranges from 0.33 to 2.0

#### Analysing Alcohol
```py
df['alcohol'].plot.hist(grid=True)
```
lcohol in wine is a key component that contributes to its body, texture, and overall sensory characteristics. It is formed through the fermentation process, during which yeast converts the natural sugars in grapes into alcohol. The alcohol content of wine is typically expressed as a percentage by volume, with most table wines falling within the range of 8.4% to 14.9%. Alcohol provides wines with a warming sensation, contributes to their mouthfeel, and plays a role in carrying and enhancing the flavors and aromas present in the wine. Additionally, the level of alcohol can influence the wine's aging potential and overall balance, with higher-alcohol wines often exhibiting greater richness and viscosity. However, excessive alcohol can overshadow the wine's other attributes and lead to an unbalanced or "hot" sensation. Winemakers carefully monitor and adjust the alcohol levels in their wines to achieve a desired style and ensure harmony with other elements such as acidity and tannins. 

#### A scatter plot of density against alcohol
```py
sns.scatterplot(x='density', y='alcohol', data=df)
``` 
A scatter plot of density against alcohol in wine provides a visual representation of the relationship between these two key components. Typically, as alcohol content increases, the density of the wine tends to decrease, resulting in a negatively sloped scatter plot. This relationship can offer insights into the wine's body and texture, with higher alcohol content wines generally displaying lower densities and potentially fuller bodies. Additionally, the scatter plot can aid in quality assessment, as unexpected patterns or outliers may indicate issues during fermentation or provide clues about the wine's composition and style.

#### A scatter plot of pH against Alcohol
```py
sns.scatterplot(x='pH', y='alcohol', data=df)
```
A scatter plot of pH against alcohol in wine provides a visual representation of the relationship between these two key parameters. Typically, as alcohol content increases, the pH level of the wine tends to decrease, resulting in a negatively sloped scatter plot. This relationship can offer insights into the wine's acidity, fermentation, and potential taste profile, as higher alcohol content wines may exhibit lower pH levels and therefore higher perceived acidity. The scatter plot can also assist winemakers in understanding the impact of alcohol on acidity levels and guide decisions related to fermentation techniques and style preferences. Additionally, it can be used for quality assessment, helping to identify any irregularities or unexpected patterns that may impact the overall composition and characteristics of the wine.

#### 
```PY
plt.figure(figsize=(10, 10))
sns.heatmap(df.corr(method='pearson'), annot=True, square=True)
plt.show()
```
 This code creates a heatmap to visualize the Pearson correlation coefficients between the columns of a pandas DataFrame df (that is the red_wine.csv file). The annot=True parameter adds the correlation values to the heatmap, while square=True ensures that each cell in the heatmap is square-shaped.This visualization is particularly useful for exploring the relationships and dependencies between different variables in the red_wine.csv file. The color intensity and the value annotated in each cell indicate the strength and direction of the correlation between the corresponding pair of variables. Positive values denote a positive correlation, negative values represent a negative correlation, and values closer to 0 indicate weaker or no correlation.

Overall, it  visually assesses the interdependence of variables in red_wine.csv, which can be valuable for understanding the data and making informed decisions in data analysis and modeling.

####
```py
df.corr().style.background_gradient(cmap="coolwarm")
```
This code applies a background gradient to the correlation matrix of the red_wine.csv df using the "coolwarm" color map. This styling technique enhances the visual representation of the correlation matrix by assigning different colors to different correlation values. The gradient helps to quickly identify the strength and direction of correlations between different variables in df.By using this method, we  gain insights into the relationships between the variables, as well as identify potential patterns or dependencies that may exist. This visual representation can be particularly useful for exploratory data analysis and for communicating the correlation structure of the wines to consumers.

#### Testing for quality
```py
df['quality'] = df['quality'].map({'bad' : 0, 'good' : 1})
df.head(10)
```
This is used to convert the categorical values in the 'quality' column of the red_wines df to numerical values. Specifically, it maps the string values 'bad' and 'good' to the numerical values 0 and 1, respectively, and assigns the results back to the 'quality' column.
Subsequently, df.head(10) displays the first 10 rows of the DataFrame df after the transformation. This allows you to verify that the mapping operation has been applied correctly and to inspect the updated 'quality' column to ensure that the categorical values have been converted to the corresponding numerical representation.

#### Quality showed in the DataFrame df using both a pie chart and a count plot.
```py
print(df['quality'].value_counts())
fig, ax = plt.subplots(ncols=2, nrows=1, figsize=(18, 5))
ax = ax.flatten()
df['quality'].value_counts().plot(x=0, y=1, kind='pie', figsize=(15,5), ax=ax[0])
sns.countplot(df['quality'], ax=ax[1])
plt.show()
```
The above code does the following:
1. Prints the count of each unique value in the 'quality' column of the DataFrame df, displaying the frequency of each numerical value after the categorical values 'bad' and 'good' have been mapped to 0 and 1, respectively.


2. Initializes a figure with two subplots arranged in a single row, with each subplot having specific dimensions defined by the figsize parameter.

3. Flattens the 2D array of axes into a 1D array, making it easier to iterate through the subplots.

4. Creates a pie chart in the first subplot to visually represent the distribution of the 'quality' column using the value_counts() method, displaying the proportion of each unique numerical value.

5. Generates a count plot in the second subplot using seaborn's countplot function to show the count of each unique value in the 'quality' column.

Overall, it displays the figure containing the two subplots, presenting the pie chart and the count plot side by side for visual comparison.


> From the very last plot ie the pie chart, it is observed that most of the wine are rated 0, ie bad and the few rest is considered good 1.










