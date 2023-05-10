# Attack wins you games, defence wins you titles. A Moneyball approach to assess the importance of defenders in football. 

The aim of this research is to examine whether there is supporting evidence for the importance of defensive players in football compared to offensive ones, and then assess if the salary market efficiently rewards their performances. 
To win a game, not conceding a goal is as important as scoring one. Nonetheless, there is a well-established tradition in football in which forwards tend to be valued much more than defenders, as witnessed by the high transfer fees paid for them in the modern era. 

To address the goal of the study, we attempt to measure player performance by using the VAEP (Valuing Actions by Estimating Probabilities) framework.
Finally, we present a comparison between the most impactful defenders and forwards in the 5 major European football leagues according to our model, along with an overview of the efficiency of players playing in these two positions.

# Data
We utilize data about salaries and matches of the top 5 European football leagues for the 2017/2018 season, as well as matches of Euro 2016 and the 2018 World Cup. 
Specifically, the leagues are: 
* Serie A (Italy)
* Premier League (England)
* La Liga (Spain)
* Bundesliga (Germany)
* Ligue 1 (France)
* UEFA Euro 2016 (International)
* FIFA World Cup 2018 (International)


Information regarding player salaries has been scraped from ([Capology](https://www.capology.com/)).

# Methodology

The main assumption of VAEP is that all actions in football are performed to increase the probabilities of scoring a goal or decrease the chance of conceding one. Therefore it values an action by estimating the change in these probabilities. These estimates are computed after each action, thus assigning an individual contribution to each player. In this regard, actions are represented through Atomic-SPADL (Soccer Player Action Description Language), which describes each of them as a set of features. Then probabilities are estimated by a classification model trained on past matches. Several models were trained, but Catboost was preferred due to  his faster training time and ability to deal with categorical features.

# Experimental Choiches
To proceed with the main idea of the thesis, the first step involved checking whether there was a significant difference in the salaries between forwards and defenders. The hypothesis was tested using a t-test, in which $H_0$, the null, stated that the true difference between the means of these groups was zero.

Given the limited resources available to us, only salary and match data from 2017/18 were used for the analysis. Euro 2016 and World Cup 2018 were included just in the training phase of the models since data on previous seasons of each league were not available. Training on a sub-sample of the current season instead, would have significantly affected the analysis. Indeed, by excluding part of the games played, the overall contribution of many players during the season would have changed dramatically, depending on the games included in the training/test set. These design choices were made in order to ensure the correctness of the analysis during the whole season.

Of the 115 matches from Euro 2016 and World Cup 2018, 70\% were used to train the models, while the remaining 30\% were used as a test set to evaluate the performances. The model performing the best was then retrained on all 115 matches before being applied to unseen matches from the five leagues. 

Lastly, in order to guarantee the robustness of the analysis, only players who played at least half of the available games were considered in the final analysis (19 out of 38 matches, i.e 1.710 minutes). Otherwise, footballers playing just a few games but with great performances would have inflated statistics compared to players who were more consistent throughout the season.

# Results

### Best defenders and forwards in the Premier League
|     | Player          | Position | Team          | VAEP rating |
| --- | ----------------| -------- | --------------| ----------- |
| 1   | P. Van Aanholt  | Defender | Crystal Palace| 0.5978      |
| 2   | L. Koscielny    | Defender | Arsenal       | 0.4349      |
| 3   | N. Monreal      | Defender | Arsenal       | 0.4159      |
| 4   | M. Alonso       | Defender | Chelsea       | 0.3933      |
| 5   | D. Janmaat      | Defender | Watford       | 0.3687      |

|     | Player      | Position | Team        | VAEP rating |
| --- | ------------| -------- | ----------- | ----------- |
| 1   | M. Salah    | Forward  | Liverpool   | 1.1180      |
| 2   | S. Agüero   | Forward  | Man. City   | 1.1020      |
| 3   | H. Kane     | Forward  | Tottenham   | 0.9054      |
| 4   | G. Jesus    | Forward  | Man. City   | 0.905392    |
| 5   | A. Martial  | Forward  | Man. United | 0.8526      |

### Summary over all leagues
| League         | VAEP   | Salary (€)   | VAEP/Salary*   | VAEP   | Salary (€)   | VAEP/Salary*   |
| -------------- | -------| ------------ | -------------- | -------| ------------ | -------------- |
| Serie A        | 6.3391 | 1,841,762    | 0.0718         | 14.0764| 3,285,049    | 0.0871         |
| Premier League | 6.7597 | 3,336,689    | 0.0264         | 16.2445| 5,650,612    | 0.0406         |
| La Liga        | 5.6745 | 2,879,158    | 0.0532         | 16.4826| 7,452,931    | 0.0573         |
| Bundesliga     | 6.1524 | 2,074,290    | 0.0470         | 12.9721| 2,889,929    | 0.0826         |
| Ligue 1        | 5.9692 | 1,274,269    | 0.1115         | 13.8945| 3,161,683    | 0.1347         |

*VAEP/Salary is computed as a measure of efficiency and multiplied by 10^4.

Strikers are the most cost-effective option for clubs in all leagues.


### Possible line-up for Premier League.

|     | Player         | Age | Position   | Team         | VAEP rating | VAEP   | Salary in €   | VAEP/Salary |
| --- | -------------- | --- | -----------| ------------ | ----------- |--------| --------------| ----------- |
| 1   | M. Ryan        | 25  | Goalkeeper | Brighton     | 0.7411      | 29.8076| 2,074,799     | 0.1437      |
| 2   | J. Kenny       | 20  | Defender   | Everton      | 0.2898      | 5.4768 | 889,199       | 0.0616      |
| 3   | A. Mawson      | 23  | Defender   | Swansea      | 0.2656      | 10.7233| 1,481,999     | 0.0724      |
| 4   | F. Hadergjonaj | 22  | Defender   | Huddersfield | 0.2393      | 4.7596 | 792,299       | 0.0601      |
| 5   | D. Rice        | 18  | Defender   | West Ham     | 0.2155      | 3.7769 | 59,279        | 0.6371      |
| 6   | A. Iwobi       | 21  | Midfielder | Arsenal      | 0.5434      | 11.6414| 1,778,399     | 0.0655      |
| 7   | R. Fraser      | 23  | Midfielder | Bournemouth  | 0.4380      | 10.3649| 1,600,559     | 0.0648      |
| 8   | A. Doucouré    | 24  | Midfielder | Watford      | 0.4113      | 16.3592| 1,185,600     | 0.1380      |
| 9   | C. Wilson      | 25  | Forward    | Bournemouth  | 0.5368      | 12.5856| 1,778,399     | 0.0708      |
| 10  | M. Rashford    | 19  | Forward    | Man. United  | 0.5042      | 10.8618| 1,185,600     | 0.0916      |
| 11  | A. Barnes      | 27  | Forward    | Burnley      | 0.4635      | 11.9323| 1,481,999     | 0.0805      |

# Conclusion

We first acknowledge that, on average, forwards are paid significantly more  than defenders. We also observe that the former is the most impactful player category in each league, and, despite higher salaries, they represent a more cost-effective option for clubs. According to these results, it might seem reasonable to conclude that strikers do actually contribute more than defenders to the overall economy of a game, suggesting that their higher salaries are justified.

However, even though in our research we adopted the most recent methodologies on the topic, there are still some underlying issues that may affect the reliability of these results.
Indeed, the model has a clear and strong bias toward forwards, at the expense of other footballers.
* Match event data is heavily focused on on-the-ball actions. Offensive actions are more straightforward to evaluate while most of the defensive ones, e.g. pressing, happen off-the-ball. Thus, the former dominates the latter in the computation of a player's VAEP, leading to higher ratings for offensive players.
* Secondly, due to the low-scoring nature of football and the high impact on the final result, goals and assists are highly rewarded by the model. Tackles and interceptions, on the contrary, happen more frequently without a direct effect on the scoreline.
* Lastly, the best defenders usually play in the top teams, where they tend to have possession of the ball and lead the game. They are much less engaged in the defensive phase compared to lower-ranking teams' players.

Therefore, given the current state of the art of football data, it is unfair to compare players across different roles. We acknowledge that results across roles are not reliable, but, by comparing players within a role and relating performance to salary, the model can provide useful indications. Indeed, for each league, it is able to build a competitive lineup on a low budget and to discover many footballers who have become key players in the years following the season taken into consideration.

This research contributes to literature review and the current state of football analytics by emphasizing the need for more comprehensive data collection that capture a wider range of in-game actions.
# References
Pappalardo, Luca; Massucco, Emanuele (2019): Soccer match event dataset. figshare. Collection. https://doi.org/10.6084/m9.figshare.c.4415000

Pappalardo, L., Cintia, P., Rossi, A. et al. A public data set of spatio-temporal match events in soccer competitions. Sci Data 6, 236 (2019). https://doi.org/10.1038/s41597-019-0247-7

Data source: publicly available on https://figshare.com/collections/Soccer_match_event_dataset/4415000/2

Tom Decroos, Lotte Bransen, Jan Van Haaren, and Jesse Davis. Actions speak louder than goals: Valuing player actions in soccer. In Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, pp. 1851-1861. 2019. ([Pdf](https://dl.acm.org/doi/10.1145/3292500.3330758))


Maaike Van Roy, Pieter Robberechts, Tom Decroos, and Jesse Davis. Valuing on-the-ball actions in soccer: a critical comparison of XT and VAEP. In Proceedings of the AAAI-20 Workshop on Artifical Intelligence in Team Sports. AI in Team Sports Organising Committee, 2020.([Pdf](https://kuleuven.limo.libis.be/discovery/search?query=any,contains,lirias2913207&tab=LIRIAS&search_scope=lirias_profile&vid=32KUL_KUL:Lirias&foolmefull=1))

