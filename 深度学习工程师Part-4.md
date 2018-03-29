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
6. Pooling layer
   * Max pooling-参数：filter size+stride,p=0,不用通过BP来确定，设计模型的时候就定下来了，输出=取矩阵中最大值
   * Average pooling: less use
7. why convolutions
   * parameter sharing:A feature detector(such as a vertical edge detector) that's useful in one part of the image is probably useful in another part of the image
   * sparsity of connections:In each layer, each output value depends only on a small number of inputs
   * 具有平移不变性
## CNN cases
1. classic networks
   * LeNet-5: conv+ pool+ conv+ pool+ fc+ fc+ output, 60k parameters
   * AlexNet: ReLU, multiple GPUs, local response normalization, 60mill parameters
   * VGG-16: 2* Conv 64+ pool+ 2* Conv 128+ pool+ 3* Conv 256+ pool+ 3* Conv 512+ pool+ 3* Conv512+ pool+ fc 4096+ fc 4096+ softmax 1000, 138mill parameters
   * Res Net: skip connection/residual block
      * identity function is easy for Residual block to learn, so it doesn't hurt performance
2. 1x1 Conv/Network in Network: could shrink channel number
3. Inception network motivation
   * choose layer automaticly
   * 1 inception module 
      * 4 paths
      * previous avtivation(pa)+ 1x1 conv
      * pa+ 1x1 conv+ 3x3 conv
      * pa+ 1x1 conv+ 5x5 conv
      * pa+ maxpool(same)+ 1x1 conv
      * add 4 outpus together= channel concat
4. transfer learning: larger data, more layers to train/只用权重做初始化，然后全部重新训练
5. data augmentation
   * mirroring, random cropping
   * color shifting/RGB: PCA color augmentation-AlexNet
   * implemente distortions during training: use CPU thread to do data augmentation, 从而和GPU训练并行
6. tricks for benchmarks/not for building production systems
   * Ensembling: Train several networks independently and average their outputs
   * Multi-crop at test time: Run classifier on multiple versions of test images and average results
## Object detection
1. classification with localization
2. landmark detection
3. object detection
   * sliding windows detection- too slow/coarse
   * convolutional implementation of sliding windows
      * Turning FC layer into convolutional layers
      * Convolutional implementation of sliding windows
   * Bounding box predictions
      * output accurate bounding boxes: **YOLO**
        * Intersection over union>= 0.5-> correct
        * non-max suppression example
        * anchor box: overlapping objects
   * Region proposal- RCNN
     * R-CNN
       * 先用分割算法过一遍，再对分割结果中的物体作检测
       * Propose regions. Classify proposed regions one at a time. Output label+ bounding box-Slow
      * Fast R-CNN
        * Propose regions. Use convolution implementation of sliding windows to classify all the proposed regions
      * Faster R-CNN
        * Use convolutional network to propose regions
## Face recognition
1. Faceverification vs. face recognition
2. one-shot learning
  * Learning a "similarity" function: degree of difference between images
  * Siamese network
  * Triplet loss
3. Face verification and binary classification
## Neural Style Transfer
1. Visualizing CNN
2. Content loss function
3. Style loss function
