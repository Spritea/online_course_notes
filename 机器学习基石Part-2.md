# 机器学习基石Part 2   

<sub>*How can Machines Learn*</sub>   

## Linear Regression   
1. Geometric View of Hat Matrix
2. LR的误差是二分类误差的上界
## Logistic Regression
1. Soft Binary Classification：Logistic Function: 把任意值转换到0-1之间
2. Three Linear Models
   * Linear Classification
   * Linera Regression
   * Logistic Regression 
3. Cross-Entropy Error
4. Gradient of Logistic Regression Error
   * Gradient Descent/梯度下降来最小化E_in(w)
   * 没有闭式解，做迭代优化
   * 用多维函数的Taylor展式来近似替代原函数，前提：步长很小
   * 好的步长应该和梯度的模正相关
   * Fixed Learning Rate=步长/该处梯度的模
## Linear Models for Classification
1. Binary Classification:用Linear/Logistic Regression来做二分类
   * 线性回归用来初始化PLA/pocket/logistic regression的w_0
   * 人们偏向于logistic regression，而不是pocket
2. Stochastic Grad. Descent
   * stochastic gradient= true gradient+ zero-mean 'noise' directions
   * after enough steps, average true gradient 约= aversge SGD
   * pro: simple
   * cons: less stable in nature
   * SGD logistic regression 约= 'soft' PLA
3. Multiclass via Logistic
   * One Class at a Time Softly
   * 1 VS.所有/One Versus All/OVA Decomposition
   * pro: efficient
   * con: unbalanced for bigdata
4. Multiclass via Binary Classification
   * One versus one/OVO: 所有2分类器投票
   * pro: efficient, stable
   * con: more training, more space 
## Nonlinear Transformation
1. Quadratic Hypotheses
   * 圆形可分 映射成 线性可分/特征转换
   * Z空间直线-> X空间二次多项式/曲线
2. Two choices
   * feature transform
   * linear model