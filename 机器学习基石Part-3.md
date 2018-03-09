# 机器学习基石Part 3   

<sub>*How can Machines Learn Better*</sub>   

## Hazard of Overfitting
1. learning curve
   * 样本量较小时，模型越复杂，泛化误差越大于训练集内误差
   * 模型复杂度起着类似增加噪声的作用
2. Stochastic noise/ Deterministic noise
3. Dealing with Overfitting     
   * data cleaning/data pruning
   * data hinting: virtual example not i.i.d. P(x,y)
## Regularization
1. Regularized hypothesis Set
   * Regression with Looser Constraint/直接控制多项式阶数: NP hard
   * Regression with Softer Constraint/控制多项式各项系数的大小
2. Weighted Decay(L2) Regularization
   * Lagrange乘子做带限优化，最优解为ridge regression
   * regularization with Augmented Error, instead of constrainted E_in
   * a little regularization goes a long way
   * 多项式用Legendre polynomial=正交基底函数
3. Regularization and VC Theory
4. General Regularizers
   * want: constraint in the 'direction' of target function 
   * noise越大，需要越大的regularization项
      * L2 Regularizer-Weighted Decay
      * L1 Regularizer-Sparsity in solution