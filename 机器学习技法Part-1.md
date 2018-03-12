# 机器学习技法Part 1   

<sub>*Why can Machines Learn*</sub>   

## Linear SVM
1. Margin Problem: 分割线离最近数据的距离/margin越远越好
2. call boundary example support vector(candidate)
   * quadratic programming- easy optimization
   * 最小化二次函数，条件只含该变量的一次式
   * SVM with general QP solver- easy
3. why Large-Margin Hyperplane
   * SVM: weight-decay regularization within E_in= 0