- Does your proposal include all of the above mentioned sections? 1/1
- Are your objectives concrete and do you have a clear stakeholder need? 2/2
- Do you have a good data source and have you done a thorough job investigating its provenance and credibility? 1/1
- Did you do a thorough job exploring your data 2/2

Beautiful job here.  PCA is indeed showing some fairly distinct patterns of variation - it would be good to look at dimensional loading to see what the derived axes reflect; this is something that is meaningful with PCA but not with UMAP.  Also worth coloring different features of data to see how specific features correlate with variance in feature space.  Presumably, some measure of success here?  Or draft picks?  Using color will really help you make sense of your data.

- Have you done some initial modeling of your problem and do you have some early baseline results? 3/3

Nice work.  As I think you figured out, the elbow plot is really not useful at all. Also - I wouldn't use HAC given the shape of your data.  As you suggest, GMM is probably a better fit, not because the data uses percentages, but because that seems to be what shape the clusters are in 3D space.

- Do you have a clear path forward 1/1

You guys are doing a great job here.  Note that the results you saw with catboost (and presumably with XGBoost) are typical - these models often do well with the center of the distribution, but have a harder time with extreme values.  There are ways to correct for that in the loss function.  It is also possible that WAV actually clusters out into distinct distributions that can be derived via clustering.  If you find that there are clear differences in mean / median WAV across clusters, you can consider training separate models for different clusters, and then your overall process is cluster assignment -> select classifier -> predict.  That can be a useful step, esp. if some categories of players are inherently easier to predict.

If you need additional compute, let me know.


Score: 10/10

