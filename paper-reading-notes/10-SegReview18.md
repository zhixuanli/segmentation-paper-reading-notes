### The progress of the reading plan: 
10 / 50

## Paper Information
#### Paper Title : 
[Recent progress in semantic image segmentation](https://arxiv.org/pdf/1809.10198) 

#### Magazine : 
Artificial Intelligence Review

#### Authors and Institutions
##### Authors
+ Xiaolong Liu 1
+ Zhidong Deng 1
+ Yuhan Yang 2

##### Institutions
+ State Key Laboratory of Intelligent Technology and Systems, Beijing National Research Center for Information Science and Technology, Department of Computer Science, Tsinghua University, Beijing 100084, China
+ Department of Economics and Management, Tsinghua University, Beijing 100084, China

## Note

### 1. Introduction
+ **Semantic segmentation**, also called pixel-level classification, is the task of clustering parts of image together which belong to the same object class
+ Moreover, there is a task named **instance segmentation** which joints detection and segmentation together.

##### Applications
+ detecting road signs
+ land use and land cover classification
+ detecting brains and tumors
+ detecting and tracking medical instruments in operations
+ self-driving car area

### 2. Datasets and evaluation metrics
#### 2.1 Datasets
+ PASCAL VOC
+ MS COCO
+ ADE20K
+ Cityscapes
+ KITTI
+ [Others](http://homepages.inf.ed.ac.uk/rbf/CVonline/Imagedbase.htm#segmentation)

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/01.png" width="80%" height="80%" />
</div>

#### 2.2 Evaluation metrics
+ $P_{acc}$ : pixel accuracy 
+ $M_{acc}$ : mean accuracy
+ $M_{IU}$ : region intersection upon union (IU)
+ $FW_{IU}$ : frequency weighted IU

Actually **Mean Intersection over Union (MIoU)** is the most frequently used evaluation metric now as I think.

### 3. Traditional methods

### 4. Recent DNN in segmentation
#### 4.1 Fully convolutional network (FCN)
The paper (Long et al. 2014) is the first work that introduces DNN to image segmentation area.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/02.jpg" width="60%" height="60%" />
</div>

#### 4.2 Up-sample method: interpolation versus deconvolution
+ bi-linear interpolation
+ deconvolution

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/03.jpg" width="80%" height="80%" />
</div>

#### 4.3 FCN joint with CRF and other traditional methods
##### FCN joint with CRF

According to the research of Deeplab, the responses at the final layer of DCNNs are not sufficiently localized for accurate object segmentation (Chen et al. 2016b).
They overcome this poor localization property by combining a fully connected Conditional Random Field (CRF) at the final DCNN layer.

##### FCN joint with other traditional methods

+ domain transform
+ super-pixels
+ MarkovRandom Field (MRF)

#### 4.4 Dilated convolution
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/04.png" width="80%" height="80%" />
</div>

Dilated convolution, also called 'Atrous Convolution' or 'Hole Convolution' is originally developed for the efficient computation.

The dilated convolution has griding artifacts, and the dilated residual networks (DRN) was proposed in 2017 to remove these artifacts and further increase the performance of the network.

#### 4.5 Progress in backbone network
+ VGG-16 (adopted by FCN)
+ ResNet
+ ResNeXt
+ Inception-ResNet

Actually there also exist Xception and DenseNet.

#### 4.6 Pyramid method in segmentation

##### 4.6.1 Image pyramid
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/05.png" width="80%" height="80%" />
</div>

There are two common kinds of image pyramids: 
Gaussian pyramid which is used to downsample images and Laplacian pyramid which is used to reconstruct an upsampled image from an image lower in the pyramid (with less resolution).

Deeplab implements an image pyramid structure (Chen et al. 2016c) which extracts multi-scale features by feeding multiple resized input images to a shared deep network.

Laplacian pyramid is also used by (Ghiasi and Fowlkes 2016). They bring out a multi-resolution reconstruction architecture based on a Laplacian pyramid, which **uses skip connections from higher-resolution feature maps** and multiplicative gating to progressively **refine boundaries reconstructed from lower resolution feature maps**.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/06.png" width="80%" height="80%" />
</div>

##### 4.6.2 Atrous spatial pyramid pooling
ASPP
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/07.png" width="60%" height="60%" />
</div>

##### 4.6.3 Pooling pyramid
PSPNet
<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/09.png" width="60%" height="60%" />
</div>

##### 4.6.4 Feature pyramid
In fact, recent deep learning object detectors have avoided pyramid representation because **it is compute and memory intensive**.

#### 4.7 Multi-level feature and multi-stage methods
Structure adopted in Hariharan et al. (2015) as hypercolumns

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/10-SegReview18/08.png" width="60%" height="60%" />
</div>

#### 4.8 Supervised, weakly-supervised and unsupervised methods

## Conclusion
This paper roughly summarizes the progress of deep learning methods in the semantic segmentation field.

But the techniques introduced in this paper are not intact, but enough comprehensive.