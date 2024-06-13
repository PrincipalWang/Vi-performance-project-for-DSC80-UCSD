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
| league   | ban1    | ban2    | ban3         | ban4    | ban5      | pick1      | pick2   | pick3     | pick4        | pick5   |   result |   firstblood |   dragons |   firstherald |   firsttower |   firstbaron |   Vi-banned |   Vi-picked |
|:---------|:--------|:--------|:-------------|:--------|:----------|:-----------|:--------|:----------|:-------------|:--------|---------:|-------------:|----------:|--------------:|-------------:|-------------:|------------:|------------:|
| LPL      | Senna   | Orianna | Gangplank    | Azir    | Swain     | Gwen       | Wukong  | Aphelios  | Renata Glasc | Vex     |        0 |            0 |         1 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Nidalee | Kindred | Lucian       | LeBlanc | Lissandra | Kalista    | Viego   | Jayce     | Ahri         | Rell    |        1 |            1 |         4 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Nidalee | Kindred | Ahri         | Jax     | Galio     | Senna      | Viego   | Seraphine | Zoe          | Kayle   |        0 |            0 |         1 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Gwen    | Lucian  | Gnar         | Azir    | Swain     | Tahm Kench | Wukong  | Ezreal    | Taliyah      | Riven   |        1 |            1 |         4 |           nan |          nan |          nan |           0 |           0 |
| LPL      | Senna   | Gwen    | Renata Glasc | Rakan   | Rell      | Wukong     | Draven  | Nautilus  | Swain        | Gnar    |        0 |            0 |         3 |           nan |          nan |          nan |           0 |           0 |
## This is lck local matches.<br>
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