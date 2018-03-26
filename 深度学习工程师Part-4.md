# Convolutional Neural Network
## CNN
1. Edge detection example
2. Padding
   * fix shrinking output
   * use edge information efficiently
   * Valid convolutions: no padding
   * Same convolutions: Pad so that output size is the same as the input size
   * use odd-numbered filter
3. Strided convolutions
   * filter必须在原图像/填充后的图像中
   * 实际做的是cross-correlation，而不是convolution，因为没有对filter做上下和左右的翻转，就直接拿去乘了
4. Convolutions over volumes
   * convolutions on RGB
   * detect different color edges
   * 输出的通道数=检测的特征种数
5. One layer of a convolutional network
   * 输入图像与各个filter卷积，加常数，再做ReLU，再把各个输出叠起来，便是经过了一层卷积
   * layer types in CNN: Conv,Pool,FC