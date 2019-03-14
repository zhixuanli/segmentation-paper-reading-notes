[TOC]
# Summary of the semantic segmentation datasets

## 1. PASCAL VOC 2012

+ Paper : [The Pascal Visual Object Classes Challenge: A Retrospective](http://www.research.ed.ac.uk/portal/files/20017166/ijcv_voc14.pdf)
+ Main page : [http://host.robots.ox.ac.uk/pascal/VOC/voc2012/](http://host.robots.ox.ac.uk/pascal/VOC/voc2012/)

It contains 20 foreground object classes and one background class. 

1464 (train), 1449 (val), and 1456 (test) pixel-level annotated images.

## 2. Semantic Boundaries Dataset (SBD)

+ Paper : [Semantic contours from inverse detectors](http://home.bharathh.info/pubs/pdfs/BharathICCV2011.pdf)
+ Dataset main page: [Semantic Boundaries Dataset and Benchmark](http://home.bharathh.info/pubs/codes/SBD/download.html)

The 11318 images in the SBD are divided into 8498 training images and 2820 test images.

## 3. PASCAL VOC 2012 augmented with SBD 

+ Download Link: [https://www.dropbox.com/s/oeu149j8qtbs1x0/SegmentationClassAug.zip?dl=0](https://www.dropbox.com/s/oeu149j8qtbs1x0/SegmentationClassAug.zip?dl=0)  
+ This download link is provided by: [https://github.com/DrSleep/tensorflow-deeplab-resnet](https://github.com/DrSleep/tensorflow-deeplab-resnet)
+ [How to use 10,582 train-aug images on DeeplabV3 code?](https://www.sun11.me/blog/2018/how-to-use-10582-trainaug-images-on-DeeplabV3-code/)

## 4. The COCO-Stuff dataset

+ Paper(CVPR, 2018): [COCO-Stuff: Thing and Stuff Classes in Context](https://arxiv.org/abs/1612.03716)
+ Main page: [https://github.com/nightrome/cocostuff](https://github.com/nightrome/cocostuff)

 COCO-Stuff augments all 164K images of the popular COCO dataset with pixel-level stuff annotations.

+ **COCO-Stuff dataset: The final version of COCO-Stuff, that is presented on this page.** It includes all 164K images from COCO 2017 (train 118K, val 5K, test-dev 20K, test-challenge 20K). It covers 172 classes: 80 thing classes, 91 stuff classes and 1 class 'unlabeled'. This dataset will form the basis of all upcoming challenges.
+ COCO 2017 Stuff Segmentation Challenge: A semantic segmentation challenge on 55K images (train 40K, val 5K, test-dev 5K, test-challenge 5K) of COCO. To focus on stuff, we merged all 80 thing classes into a single class 'other'. The results of the challenge were presented at the Joint COCO and Places Recognition Workshop at ICCV 2017.
+ COCO-Stuff 10K dataset: Our first dataset, annotated by 10 in-house annotators at the University of Edinburgh. It includes 10K images from the training set of COCO. We provide a 9K/1K (train/val) split to make results comparable. The dataset includes 80 thing classes, 91 stuff classes and 1 class 'unlabeled'. This was initially presented as 91 thing classes, but is now changed to 80 thing classes, as 11 classes do not have any segmentation annotations in COCO. This dataset is a subset of all other releases.

## 5. PASCAL-Context Dataset
+ paper: ["The Role of Context for Object Detection and Semantic Segmentation in the Wild"](https://cs.stanford.edu/~roozbeh/pascal-context/mottaghi_et_al_cvpr14.pdf)
+ Main page: [https://cs.stanford.edu/~roozbeh/pascal-context/](https://cs.stanford.edu/~roozbeh/pascal-context/)

PASCAL-Context dataset augments PASCAL VOC 2010 dataset with annotations for 400+ additional categories. The dataset contains semantic segmentation annotations for 10,103 images in the Training and Validation subsets of PASCAL VOC 2010 dataset. 

The previous annotations covered around 29% of pixels in the dataset, while ours covers 100% of pixels. The dataset contains annotations for things (e.g., keyboard, fork), stuff (e.g., sky, water) and hybrids (e.g., road) that have clear boundaries, but their shape is more complex than the shape of things.

## 6. Cityscapes Datasets
+ Paper: [The cityscapes dataset for semantic
urban scene understanding](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Cordts_The_Cityscapes_Dataset_CVPR_2016_paper.pdf)
+ Main page: [https://www.cityscapes-dataset.com](https://www.cityscapes-dataset.com)

**Details:**

+ 30 classes
+ 5000 annotated images with fine annotations
+ 20000 annotated images with coarse annotations

**Descriptions:**

CITYSCAPES is a real-world vehicle-egocentric image dataset collected from 50 cities in Germany and the countries around. 

There are 5000 annotated images with fine annotations. 

It provides three disjoint subsets: 2975 training images, 500 validation images, and 1525 test images. It also provides accurate pixel-level annotations for all images with 19 different categories.



## 7. PASCAL-$5^i$ (for shot learning)

+ Paper: [One-shot learning for semantic segmentation](https://arxiv.org/abs/1709.03410)
+ Main Page: [https://github.com/lzzcd001/OSLSM](https://github.com/lzzcd001/OSLSM)

**The following descriptions are from [Attention-based Multi-Context Guiding for Few-Shot Semantic Segmentation](https://www.google.com.hk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwijz7mQsOrfAhVVUd4KHYsXCfUQFjAAegQIAhAC&url=https%3A%2F%2Fpdfs.semanticscholar.org%2F1216%2Feebb5a407b40eb46596073f0fd229acaea48.pdf&usg=AOvVaw2z0pB6k3R4zdgLhFZiQcFM)**

This dataset is originated from PASCAL VOC12 (Everingham et al. ) and extended annotations from SDS (Hariharan et al. ). The set of 20 classes in PASCAL VOC12 is divided into four sub-datasets as indicated in Table 2. Three sub-datasets are used as the training label-set $L_{train}$, the left one sub-dataset is utilized for test label-set $L_{test}​$.

<div  align="center">    
<img src="https://raw.githubusercontent.com/zhixuanli/segmentation-paper-reading-notes/master/images-folder/PASCAL-5i.png" width="60%" height="60%" />
</div>

The training set $D_{train}$ is composed of all image-mask pairs from PASCAL VOC12 and SDS training sets that include at least one pixel in the segmentation mask from the label-set $L_{train}$. The masks in $D_{train}$ are modified into binary masks by setting pixels whose semantic class are not in $L_{train}$ as background class l. The test set $D_{test}$ is from PASCAL VOC12 and SDS validation sets, and the processing procedure for test set $D_{test}$ is similar with training set $D_{train}​$.



## 8.  SYNTHIA

+ Paper: [The synthia dataset: A large collection of synthetic images for semantic segmentation of urban scenes](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=2ahUKEwj4uY322ezfAhUJKHwKHRJeD30QFjAAegQIARAC&url=http%3A%2F%2Frefbase.cvc.uab.es%2Ffiles%2FRSM2016.pdf&usg=AOvVaw31lOP8Ts2FzXe0AcGtO6vU)
+ Main Page: [http://synthia-dataset.net/download-2/](http://synthia-dataset.net/download-2/)

> SYNTHIA is a large dataset of photo-realistic frames rendered from a virtual city with precise pixel-level annotations.



> It is the set containing the original 13,407 images used to perform training and domain adaptation of the models presented in our CVPR’16 paper. These images are generated as random perturbation of the world and therefore do not have temporal consistency (this is not a video stream). These images have annotations for 11 basic classes and do not have annotations for instances. The classes are: void, sky, building, road, sidewalk, fence, vegetation, pole, car, sign, pedestrian, cyclist.



## 9.  GTA-5

+ Paper: [Playing for data: Ground truth from computer games.](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=2ahUKEwjwyeuF2-zfAhWjMnwKHfHYB6gQFjABegQICBAC&url=http%3A%2F%2Fvladlen.info%2Fpapers%2Fplaying-for-data.pdf&usg=AOvVaw2Oaq_UNH_yaDNxiazvRMki)
+ Main Page: [https://download.visinf.tu-darmstadt.de/data/from_games/index.html](https://download.visinf.tu-darmstadt.de/data/from_games/index.html)
+ Code: [https://bitbucket.org/visinf/projects-2016-playing-for-data](https://bitbucket.org/visinf/projects-2016-playing-for-data)

>  GTA-5 contains 24966 high quality labeled frames from realistic open-world computer games, Grand Theft Auto V (GTA-5). Each frame is generated from fictional city of Los Santos, based on Los Angeles in Southern California with annotations that are compatible with CITYSCAPES dataset.

## 10. ADE20K
+ Paper: [Scene parsing through ade20k dataset.](http://openaccess.thecvf.com/content_cvpr_2017/papers/Zhou_Scene_Parsing_Through_CVPR_2017_paper.pdf)
+ Main Page: [http://groups.csail.mit.edu/vision/datasets/ADE20K/](http://groups.csail.mit.edu/vision/datasets/ADE20K/)
+ Code: [https://github.com/CSAILVision/semantic-segmentation-pytorch](https://github.com/CSAILVision/semantic-segmentation-pytorch)

> ADE20K is a recent scene parsing benchmark containing dense labels of 150 stuff/object categories. The dataset includes 20K/2K/3K images for training, validation and test.

## 11. COCO panoptic segmentation dataset
+ [http://cocodataset.org/#panoptic-2018](http://cocodataset.org/#panoptic-2018)
+ 

## ATTENTION

Descriptions are gathered from many different papers, and thank you all !