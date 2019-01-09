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
+ Paper: [The cityscapes dataset for semanticurban scene understanding](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Cordts_The_Cityscapes_Dataset_CVPR_2016_paper.pdf)
+ Main page: [https://www.cityscapes-dataset.com](https://www.cityscapes-dataset.com)

### Details
+ 30 classes
+ 5000 annotated images with fine annotations
+ 20000 annotated images with coarse annotations