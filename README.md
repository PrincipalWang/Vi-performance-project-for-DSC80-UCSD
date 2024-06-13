# League of Legends Vi Performance Statistical Analysis
**Name**: Chen Wang
# Introduction
In my experience watching the lol matches, especially lpl matches in 2022, I remember one thing clearly: lpl teams like Vi in unexplained reasons in summer. Nearly every time Vi was picked, lpl teams performed very bad. In wlds, lpl teams also like to pick Vi and lose to the lck teams. I am curious about it.<br>
This analysis will mainly focus on one topic: Is lpl team more likely to pick Vi and win than lck teams?
# Data Cleaning and Exploratory Data Analysis
## Data Cleaning
To save time in the further data cleaning steps, I first only keep the relevant columns: league ban1 ban2 ban3 ban4 ban5 pick1 pick2 pick3 pick4 pick5 result firstblood dragons firstherald firsttower firstbaron. I decide to keep rows that is related to lpl and lck teams.<br>
Furthermore, among these columns, I find out that league ban1 ban2 ban3 ban4 ban5 pick1 pick2 pick3 pick4 pick5 columns show the preference of Vi and result firstblood dragons firstherald firsttower firstbaron columns show the in game performance.<br>
## This lpl local mathes.
| league   | ban1    | ban2    | ... | pick4        | pick5   |   result |   firstblood |   dragons |   firstherald |   firsttower |   firstbaron |   Vi-banned |   Vi-picked |
|:---------|:--------|:--------|:----|:-------------|:--------|---------:|-------------:|----------:|--------------:|-------------:|-------------:|------------:|------------:|
| LPL      | Senna   | Orianna | ... | Renata Glasc | Vex     |        0 |            0 |         1 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Nidalee | Kindred | ... | Ahri         | Rell    |        1 |            1 |         4 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Nidalee | Kindred | ... | Zoe          | Kayle   |        0 |            0 |         1 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Gwen    | Lucian  | ... | Taliyah      | Riven   |        1 |            1 |         4 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Senna   | Gwen    | ... | Swain        | Gnar    |        0 |            0 |         3 |           nan |          nan |          nan |           0 |           0 |
## This is lck local matches.
| league   | ban1         | ban2         | ban3      | ban4         | ban5         | pick1   | pick2   | pick3    | pick4    | pick5        |   result |   firstblood |   dragons |   firstherald |   firsttower |   firstbaron |   Vi-banned |   Vi-picked |
|:---------|:-------------|:-------------|:----------|:-------------|:-------------|:--------|:--------|:---------|:---------|:-------------|---------:|-------------:|----------:|--------------:|-------------:|-------------:|------------:|------------:|
| LCK      | Diana        | Lissandra    | Jax       | Karma        | Renata Glasc | Gwen    | Kai'Sa  | Ahri     | Nautilus | Trundle      |        1 |            0 |         4 |             1 |            1 |            1 |           1 |           0 |
| LCK      | Lucian       | Taliyah      | Kalista   | Vi           | Viego        | Ezreal  | Wukong  | Galio    | Kayle    | Alistar      |        0 |            1 |         2 |             0 |            0 |            0 |           1 |           0 |
| LCK      | Twisted Fate | Renata Glasc | Taliyah   | Nautilus     | Kayle        | Ezreal  | Viego   | Gnar     | Swain    | Rakan        |        1 |            1 |         4 |             0 |            0 |            0 |           0 |           0 |
| LCK      | Lucian       | Gwen         | Diana     | Lissandra    | Karma        | Wukong  | Kai'Sa  | Ahri     | Sejuani  | Gragas       |        0 |            0 |         2 |             1 |            1 |            1 |           0 |           0 |
| LCK      | Swain        | Diana        | Lissandra | Renata Glasc | Galio        | Gwen    | Kai'Sa  | Nautilus | Nocturne | Twisted Fate |        1 |            1 |         3 |             1 |            1 |            1 |           1 |           0 | \n
## This is lpl matches in wlds.
| league   | teamname            | ban1    | ban2     | ban3      | ban4   | ban5         | pick1   | pick2   | pick3   | pick4    | pick5    |   result |   firstblood |   dragons |   firstherald |   firsttower |   firstbaron |   Vi-banned |   Vi-picked | belong_league   |
|:---------|:--------------------|:--------|:---------|:----------|:-------|:-------------|:--------|:--------|:--------|:---------|:---------|---------:|-------------:|----------:|--------------:|-------------:|-------------:|------------:|------------:|:----------------|
| WLDs     | Royal Never Give Up | Kalista | Wukong   | Lucian    | Poppy  | Sejuani      | Yuumi   | Vi      | Sivir   | Taliyah  | Jax      |        1 |            1 |         3 |           nan |          nan |          nan |           0 |           1 | LPL             |
| WLDs     | EDward Gaming       | Fiora   | Nautilus | Aatrox    | Ahri   | Sylas        | Azir    | Zeri    | Lulu    | Renekton | Trundle  |        0 |            0 |         3 |           nan |          nan |          nan |           0 |           0 | LPL             |
| WLDs     | EDward Gaming       | Fiora   | Vi       | Poppy     | Braum  | Renata Glasc | Sejuani | Sylas   | Sivir   | Nautilus | Renekton |        0 |            1 |         2 |           nan |          nan |          nan |           1 |           0 | LPL             |
| WLDs     | Royal Never Give Up | Lucian  | Yuumi    | Azir      | Amumu  | Zilean       | Wukong  | Zeri    | Taliyah | Lulu     | Aatrox   |        1 |            0 |         3 |           nan |          nan |          nan |           1 |           0 | LPL             |
| WLDs     | EDward Gaming       | Poppy   | Fiora    | Lissandra | Aatrox | Renekton     | Vi      | Taliyah | Sivir   | Gragas   | Nautilus |        1 |            0 |         2 |           nan |          nan |          nan |           0 |           1 | LPL             |
## This is lck matches in wlds.
| league   | teamname   | ban1     | ban2    | ban3     | ban4   | ban5   | pick1   | pick2        | pick3   | pick4   | pick5   |   result |   firstblood |   dragons |   firstherald |   firsttower |   firstbaron |   Vi-banned |   Vi-picked | belong_league   |
|:---------|:-----------|:---------|:--------|:---------|:-------|:-------|:--------|:-------------|:--------|:--------|:--------|---------:|-------------:|----------:|--------------:|-------------:|-------------:|------------:|------------:|:----------------|
| WLDs     | DWG KIA    | Yuumi    | Azir    | Nautilus | Ornn   | Poppy  | Sejuani | Lucian       | Nami    | Swain   | Aatrox  |        1 |            1 |         4 |             1 |            1 |            0 |           0 |           0 | LCK             |
| WLDs     | DWG KIA    | Azir     | Yuumi   | Sivir    | Poppy  | Ornn   | Lucian  | Vi           | Nami    | Vex     | Yone    |        0 |            0 |         1 |             0 |            0 |            0 |           0 |           1 | LCK             |
| WLDs     | DWG KIA    | Yuumi    | Azir    | Aphelios | Akali  | Ahri   | Sivir   | Renata Glasc | Sylas   | Gwen    | Lee Sin |        1 |            1 |         4 |             1 |            1 |            1 |           0 |           0 | LCK             |
| WLDs     | DWG KIA    | Yuumi    | Azir    | Kalista  | Vi     | Poppy  | Sylas   | Nami         | Lucian  | Wukong  | Aatrox  |        1 |            0 |         3 |             0 |            1 |            1 |           1 |           0 | LCK             |
| WLDs     | DRX        | Renekton | Kalista | Ahri     | Amumu  | Lulu   | Yuumi   | Sylas        | Zeri    | Wukong  | Fiora   |        1 |            0 |         2 |             0 |            0 |            0 |           0 |           0 | LCK             |
## Analysis
We have a pie chart of Vi win rate in lpl.
<iframe
  src="assets/lpl_Vi_win_rate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This shows that the lpl Vi winning rate is nearly 1 to 1.  
  
We have a pie chart of Vi win rate in lck.
<iframe
  src="assets/lck_Vi_win_rate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This shows that the lck Vi winning rate is nearly 1 to 1.  
  
We have a pie chart of Vi win rate in lpl in wlds.
<iframe
  src="assets/wlds_lpl_Vi_win_rate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This shows that the lpl Vi in wlds winning rate is nearly 1 to 1.  
  
We have a pie chart of Vi win rate in lck in wlds.
<iframe
  src="assets/wlds_lck_Vi_win_rate.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
This shows that the lck Vi in wlds winning rate is nearly 1 to 1.  

# Assessment of Missingness
## NMAR Analysis
In my data, I believe the columns league, teamname, ban1, ban2, ban3, ban4, ban5, pick1, pick2, pick3, pick4, pick5, result are all Not Missing At Random. They seems that they do not have a trend of missing.<br>
Also, after checking, firstblood and dragons do not have missing, too.  <br>
For the firsttherald firsttower and firstbarron missing in LPL part I will sat it is Not Missing At Random since LPL does not put this data on the dataset.  
## Missingness Dependency
<iframe
  src="assets/Empirical Distribution of the Test Statistic (firstblood).html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
Observed Stat (firstblood): 0.0  <br>
P-value (firstblood): 0.533  <br>
Observed Stat (dragons): 0.1930716060049682  <br>
P-value (dragons): 0.013  <br>
Observed Stat (Vi-picked): 0.007247002916081657  <br>
P-value (Vi-picked): 0.357  <br>
Dependent Columns (p < 0.05): ['dragons']  <br>
Independent Columns (p >= 0.05): ['firstblood', 'Vi-picked']  <br>
The permutation tests reveal that the missingness of firsttherald significantly depends on the dragons column, with a p-value of 0.006, indicating a relationship between the two. However, the missingness of firsttherald does not significantly depend on the firstblood (p-value: 0.508) or Vi-picked (p-value: 0.398) columns, suggesting that any observed differences in these columns between rows with and without missing firsttherald values are likely due to random chance. Therefore, we can conclude that the occurrence of missing values in firsttherald is influenced by the number of dragons secured but not by whether the team got the first blood or whether Vi was picked.  

# Hypothesis Testing
## Null Hypothesis (H0):
H0: There is no difference in the likelihood of Vi winning a match between the LPL and LCK leagues.
## Alternative Hypothesis (H1)
H1: There is a difference in the likelihood of Vi winning a match between the LPL and LCK leagues.
## Test Statistic
The test statistic for this comparison is the two-proportion z-test.
## Significance Level
5%  
## Result
After the hypothesis test performed, with p-values of 0.078(local) and 0.424(wlds), I fail to reject the null hypothesis. There is no significant difference in Vi's win rates between LPL and LCK, no matter local matches or wld matches.  
# Framing a Prediction Problem
Can we predict if Vi will be picked or banned in a match based on in-game statistics and match metadata?
# Baseline Model
In the previous sections, I found out that win rate of Vi is not that different between lpl and lck. Then can we use the data of in game performace to judge if Vi is picked?  <br>
First, I only used firstblood and dragons. This shows the ganking ability.  <br>
Accuracy: 0.9206349206349206  <br>
Classification Report:  <br>
               precision    recall  f1-score   support  <br>
           0       0.92      1.00      0.96       232  <br>
           1       0.00      0.00      0.00        20  <br>
    accuracy                           0.92       252  <br>
   macro avg       0.46      0.50      0.48       252  <br>
weighted avg       0.85      0.92      0.88       252  <br>
After fitting the model, my accuracy score on the training data is 0.9206. This means that my model is able to correctly predict 92.06% of data. This accuracy score is really high.
# Final Model
In my final model, I added 3 more features: firstherald firsttower and firstbaron. These show the ability of map controlling.  <br>
Accuracy: 0.9032258064516129  <br>
Classification Report:  <br>
               precision    recall  f1-score   support  <br>
           0       0.90      1.00      0.95        28  <br>
           1       0.00      0.00      0.00         3  <br>
    accuracy                           0.90        31  <br>
   macro avg       0.45      0.50      0.47        31  <br>
weighted avg       0.82      0.90      0.86        31  <br>
The accuracy score is now 0.9032, meaning my model is able to correctly predict 90.32% of my data. Although the score goes down, mainly because the increasement of complexity of data, I still have a high F-1 score 0.95,meaning both of my precision and recall are close to 1.  
# Fairness Analysis
## Hypotheses
## Null Hypothesis (H0)
My model is fair. Its accuracy for matches where Vi is picked is the same as its accuracy for matches where Vi is not picked.
## Alternative Hypothesis (H1)
My model is unfair. Its accuracy for matches where Vi is picked is not the same as its accuracy for matches where Vi is not picked. 
## Groups
Group X: Games where Vi was picked. <br>
Group Y: Games where Vi was not picked.  
## Result
Overall Accuracy: 0.9206349206349206  <br>
Observed Accuracy Difference: -1.0  <br>
P-value: 1.0  
<iframe
  src="assets/Empirical Distribution of the Test Statistic (Accuracy Difference).html"
  width="800"
  height="600"
  frameborder="0"
></iframe>
After performing the permutation test, the result p-value I got is 1.0, which is larger than the 0.05 significance level. Consequently, I fail to reject the null hypothesis. This outcome implies that my model predicts Vi appearance according to the in-game performance value. Consequently, my model appears to be fair, exhibiting no discernible bias towards one group over the other based on the specified criteria.