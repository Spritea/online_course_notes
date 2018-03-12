# 机器学习技法Part 1   

<sub>*Embedding Numerous Features: Kernal Models*</sub>   

## Linear SVM
1. Margin Problem: 分割线离最近数据的距离/margin越远越好
2. call boundary example support vector(candidate)
   * quadratic programming- easy optimization
   * 最小化二次函数，条件只含该变量的一次式
   * SVM with general QP solver- easy
3. why Large-Margin Hyperplane
   * SVM模型等效于
      * weight-decay regularization within E_in= 0
      * 带margin的PLA，较小的VC维
   * SVM算法
      * feature transform->较小E_in
      * VC维很小->较好泛化性能
## Dual SVM
1. Motivation of Dual SVM
   * Constrained to 'Unconstrained'
   * Lagrange Dual Problem