# Neural Network& Deep Learning
## 深度学习概论
## 神经网络基础
1. loss function是对单个函数来说， cost function是对整个训练集来说
2. vector计算比for循环快100X，SIMD指令-单指令流多数据流，用好numpy库
3. Python-broadcasting: 向量和实数做运算时，自动把实数扩充成向量；避免(5,)这种rank=1 矩阵，它既不是行向量也不是列向量（可用keepdim指明），最好直接用(5,1)这种明确的矩阵
## 浅层神经网络
1. activation function: 只在二元分类的输出层用sigma 函数，其他都用ReLU(Leaky ReLU,maybe)，可保证梯度
2. 使用非线性激活函数，才让NN有意义，否则就是一堆线性组合，和Log Reg没区别
3. 不能把权重矩阵全部初始化为0，否则hidden layerde的nodes都一样了；初始化权重矩阵w为很小的正值，从而落在tanh/sigma激活函数的梯度较大部分
## 深层神经网络
1. Hyperparameters-控制参数的参数: 调整它们，可得到不同的W和b
# Improving Deep Neural Network

