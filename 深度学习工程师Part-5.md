# Sequence Models
## RNN
1. Only use former information, without using later information to classify a word.
2. BP through time
3. Different types of RNN
   * input length=output length
   * many-to-one architecture, input the whole sentence, eg. sentiment classification
   * one-to-many architecture, eg. music generation/sequence generation
   * input length !=output length, eg. translation
4. Language model and sequence generation
   * language modelling with an RNN
      * Tokenize: build a dictionary
      * precode(one-hot) these words
      * add EOS(End of Sentence)
      * use UNK to represent unknown word
      * loss function: softmax
5. Sampling novel sequences to check trained language model
   * Sampling a sequence from a trained RNN with word-level language model
   * or character-level language model
      * pro: no UNK
      * con: model size is much larger than word-level
6. Vanishing gradients with RNNs
   * basic RNN can't capture very long-term dependencies
      * due to gradient vanishment
      * would have local influences: one word is mainly influenced by words nearby
   * use gradient clipping to solve exploding gradient, it's easier to be solved by vanishing gradient
7. Gated Recurrent Unit-GRU
   * solve vanishing gradient
   * use memory cell to save long-term relation and determine whether to update memory cell weights
   * 2 gates: update gate and relevance gate
   * simple and fast
8. Long Short Term Memory-LSTM unit
   * 3 gates: update gate, forget gate and output gate
   * keep long-term relation
   * peephole connection: the previous memory cell value also influences gate value
9. Bidirectional RNN-BRNN
   * get information from the future, both forward and backward
   * good choice for NLP problem with complete sentence: bidirectional RNN with LSTM blocks
   * limit: you need the entire sequence of data, before you can make predictions anywhere: you can only translate language after sb stops speaking.
10. Deep RNNs
   * stack RNN, <10 layers, because one layer of RNN is very long(time-dimension)

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