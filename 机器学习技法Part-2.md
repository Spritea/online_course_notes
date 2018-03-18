# 机器学习技法Part 2   

<sub>*Combining Predictive Features: Aggregation Models*</sub>   

## Blending and Bagging
1. motivation-better performance
2. uniform blending
   * reduces variance for most stable performance
3. linear blending=Lin model+ hypotheses as transform
4. any blending/stacking, easily overfitted
5. bootstrap aggregation/bagging
   * bagging works very well if base algorithm sensitive to data randomness
## Adaptive Boosting
1. Adaptive Boosting= weak base learning algorithm(student)+ optimal re-weighting factor(teacher)+ magic linear aggregation(class)
2. AdaBoost-Stump: efficient feature selection and aggregation
## Decision Tree
1. CART系列/C&RT/Classification and regression tree: fully-growth tree with cnostant leaves that come from bi-branching by purifying 
2. regularization by pruning: pruned decision tree
3. missing features: surrogate branch
4. C&AT
   * divide and conquer/边分割边切
   * even more efficient than AdaBoost-Stump
   * C4.5
## Random Forest
