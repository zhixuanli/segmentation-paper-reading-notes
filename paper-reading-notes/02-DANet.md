### The progress of the reading plan: 
2 / 50

## Paper Information
#### Paper Title : [Dual Attention Network for Scene Segmentation](https://arxiv.org/abs/1809.02983)

#### Conference : AAAI 2019

#### Authors and Institution
Jun Fu, Jing Liu, Haijie Tian, Zhiwei Fang, Hanqing Lu

CASIA IVA (中科院自动化所)

#### Official Code: [https://github.com/junfu1115/DANet](https://github.com/junfu1115/DANet)

#### Unofficial PPT for comprehending
[https://blog.csdn.net/mieleizhi0522/article/details/83111183](https://blog.csdn.net/mieleizhi0522/article/details/83111183)

#### Network Structure
![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/DANET-1.png)

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/DANET-2.png)

#### Some reference to comprehend this paper
+ [双重注意力网络：中科院自动化所提出新的自然场景图像分割框架（附源码）](https://www.jiqizhixin.com/articles/091204)
+ [论文阅读-Dual Attention Network for Scene Segmentation](https://zhuanlan.zhihu.com/p/48056789)

## Notes
### Summary in one sentence

Adopting self-attention mechanism, which essentially means to use weighted summation at all positions to update each certain position, to capture the relationship between different positions and channels. 

### Keywords
self-attention, Scene Segmentation

## Five questions about this paper:

### 1. [Problem Definition] What problem is this paper trying to solve? 
State-of-the-art methods based on FCNs, which utilize multi-scale context information but mining the relationship between different objects and stuffs are lacking.

In the same time, capturing the global relationship by employing LSTM or RNN will heavily rely on the learning outcome of the long-term memorization.


### 2. [Contribution] What's new in this paper? 

The DANet append two types of attention modules to capture the relationship between positions and channels.

For position attention module, each position will be updated via all positions with weighted summation, to mining the relationship between different objects. The weight is decided by the similarity of the two positions. The channel attention module is similar to the position attention module.

This attention module can be directly inserted into the existing FCNs based pipelines and will not increase too much parameters.

### 3. Details about the experiment
#### 3.1 Which Datasets are used?
+ Cityscapes dataset
+ PASCAL Context dataset
+ COCO Stuff dataset

##### Cityscapes 
The dataset has 5,000 images captured from50 different cities. Each image has 2048  1024 pixels, which have high quality pixel-level labels of 19 semantic classes. There are 2,979 images in training set, 500 images in validation set and 1,525 images in test set. We do not usecoarse data in our experiments.
##### PASCAL 
Context The dataset provides detailed semantic labels for whole scenes, which contains 4,998 images for training and 5,105 images for testing. 
##### COCO Stuff 
The dataset contains 9,000 images for training and 1,000 images for testing. 

#### 3.2 How is the experiment set up?
##### 3.2.1 Ablation studies are performed here.
+ Using dilated FCNs as the baseline, the ablation study determines the improvement of attention module.

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/DANET-exp1.png)

+ Ablation study for improvement strategies: 

	+ (1) DA: Data augmentation with randomscaling.
	+ (2) Multi-Grid: we apply employ a hierarchyof grids of different sizes in the last ResNet block. 
	+ (3) MS: We average the segmentation probability maps from 6 imagescales (0.75 1 1.25 1.5 1.75 2) for inference.

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/DANET-exp2.png)

And I'm surprised to know that these strategies could improve so much performance!

#### 3.3 What's the evaluation metric?
Mean IoU

#### 3.5 (Optional）What is the ranking of the experiment results?
"DANet outperforms existing approaches with dominantly advantage!"

But actually the performance is **not better than DeepLab V3+**.

![](https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/DANET-exp3.png)

But the Deeplabv3+ (the best in deeplab series) is published almost half a year before the DANet, and they are not compared in this paper.

### 4. Advantages (self-summary rather than the author's)
The attention modules capture relationship between positions and channels very well. No matter how far the two positions are, the similar features will always have strong connections.

### 5. Disadvantages (self-summary rather than the author's)


### Appendix
1. When capturing the similarity between different positions or channels, the matrix multiplication is used. Why the matrix multiplication can represent the similarity?

Because when we have two point (x1, y1) and (x2, y2), the Euclidean Distance between them is $\sqrt{(x_2-x_1)^2 + (y_2-y_1)^2}$

And for the normalization is used here, the $\sqrt{x^2+y^2}=1$ , so

$\sqrt{(x_2-x_1)^2 + (y_2-y_1)^2}=\sqrt{2-2(x_1x_2+y_1y_2)}$

