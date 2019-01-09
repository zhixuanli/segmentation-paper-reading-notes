### The progress of the reading plan: 
01 / 50

## Paper Information
#### Paper Title : 
[Encoder-Decoder with Atrous Separable Convolution for Semantic Image Segmentation](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=2ahUKEwik37fbi8zfAhXzOn0KHYpTCzQQFjACegQICBAB&url=https%3A%2F%2Farxiv.org%2Fabs%2F1802.02611&usg=AOvVaw0pOEX9DfWqpHvfnCjdywuy)
#### Conference : 
ECCV 2018
#### Authors and Institution
Liang-Chieh Chen, Yukun Zhu, George Papandreou, Florian Schro, Hartwig Adam

Google Inc.

#### Official codes:
[https://github.com/tensorflow/models/tree/master/research/deeplab](https://github.com/tensorflow/models/tree/master/research/deeplab)

#### Network Structure
![DeepLabv3+](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/deeplabv3+_1.png)

## Five questions about this paper:

### 1. [Problem Definition] What problem does this paper try to solve? 

1. Details recovered from the low resolution feature of the decoder output are not good enough when employing the DeepLab V3 model.
2. The DeepLabv3 is not very fast at the inference procedure.


### 2. [Contribution] What method is used in this paper? 
1. A new encoder-decoder structure that employs DeepLabv3 as the decoder and a simple yet effective decoder structure, in which **the low layer feature is concatenated with the high layer feature** is proposed.
2. Using **atrous convolution** to trade-off precision and runtime. 
	+ ASPP = atrous convolution + spatial pyramid pooling
	+ Atrous separable convolution = atrous convolution + depthwise separable convolution
3. For being faster, the **depthwise separable convolution** are applied to both ASPP module and decoder module.

### 3. Details about the experiment
#### 3.1 Which Datasets are used?

PASCAL VOC 2012 and Cityscapes datasets

#### 3.2 How is the experiment set up?

+ learning rate schedule: 
	+ "poly" policy = learning_rate(1 - iter/max_iter) ^ (power)
		+ optional float power = 10; // The parameter to compute the learning rate.
	+ initial learning rate 0.007
+ crop size 513 x 513
+ fine-tuning batch normalization parameters when output stride = 16
+ random scale data augmentation during training
+ We employ ImageNet-1k pretrained ResNet-101 or modified aligned Xception to extract dense feature maps by atrous convolution.

#### 3.3 What's the evaluation metric?
mIOU: pixel intersection-over-union averaged across all of the classes

#### 3.4 (Optional）How to divide training data and test data？

#### 3.5 (Optional）What is the ranking of the experiment results?
##### PASCAL VOC 2012 test set:

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/deeplabv3+_pascalvoc12.png)

DeepLabv3+ (Xception-JFT) : 89.0

##### DeepLabv3+ on Cityscapes test set:
![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/deeplabv3+_cityscapes.png)

DeepLabv3+ : 82.1

### 4. Advantages (self-summary rather than the author's)
1. Comparing to DeepLabv3, this paper designed a simple decoder to merge the low and high level features, corresponding to structure details and semantic information, to extract more information from the input image.
2. Using atrous and depthwise separable convolution to computer faster while maintaining the quite similar precision.
3. **Xception model** and ResNet 101 are used as backbone here for better performance (both accuracy and speed).
4. The number of parameters is not very large.

### 5. Disadvantages (self-summary rather than the author's)
Some naive thoughts:  

1. the bilinear upsampling method may be not good enough
2. to gain more informations, maybe more features from the inner layers should be concatenated with the low level feature.

