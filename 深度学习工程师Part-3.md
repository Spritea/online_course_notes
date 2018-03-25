# Structuring Machine Learning Projects
## ML策略 One
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
## ML策略 Two
1. Carrying out error analysis
   * look at dev examples to evaluate ideas 
   * clean up incorrectly labeled data
      * DL algorithms are quite robust to **random errors** in the **training set**
      * compare **overall dev set error** with **errors due to incorrect labels**/ **errors due to other causes**, then decide whether to fix error labels in dev set, especially when the overall dev set error >> difference between different models, and *errors due incorrect labels* take a large percent of dev set error 
2. Project guidline(做工程): Build your first system quickly, then iterate
3. Training and testing on different distributions
   * add *data from webpages* and *data from mobile app* together as the whole training set, dev/test set are randomly sampled from training set. Then dev set contains only a few target images, which is bad for evaluating wanted model. **Bad choice**
   * add *data from webpages* and **half** of *data from mobile app* together as the whole training set, dev/test set are all from *data from mobile app*. Now you're aiming the taregt where you want it to be.
4. Bias and Variance with mismatched data distributions
   * build **Training-dev set**: same distribution as training set, but not used for training. Then train on the rest tarining set, to do error analysis, see the error on **the rest training set**, on the **training-dev set**, and **original dev set**.
   * training set error<< training-dev set error: **variance problem**
   * training set error is close to training-dev set error, but training-dev set error<< dev set error: **data mismatch problem**
   * training error, training-dev error and dev error are close, but training error>> human error: **bias problem**
   * difference between dev error and test error is large: **overfit to dev set**, need a bigger dev set
5. Addressing data mismatch
   * do manual error analysis to try to understand difference between training and dev/test sets
   * make training data more similar; or collect more data similar to dev/test sets: **artificial data synthesis**, may overfit to a small set
6. Transfer learning
   * pretrain on other big datasets, to learn low level features
   * retrain the last layer-finetune
   * when transfer learning makes sense
      * Task A and B have the same input x
      * You have a lot more data for Task A than Task B
      * Low level features from A could be helpful for learning B
7. Multitask learning
   * one image may have muitiple labels
   * when multi-task learning makes sense
      * Training on a set of tasks that could benefit from having shared lower-level features
      * Usually: Amount of data you have for each task is quite similar, then data from other classes are bigger than any one class, fulfill transfer learning
      * Can train a **big enough** neural nerwork to do well on all the tasks
8. What is end-to-end learning  
   Pros
   * let the data speak
   * less hand-designing of components needed     
   
   Cons
   * May need large amount of data
   * Excludes potentially useful hand-designed components   

   Key question: Do you have **sufficient data** to learn a function of the complexity needed to map x to y