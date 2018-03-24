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
1. mini-batch gradient descent
   * mini-batch size=all: batch grad descent，可以收敛到最佳点
   * mini-batch size=1: stochastic grad descent，不能做向量化来加速运算，不能收敛到最佳点
   * mini-batch size=medium
2. choose mini-batch size
   * small training set<2000: batch grad desc
   * 大于2000: 2^n
3. exponentially weighted averages-历史值和当前值的加权平均，离当前值较近的权重越大/bias correction-修正早期误差
4. gradient descent with momentum=grad+ exponentially weighted average 
5. RMSprop(Hinton): root mean square prop
6. Adam optimizaiton algorithm/Adaptive moment estimation= momentum+ RMSprop
7. learning rate decay

