# NFL Draft Board: A Comprehensive Evaluation of What Makes Collegiate Football Players Successful in the NFL

### Team
natekbackman (POC), ChrisMarfisi, HunterGeise, DylanStafeil1, bjcerenz

### Introduction

The three-day NFL Draft is the one of the most critical days of the calendar year for NFL franchises because players selected can set up a team’s future for years to come or set them back for a long time. Many comparisons and eye-tests are used by front-offices and scouts to pick “their guy” in the draft, but every process has its flaws. In this project, we are predicting NFL career success of skill players (quarterbacks, running backs, wide receivers, and tight ends) in the upcoming draft by using collegiate data and former drafted players as reference points. In this new approach, we are using machine learning on the collegiate data to create a score that values player success, then run a clustering model to compare players in the draft class and previously drafted players. We find these two models as the most optimal for this problem because they are better at separating hype around players, letting the numbers do the talking. Our stakeholders in this project will be NFL front-offices and coaches, as well as any media outlets that make NFL Draft predictions. In the case of the front-offices and coaches, a successful project will help improve scouting departments and simplify draft-day decisions due to having an algorithm that shows which skill players can have the best careers. For media outlets, this impacts any analyst or personality that shares their mock drafts as the season comes to a close. This project would help solidify who the top players are, reducing noise in which players A and B will have better careers than players C and D. 

### Literature Review

Projecting the impact of amateur players in a professional setting has been a common idea addressed within the world of sport analytics over the last few years. The insights that result from these projects are generally seen as incredibly valuable for front office executives, coaches, and scouts alike, as it helps to provide a more efficient means of assessment on future draft prospects and can cut down significantly on time spent watching film.

Kitman Labs (2025) released work in which they outline two different models trained for each offensive skill position player in the NFL draft; one to predict the likelihood of a player being drafted in the first round, and one to predict whether a player will succeed in the NFL over multiple seasons. The goal in training both of these models was to highlight the gaps between metrics that are generally seen as indicators of success (driving the first model) versus metrics that are actually indicators of success (driving the second model) by using a combination of collegiate stats and draft combine results. The definition of “success” in the NFL, however, was not explicitly stated.[^1]

Czasonis et al. (2025) developed a metric called “Relevance-based Prediction” (RBP) for NBA draft prospects. This metric aimed to use historical information from previous draft prospects and their subsequent career trajectory in order to align with the information of current draft prospects as a means for forecasting the potential trajectory of their career. While this methodology was applied to NBA draft prospects, we felt the approach could be reproducible in the context of NFL draft grades.[^2]

A public GitHub project (Hauck 2023) outlined a methodology for projecting prospect success, defined as a metric called “Adjusted Approximate Value” (AAV) which is a stat meant to be an all-encompassing quantification of a player’s value towards their team’s success. This approach utilizes various data sources, from collegiate stats to public scouting grades for quarterbacks and wide receivers.[^3]

With these works as a foundation for our project, we aim to improve upon in them in the following ways:

- (Kitman Labs 2025) did not clearly define what “success” meant for a given player. We will be utilizing a metric called “Weighted Approximate Value” (similar to Hauck).
- (Hauck 2023) only looked at quarterbacks and wide receivers. We would like to extend this analysis to running backs as well.
- (Hauck 2023) utilized public scouting grades. While this information is generally provided by people who are well-versed in the field of prospect analysis, they all have their own biases which in turn can influence how favorable or unfavorable a given prospect’s grade may be. These biases can stem from the physical build of a prospect, preferred play-style by the scout, or even a lack of film viewed on that particular prospect.

### Data

We will utilize data from the [collegefootballdata.com](https://collegefootballdata.com/exporter/draft/picks) database & the [nflreadpy](https://github.com/nflverse/nflreadpy) package in Python. The collegefootballdata.com database which collects season level college football data going back to 2014 as well as draft information on each player. It collects advanced metrics such as average & total Predicted Points Added, which evaluates total number of points a player added to their offense, Usage Rate, which evaluates how often the player is utilized in the offense, & other basic box score statistics such as Passing Yards, Rushing Yards, TDs, etc. Variables are included in a glossary on the College Football Data webpage, and data is updated on a consistent basis to ensure up-to-date, accurate information. Nflreadpy will allow me to scrape draft data with player performance in the NFL, graded as [Weighted Approximate Value](https://www.pro-football-reference.com/about/approximate_value.htm), a measure created by pro-football-reference to evaluate & compare player performance across different positions with a single number. The ultimate goal is to join this draft data onto college football data’s draft data based on year, name, position, & pick number, which will then allow us to join on player id for the usage & predicted points added tables. Currently, a merged dataframe of usage and predicted points added statistics has over 27,000 rows & roughly 30 columns after filtering for D1 players. 

### Methods

Our aim is to build a regression machine learning model that predicts a player’s Weighted Approximate Value based on college stats, predicted points added, usage rate, position, conference, & other basic statistics. Conference & position variables will require us to transform them into dummy variables so that the data can be transformed into a matrix format. Similarly, we will add a dummy variable for power 4 conferences, as these conferences are considered to be the very best in all of college football and as a result, have the best players in college football. This will allow the model to favor these players in their predictions as the lower values within these conferences could be due to going up against better competition rather than being worse to someone from a weaker conference. Another thing that we’ll need to do is scale the continuous features in our model. Our features are going to be on different scales, especially if we mix rate stats with season stats, so it’s important that we scale them so the model doesn’t favor one over the other when the model is being built out. Another avenue we want to explore is creating player similarity scores for players in the upcoming draft through a clustering process. This would help evaluators get a better idea of each player’s archetype and how that archetype may or may not fit their offensive system. We will use root mean squared error to evaluate our model’s accuracy, ensuring that our model provides us with accurate estimates that we can rely on in the future. 

### Project Plan

| Period | Activity | Milestone |
|---|---|---|
| 2/2–2/16 | Collect college football data from collegefootballdata.com <br/> Collect NFL data from profootballreference <br/> Collect combine data (?) <br/> Collect Draft data (?) | Get all data collection done. |
| 2/16–3/2 | Preprocessing. Merging and cleaning data. | Have final dataset done by end of period, and start building out models. |
| 3/2–3/16 | Start building out both XGBoost model for player score and clustering model for player comparisons. | Have the basic framework for models done and put ourselves into position to be able to start testing models next period. |
| 3/16–3/30 | Test and improve on models. | Finalize the algorithm and all the parameters for the models. |
| 3/30–4/13 | Finalize models and predictions, and begin data analysis. | Finish running models, get final predictions, analyze data. |
| 4/13–4/27 | Write final report and create presentation. | Finish the project report, present our findings. |


### Risks
A first possible risk or difficulty could be missing identifiers or name inconsistencies across datasets, reducing the amount of data. To fight this problem, we'll use multiply join keys as to mitigate the possibility of this running rampant. Longer careers could have an innate bias as they'll have more data, so including position and draft position will account for the natural inequities across these positions. Overfitting could be a problem, but through techniques like cross validation or regularization, we're hoping this will also be limited. The historical relationships from previous draft classes could not apply to current draft classes, schemes, or positional value as the league changes regularly, so our outputs will be framed as probablities of success or value instead of absolute values. Lastly, something like weighted approximate value could be an oversimplification of a player's success or value, so its impact will be tested and evaluated in combination with many other predictors to add nuance and clarity. 

##### Footnotes

[^1]: Kitman Labs. “Predicting NFL Draft Success Using Machine Learning.” 2025.

[^2]: Czasonis, N., et al. “Relevance-Based Prediction for NBA Draft Prospects.” 2025.

[^3]: Hauck, J. “Projecting NFL Prospect Success Using Adjusted Approximate Value.” GitHub repository, 2023.
