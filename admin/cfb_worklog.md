## 2026-04-06 - Test Out GMM Fit (Nathan)

**Context: Wanted to attempt cluster analysis using Guassian Mixture Modeling. Because a lot of our data is represented in probabilities, it made sense to attempt this model type to see if it would result in a better fit than the previous clustering attempts.**

**Work Completed:**

- Ran the GMM on the QB position for multiple different clusters.

**Impact:** Results did not yield any significant findings. Cluster evaluation wound up being very similar to previous clustering attempts.

**Next Steps:** Very likely that we will omit clusters from the final model.


## 2026-04-06 - Test Out New Models & Objective Functions (Brett)

**Context: Wanted to try different models w/ different distributions & objective functions to account for the right-tailed skew that's present with the data. Seems to have worked out fairly well as the model became more aggressive at predicting outliers and was more accurate**

**Work Completed:**

- Tried out an NGBoost model which models the distribution and estimates not only a point estimate but also a prediction distribution, so we can estimate their different percentile outcomes. I also utilized a Tweedie & Gamma distribution on my Catboost & XGBoost models which helped the model predict outliers more confidently.

**Impact:** Provided me with the model architecture I want to continue with as we finalize the model. NGBoost with a LogNormal Distribution (Only loss function NGBoost has builtin) or Catboost/XGBoost with a Tweedie/Gamma Distribution.

**Next Steps:** Perform Hyperparameter tuning on the models and pick the best one. If the best model is Catboost & XGBoost, utilize Instance-Based Uncertainty Estimation (IBUG) to get their entire distribution of possibilities.


## 2026-03-23 - Discuss Further Work to be Done (Team)

**Context: Met to talk about what else is needed to be completed**


**Work Completed:**

- Lined up what needs to be done at specific due dates

**Impact:** Nearing completion of project

**Next Steps:** Complete steps outlined in meeting


## 2026-03-05 - Complete Checkpoint Update (Team)

**Context: Create Checkpoint ipynb for Professor Introne to see our progress**


**Work Completed:**

- Showed distribution of data through bar plots and nulls in columns (Hunter)
- Pre-processed data using PCA (Chris)
- Modeled data using Ward's Linkage HAC and CATBoost models (Brett and Nathan)
- Discussed problems and challenges in our work as well as next steps to completing the project

**Impact:** Gives a framework of what has been done and what is needed to be done for the project to be completed

**Next Steps:** Apply Professor Introne's feedback, fine-tune any issues we see with the models


## 2026-03-01 - Baseline Model (Brett)

**Context: Created initial pipeline and model code for project**


**Work Completed:**

- Wrote script that allows us to select X variables and create proper pipeline to run a cross validation model utilizing numerous Machine Learning algorithms such as Catboost, RandomForest, & XGBoost

**Impact:** Gets initial code in so we can focus on variable selection for model input

**Next Steps:** Choose adequate X variables, perform dimensionality reduction, add code for hyperparameter tuning.


## 2026-02-22 - Intro Data Exploration (Hunter)

**Context: Collected summary statistics and made basic plots to get early understanding of data**


**Work Completed:**

- Wrote scripts to collect summary statistics. Created barplots, histograms, and scatterplots to get early understanding of distribution of players by position, conference, team, and touchdown tendencies (Hunter)

**Impact:** Have a basic idea of data distribution, may lead to data aggregation

**Next Steps:** Continuing futher data exploration

## 2026-02-08 - Data Merging (Dylan)

**Context: Merged multiple data sets from the CollegeFootballData & nflreadpy api to have one master data set**


**Work Completed:**

- Wrote scripts to merge data using python packages to collect necessary college & nfl data for our analysis. (Dylan)

**Impact:** Data is now all together, allowing us to begin data exploration.

**Next Steps:** Begin exploratory analysis.


## 2026-02-08 - Data Collected (Team)

**Context: Collect Data from the CollegeFootballData & nflreadpy api to get all the information we need to conduct our analysis.**


**Work Completed:**

- Wrote scripts to scrape websites using python packages to collect necessary college & nfl data for our analysis. (Team)
- Created cfb_worklog.md and cfb_workplan.md files (Hunter)

**Impact:** Initial data is collected which will allow us to officially begin to explore the data.

**Next Steps:** Continue to work on final joins and begin exploratory analysis.


## 2026-02-02 - Proposal Completion (Team)

**Context**: Have proposal done to get feedback from Professor Introne. 

**Work Completed**:
- (Hunter) Wrote Introduction section.
- (Nathan) Wrote Literature Review section.
- (Brett) Wrote Data and Methods section.
- (Dylan) Wrote Project Plan section.
- (Chris) Wrote Risks section

**Impact**: Sets early framework to complete project.

**Next Steps**: Begin analysis.

---

## 2026-02-01 - Project Kickoff (Team)

**Context**: First team meeting to talk about the project.

**Work Completed**:
- (Team) Discussed idea of predicting NFL career success of skill position players.
- (Team) Designated roles for who should work on which part of the proposal

**Impact**: Set ideas into motion. 

**Next Steps**: Complete proposal. Get early idea of data.

---
