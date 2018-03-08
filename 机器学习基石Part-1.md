# 机器学习基石Part 1   

<sub>*Why can Machine Learning work*</sub>   

## The Learning Problem    
1. 适用机器学习的条件  
    * 存在范式
    * 普通的程序不方便定义
    * 有关于范式的数据
2. 机器学习模型=算法+假设
3. **机器学习ML**：用数据来计算假设，逼近真实的分布  
**数据挖掘DM**：从大数据中找到**感兴趣**的性质，如果ML的假设就是感兴趣的性质，那么此时ML=DM  
**人工智能AI**：让机器具备智能行为，机器学习是实现人工智能的方式   
**统计Statistics**: 使用数据来对某个未知过程做推理，是从数学出发的，可以用来实现机器学习
## Learning to Answer Yes/No
1. 感知器假设+算法，感知器就是线性分类器的一种  
2. 感知器算法    
   * Perceptron Learning Algorithm=> W(t+1)= W(t)+y[n(t)]x[n(t)]
   * h-正负分割线就是W(t)的法线   
   * 证明了PLA算法会停/收敛，前提：数据线性可分   
3. 处理带噪声的线性
   * 没有闭式解，np-hard问题
   * Pocket：以迭代的方式最小化误差，比PLA慢
   * 通过保持最好的线在手里，来调整PLA
   * 学习算法的类型  
      * 监督式
      * 无监督
      * 半监督
      * 强化学习
4. 学习的可行性分析
   * No Free Launch：针对某一领域所有问题，所有算法的期望性能是相同的
   * Hoeffding不等式：样本足够大时，样本分布接近真实分布，故能用抽样来估计真实的分布
## Training versus Testing
1. 讨论误差上限，对假设进行分类
   * 有效线的数量是有限的
   * 有效假设的数量=有效线的数量
2. 成长函数=假设数量对于样本数量的函数
3. 断点k：growth function对于k的值<2^k(shatter)，关注最小断点
## Theory of Generalization
1. minimum break point对假设数量的限制:固定minimum break point，固定样本数量，便固定了假设的数量，也就是dichotomy（二分）的条数
2. bounding function/上限函数:对于mbp的最大假设数量
3. VC bound形象化证明（不严格）
## The VC Dimension
1. VC维=最大的non-break point=minimum break point-1，是对minimum break point的另一种定义
2. 多维perceptron的VC维
   * 1D perceptron的VC维=2
   * 2D perceptron的VC维=3 
3. 证明d(vc)=d+1
   * d(vc)>=d+1：存在d+1个inputs，可以shatter，此时数据矩阵为d+1*d+1的方阵
   * d(vc)<=d+1：任意d+2个inputs都不能shatter，此时数据矩阵为行d+2*d+1列的长条阵（ *注：此时均考虑没有noise和error的情况，即当行数大于列数时，矩阵对应的线性方程组是相容的，不会出现矛盾的情况，从而多出的一行均可由其他行的线性组合来表示*）
   * shatter可理解成数据矩阵可逆
4. VC维的物理意义：二元分类的有效自由度个数/假设集中有效假设的个数
5. VC维进一步解释
   * Penalty for Model Complexity
   * Sample Complexity:
      * 理论上，数据量N约等于10,000*d(vc)，可取得误差上界
      * 实际中，N约等于10*d(vc)够用了
      * 因为考虑到任意分布、数据等，VC bound相对于实际的bound比较宽松
## Noise and Error
1. Target Distribution P(y|x), VC仍然有用
2. Error Measure
   * out-of-sample
   * pointwise
   * classification or 0/1
3. Pointwise Error Measures
   * classification error, for classification
   * squared error, for regression 
   * P(y|x)和error measure定义了ideal mini-target f(x)
   