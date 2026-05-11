This is a competent project and I think you delivered something of value in the end.  I think what I'm missing here is the evaluation piece - you've given me an anecdotal evaluation, but I'm not seeing a more rigorous analysis.  More generally, I feel like you probably had the time and capacity to go a little deeper here.  For instance, you might have sought to predict the rank of each player within position class, or predict wAV percentile bucket, or predict career trajectory (based on NFL data post draft).

Depth of analysis aside, specific weaknesses (in no particular order):

- Missing baselines - it's really hard to tell how good your results are
- Unclear / underspecified train / test methodology
- Dividing wAV by seasons negates the importance of a long career
- Uncertain why you're using PCA?  Would have loved to seen Catboost on raw vs. Catboost on PCA
- You spent a lot of time with the GMM - what happened to it in the final analysis?
- Feature importance analysis appears to be missing?  Hard to imagine how this would work with PCA based features anyway...

So, all in all, it's a solid project, but I think you could have pushed things a little further than you did.

Team Score: 27/30


---

## Final Project Grade
| Assessment Item | Nathan Backman | Chris Marfisi | Hunter Geise | Dylan Stefali | Brett Cerenzio |
|---|---|---|---|---|---|
| **Proposal (5 pts)** | 5 | 5 | 5 | 5 | 5 |
| **Midterm Report (10 pts)** | 10 | 10 | 10 | 10 | 10 |
| **Final Presentation (5 pts)** | 5 | 5 | 5 | 5 | 5 |
| **Final Report (30 pts)** | 27 | 27 | 27 | 27 | 27 |
| **Weekly Updates (30 pts)** | 25 | 25 | 30 | 22 | 30 |
| **Total (80 pts)** | **72** | **72** | **77** | **69** | **77** |
