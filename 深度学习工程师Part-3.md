# Structuring Machine Learning Projects
## ML策略
1. orthogolization-1个参数对应1个功能
2. using **a single** evaluation metric
   * precision+ recall=F1 score
   * optimizing metric/ satisfying metric(threshold)
3. set up data sets
   * **dev/test must** comes from the same distribution
   * define a new evaluation metric
4. avoidable bias: training error- Bayesian/Human eror
   * human-level error:best error people can achieve< Bayesian
   * human-level error based on purpose
5. variance problem:dev error- training error
6. Guidelines
   * decrease Avoidable bias
      * train bigger model
      * train longer/better optimization algorithms
      * NN architecture/hyperparameters search
   * decrease variance
      * more data
      * regularization
      * NN architecture/hyperparameters search
7. Carrying out error analysis
   * look at dev examples to evaluate ideas 
   * clean up incorrectly labeled data
      * DL algorithms are quite robust to **random errors** in the **training set**
      * compare **overall dev set error** with **errors due to incorrect labels**/ **errors due to other causes**, then decide whether to fix error labels in dev set, especially when the overall dev set error >> difference between different models, and *errors due incorrect labels* take a large percent of dev set error 
8. Project guidline(做工程): Build your first system quickly, then iterate
9. Training and testing on different distributions
   * add *data from webpages* and *data from mobile app* together as the whole training set, dev/test set are randomly sampled from training set. Then dev set contains only a few target images, which is bad for evaluating wanted model. **Bad choice**
   * add *data from webpages* and **half** of *data from mobile app* together as the whole training set, dev/test set are all from *data from mobile app*. Now you're aiming the taregt where you want it to be.