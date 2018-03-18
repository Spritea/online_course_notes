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
   * use special solver
2. SVM/PLA的w均可用data表示
## Kernal SVM
1. Kernal: Transform+ Inner Product
2. Kernal trick: plug in efficient kernal function to avoid dependence on d^~
3. General Poly-2 Kernal
   * change of kernal-> change of margin definition
   * genaral polynomial kernal
4. Gaussian kernal: RBF Kernal
   * large r：sharp Gaussian, overfit
   * warning: SVM can still overfit
5. Compare kernals: kernal 需满足Mercer's condition=kernal矩阵半正定（特征值非负）
## Soft-Margin SVM
## Kernal Logistic Regression
1. SVM: L2 regularization
2. SVM for Soft Binary Classification
3. Kernal Logistic Regression: represent theorem on L2-regularized LogReg
## Support Vector Regression
1. Kernal ridge regression
2. kernal ridge regression 换误差衡量=SVR

