# Attack wins you games, defence wins you titles. A Moneyball approach to assess the importance of defenders in football. 
"Attack wins you games, defense wins you titles." is a famouse quote from Sir Alex Ferguson which emphasizes that having a strong attack is important, but having a solid defense is even more crucial to winning championships or achieving long-term success. 
The aim of this research is to examine whether there is supporting evidence for the importance of defensive players in football compared to offensive ones, and then assess if the salary market efficiently rewards their performances. To win a game, not conceding a goal is as important as scoring one. Nonetheless, there is a well-established tradition in football in which forwards tend to be valued much more than defenders, as witnessed by the high transfer fees paid for them in the modern era. Many great strikers have easily exceeded the 100 million euros threshold, with the record set by Neymar's transfer to Paris Saint-Germain for 222 million euros in 2017. Despite recent price increases, defenders are still far from these amounts. Virgil van Dijk's transfer to Liverpool in 2018 for 84.5 million euros was a record-breaking purchase for the category in recent years and yet much criticized by the media. 
To address the goal of the study, we attempt to measure player performance by using the VAEP (Valuing Actions by Estimating Probabilities) framework. Estimates of the probability of scoring and conceding a goal are computed after each action, thus assigning an individual contribution to each player. In this regard, actions are represented through Atomic-SPADL (Soccer Player Action Description Language), which describes each of them as a set of features. Then probabilities are estimated by a classification model trained on past matches.
Finally, we present a comparison between the most impactful defenders and forwards in the 5 major European football leagues according to our model, along with an overview of the efficiency of players playing in these two positions.

#Data
We utilize data about salaries and matches of the top 5 European football leagues for the 2017/2018 season, as well as matches of Euro 2016 and the 2018 World Cup. 
Specifically, the leagues are: 
    * Serie A (Italy)
    * Premier League (England)
    * La Liga (Spain)
    * Bundesliga (Germany)
    * Ligue 1 (France)
    * UEFA Euro 2016 (International)
    * FIFA World Cup 2018 (International)
Information regarding player salaries has been scraped from ( ([Capology](https://www.capology.com/))).


# References
Pappalardo, Luca; Massucco, Emanuele (2019): Soccer match event dataset. figshare. Collection. https://doi.org/10.6084/m9.figshare.c.4415000

Pappalardo, L., Cintia, P., Rossi, A. et al. A public data set of spatio-temporal match events in soccer competitions. Sci Data 6, 236 (2019). https://doi.org/10.1038/s41597-019-0247-7

Data source: publicly available on https://figshare.com/collections/Soccer_match_event_dataset/4415000/2

Tom Decroos, Lotte Bransen, Jan Van Haaren, and Jesse Davis. Actions speak louder than goals: Valuing player actions in soccer. In Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining, pp. 1851-1861. 2019. ([Pdf](https://dl.acm.org/doi/10.1145/3292500.3330758))


Maaike Van Roy, Pieter Robberechts, Tom Decroos, and Jesse Davis. Valuing on-the-ball actions in soccer: a critical comparison of XT and VAEP. In Proceedings of the AAAI-20 Workshop on Artifical Intelligence in Team Sports. AI in Team Sports Organising Committee, 2020.([Pdf](https://kuleuven.limo.libis.be/discovery/search?query=any,contains,lirias2913207&tab=LIRIAS&search_scope=lirias_profile&vid=32KUL_KUL:Lirias&foolmefull=1))

