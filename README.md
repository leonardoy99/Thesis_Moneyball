# Attack wins you games, defence wins you titles. A Moneyball approach to assess the importance of defenders in football. 

The aim of this research is to examine whether there is supporting evidence for the importance of defensive players in football compared to offensive ones, and then assess if the salary market efficiently rewards their performances. 
To win a game, not conceding a goal is as important as scoring one. Nonetheless, there is a well-established tradition in football in which forwards tend to be valued much more than defenders, as witnessed by the high transfer fees paid for them in the modern era. Many great strikers have easily exceeded the 100 million euros threshold, with the record set by Neymar's transfer to Paris Saint-Germain for 222 million euros in 2017. Despite recent price increases, defenders are still far from these amounts. Virgil van Dijk's transfer to Liverpool in 2018 for 84.5 million euros was a record-breaking purchase for the category in recent years and yet much criticized by the media. 

To address the goal of the study, we attempt to measure player performance by using the VAEP (Valuing Actions by Estimating Probabilities) framework. Estimates of the probability of scoring and conceding a goal are computed after each action, thus assigning an individual contribution to each player. In this regard, actions are represented through Atomic-SPADL (Soccer Player Action Description Language), which describes each of them as a set of features. Then probabilities are estimated by a classification model trained on past matches.
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

# Experimental Choiches
To proceed with the main idea of the thesis, the first step involved checking whether there was a significant difference in the salaries between forwards and defenders. The hypothesis was tested using a t-test, in which $H_0$, the null, stated that the true difference between the means of these groups was zero.

Given the limited resources available to us, only salary and match data from 2017/18 were used for the analysis. Euro 2016 and World Cup 2018 were included just in the training phase of the models since data on previous seasons of each league were not available. Training on a sub-sample of the current season instead, would have significantly affected the analysis. Indeed, by excluding part of the games played, the overall contribution of many players during the season would have changed dramatically, depending on the games included in the training/test set. These design choices were made in order to ensure the correctness of the analysis during the whole season.

Of the 115 matches from Euro 2016 and World Cup 2018, 70\% were used to train the models, while the remaining 30\% were used as a test set to evaluate the performances. The model performing the best was then retrained on all 115 matches before being applied to unseen matches from the five leagues. 

Lastly, in order to guarantee the robustness of the analysis, only players who played at least half of the available games were considered in the final analysis (19 out of 38 matches, i.e 1.710 minutes). Otherwise, footballers playing just a few games but with great performances would have inflated statistics compared to players who were more consistent throughout the season.


# References
Pappalardo, Luca; Massucco, Emanuele (2019): Soccer match event dataset. figshare. Collection. https://doi.org/10.6084/m9.figshare.c.4415000

Pappalardo, L., Cintia, P., Rossi, A. et al. A public data set of spatio-temporal match events in soccer competitions. Sci Data 6, 236 (2019). https://doi.org/10.1038/s41597-019-0247-7

Data source: publicly available on https://figshare.com/collections/Soccer_match_event_dataset/4415000/2

Tom Decroos, Lotte Bransen, Jan Van Haaren, and Jesse Davis. Actions speak louder than goals: Valuing player actions in soccer. In Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, pp. 1851-1861. 2019. ([Pdf](https://dl.acm.org/doi/10.1145/3292500.3330758))


Maaike Van Roy, Pieter Robberechts, Tom Decroos, and Jesse Davis. Valuing on-the-ball actions in soccer: a critical comparison of XT and VAEP. In Proceedings of the AAAI-20 Workshop on Artifical Intelligence in Team Sports. AI in Team Sports Organising Committee, 2020.([Pdf](https://kuleuven.limo.libis.be/discovery/search?query=any,contains,lirias2913207&tab=LIRIAS&search_scope=lirias_profile&vid=32KUL_KUL:Lirias&foolmefull=1))

