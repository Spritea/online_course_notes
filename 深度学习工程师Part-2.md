# Improving Deep Neural Network
## 深度学习的实用层面
1. 训练目的:low-bias && low-variance
2. reguarization
   * L2
   * dropout-inverted dropout:按设置的概率keep-prop随机干掉一些节点，简化网络
   * data augmentation
   * early stopping
3. 归一化输入，使代价函数对称些，便于优化
4. exploding or vanishing gradients: 神经网络的权重初始化
5. gradient checking/debug时才用
   * numerical approximation of gradients: 用双边导数逼近梯度值比单边导数更准确
   * gradient checking
   * 若有regularization, grad check时要包括regularization项
   * 不能与dropout一起用，可以先用grad check，再用dropout
## Optimization Algorithms
1. 
