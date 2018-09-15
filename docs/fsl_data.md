## Datasets for Zero shot learning
**数据集简介**

Zero-Shot Learning数据集用于建立 **视觉特征** 和 **语义特征** 的联系。因此，一个ZSL数据集既包含图像，也包含相应的语义特征。语义特征是一个向量，有如下几种形式：

- 属性（颜色、形状、大小等）
- 词向量 
- 文本描述

语义特征的特点是：**相似的图像具有相似的语义特征。**  现有ZSL方法即针对该特性进行建模。

---

### Animal With Attributes (AWA) [[AWA网址]](https://cvml.ist.ac.at/AwA/) [[AWA2网址]](https://cvml.ist.ac.at/AwA2/)
AWA数据集包含50种常见动物的**图像**与**属性**。其具体细节在论文[[Learning to detect unseen object classes by between-class attribute transfer]](http://ieeexplore.ieee.org/document/5206594/)中描述。

- 图像：AWA包含30475张(AWA2：37322张)图像，分为50个类别，每类别至少92张。这些图像来自Google, Microsoft, Yahoo and Flickr等搜索引擎的检索结果。其中重复、难以清晰辨认的检索结果被剔除，因此AWA是一个较为理想化的数据集。

- 语义信息：属性，**每个类别**标注了real-value属性，共85项属性。这些属性的值是由人类专家根据*relative strength of association*原则 **主观确定** ，其具体过程参见论文第4节。

--- 
### aPascal & Yahoo (APY) [[APY网址]](http://vision.cs.uiuc.edu/attributes/) 

APY数据集包含32种日常生活常见物体的**图像**、**Boundbox**与**属性**。其细节在论文[[Describing objects by their attributes]](http://ieeexplore.ieee.org/document/5206772/)[作者Ali Farhadi,YOLO通讯作者]中描述。

- 图像：APY包含15339个Boundbox图像(有的jpg文件含有多个boundbox)。是两个数据集aPascal(VOC 2008的一个子集,12695张)和aYahoo(2644张)的综合，包含了32种日常生活中常见的类别。其中20个类别来自于VOC2008:
	- **Person**: person
	- **Animal**: bird, cat, cow, dog, horse, sheep
	- **Vehicle**: aeroplane, bicycle, boat, bus, car, motorbike, train
	- **Indoor**: bottle, chair, dining table, potted plant, sofa, tv/monitor  
	12个类别来自于Yahoo:
	- **Animal**: donkey, monkey, goat, wolf, zebra, centaur
	- **Vehicle**: jetski, carriage
	- **Indoor**: mug, bag
	- **Outdoor**: statue, building

- 语义信息：属性，**每张图片**标注了64种常见属性，0-1属性，表示某个特性存在或不存在，用土耳其机器人标注获得。

- 注意事项：
	- [APY网址]中的VOC2008链接失效，请使用[[VOC2008-new]](http://pascallin.ecs.soton.ac.uk/challenges/VOC/voc2008/)
	- APY包含许多噪声，其中Person类别（来自VOC2008）的图像达到了5071张。因此ZSL已经逐步弃用这个数据集。

- 论文的启示：
	- 0. 泛化问题在Few shot问题当中依然存在，但是并不能用传统的Variance来刻画。 
	- 1. 提出了Correlation问题，指出一个刻画attr过拟合的指标。 
	- 2. 用特征x去学习属性a，学到的映射是依赖于数据集的。本文提出了解决这一依赖的方法。
	- 3. Discriminative属性是提升泛化能力的关键，但是数据集中只给出了64维semantic属性。
	- 4. 属性和feature map的某个局部是有对应关系的。许多时候“摩托车”出现了“皮肤”这一属性(见图8和6.1.2节)，是因为所选图片的Boundbox中还包含了人。

---
### The Caltech-UCSD Birds-200-2011 Dataset (CUB) [[数据集地址]](http://www.vision.caltech.edu/visipedia/CUB-200-2011.html) [增强数据集[CUB+Sentences]](https://drive.google.com/open?id=0B0ywwgffWnLLZW9uVHNjb2JmNlE)

CUB数据集包含200种北美地区常见的鸟类,包含**图像**、**Segmentation**、**Boundbox**与**属性**。其细节在技术报告[[Caltech-UCSD Birds 200]](http://www.vision.caltech.edu/visipedia/papers/WelinderEtal10_CUB-200.pdf)和[[The Caltech-UCSD Birds-200-2011 Dataset]](http://authors.library.caltech.edu/27452/1/CUB_200_2011.pdf)中描述。

- 图像：CUB包含11788张图像。包含了200种不同的北美鸟类照片。图像还包含了Segmentation和Boundbox的标注。以及给出了鸟类各部位（啄、左翼、右翼、左眼、右眼）的中心位置(没有Boundbox)。

- 语义信息：属性，**每张图片**标注了312维的0-1属性（本质是28维离散取值的属性转化成的one-hot向量），1表示某个特性存在(0不存在)。这些属性涵盖了鸟类的各部位的颜色和形状。每个属性还给出了人工标注的犹豫时间和确信程度。

- 外部信息：数据集为**每张图片**提供了10个句子的描述。详见：[论文[Learning Deep Representations of Fine-Grained Visual Descriptions.]](http://ieeexplore.ieee.org/document/7780382/)。文中使用text based CNN+RNN将句子向量化。

---
### FLO [数据集地址](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/) [增强数据集[Flower+Sentences]](https://drive.google.com/open?id=0B0ywwgffWnLLcms2WWJQRFNSWXM)

FLO数据集包含102种英国常见的花,包含**图像**、**Segmentation**、**文本描述**。其细节在论文报告[[Automated Flower Classification over a Large Number of Classes]](http://www.robots.ox.ac.uk/~vgg/publications/papers/nilsback08.pdf)中描述。

- 图像：FLO包含8189张图片, 102个类别的不同种类的花。每类有40到258张的图片。图片样例详见[这里](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/categories.html)

- 语义信息：FLO**不提供属性**


- 外部信息：数据集为**每张图片**提供了10个句子的描述。详见：[论文[Learning Deep Representations of Fine-Grained Visual Descriptions.]](http://ieeexplore.ieee.org/document/7780382/)。文中使用text based CNN+RNN将句子向量化。

---
### Dogs [数据集地址](http://vision.stanford.edu/aditya86/ImageNetDogs/)

Dogs数据集包含113种常见的狗,包含**图像**、**Boundbox**。其细节在论文[[Novel dataset for Fine-Grained Image Categorization]](http://people.csail.mit.edu/khosla/papers/fgvc2011.pdf)中描述。

- 图像:Dogs包含19499张图片，113个类别的狗狗。数据来源于ImageNet当中所有包括狗的类别，小于200x200的图像被剔除。其中重复、难以清晰辨认的检索结果被剔除，因此Dogs是一个较为理想化的数据集。


- 语义信息：Dogs**不提供属性**，通常使用Label的Word2vec代替，或WordNet的Hierarchical Embedding作为语义信息。

- 数据集特性：Dogs不同于CUB和Flowers，该数据集上，Word2vec并不能很好的描述语义信息，反而BoW(某种狗对于的Wiki文档的BoW)能够较好地描述。参见论文[[Evaluation of output embeddings for fine-grained image classification]](http://ieeexplore.ieee.org/document/7298911/)

---

### Scene UNderstanding (SUN) Attribute [SUN attribute数据集地址](http://cs.brown.edu/~gmpatter/sunattributes.html)


SUN Attribute 是一个场景数据集，包含**图像**和**属性**

SUN是一个大规模数据集[完整SUN数据集地址](http://vision.princeton.edu/projects/2010/SUN/)，用于Zero-shot Learning的是该数据集的一个子集，称为SUN attribute。该子集包含707类不同场景，其场景之间存在3层[树形隶属关系](http://vision.princeton.edu/projects/2010/SUN/hierarchy/)。其细节参见论文：[[The SUN Attribute Database: Beyond Categories for Deeper Scene Understanding]](https://link.springer.com/content/pdf/10.1007%2Fs11263-013-0695-z.pdf)

- 图像：707类，14140张图像，每类20张。

- 语义信息：**每张图像属性**：102维，包含材质、表面性质、光照、档次、空间排布等，**离散取值：0，1/3，2/3，1**。
	- 离散取值的产生方式：3个标注者进行0-1属性标注，对其标注结果取平均得到上述离散取值。

- 适应任务：场景分类、ZSL、Caption、基于文本的search、Image parsing、Image Descriptor。
- 论文启示：
-
	- 讲解了标注的详细过程——如何剔除不可靠的标注。
	- 图11讲解了feature对预测属性的贡献。
	- 5.2第二段重申了属性相关的问题
	- 5.2对图15的解释是很好的定性分析的例子。
	- 6揭示了良好属性的性质：1.相互独立 2.与label一致。
		- 有没有可能做正交变换，得到一组正交基。其物理意义由原基的线性组合系数在Word2Vec空间中找。
	- 6.1.1 最后一段，预测Attr和真实attr之间存在GAP，这又是一个Variance和Bias的问题。
	- 6.1.2 倒数第三段，证实classifier需要知道全部类别的attr
	- 第7节讲解了用于自动标注。
	- 相对属性可能有用 
- ImageNet 21K
- ImageNet 1K


## Datasets for domain adaptation and transfer learning

- *How many times have you been* **struggling to find** the useful datasets?
- *How much time have you been wasting to* **preprocess datasets**?
- *How burdersome is it to compare with other methods*? Will you re-run their code? or there is **No** code?

**Datasets are critical to machine learning**, but *You should focus on* **YOUR** work! So we want to save your time by:

**JUST GIVE THEM TO YOU** so you can **DIRECTLY** use them!

- - -

**If you are tired of repeating the experiments of other methods, you can directly use the [benchmark](https://github.com/jindongwang/transferlearning/blob/master/data/benchmark.md).**

*Only image datasets are listed, text datasets are to be added*

|     Dataset    |        Area        | #Sample |       #Feature      | #Class |   Subdomain  | Reference |
|:--------------:|:------------------:|:-------:|:-------------------:|:------:|:------------:|:--------:|
| [Office+Caltech](#office+caltech) | Object recognition |   2533  | SURF:800 DeCAF:4096 |   10   |  C, A, W, D  |   [1]       |
| [Office-31](#office-31) | Object recognition |   4110  | SURF:800 DeCAF:4096 |   31   |  A, W, D  |   [1]       |
|   [MNIST+USPS](#mnist+usps)   |  Digit recognition |   3800  |         256         |   10   |  USPS, MNIST |    [4]      |
|     [COIL20](#coil20)     | Object recognition |   1440  |         1024        |   20   | COIL1, COIL2 |    [4]      |
|       [PIE](#pie)      |  Face recognition  |  11554  |         1024        |   68   |   PIE1~PIE5  |     [6]     |
|     [VOC2007](#vlsc)    |       Object recognition      |   3376  |      DeCAF:4096     |    5   |       V      |    [8]      |
|     [LabelMe](#vlsc)    |       Object recognition      |   2656  |      DeCAF:4096     |    5   |       L      |    [2]      |
|      [SUN09](#vlsc)     |       Object recognition      |   3282  |      DeCAF:4096     |    5   |       S      |    [9]      |
|   [Caltech101](#vlsc)   |       Object recognition      |   1415  |      DeCAF:4096     |    5   |       C      |    [3]      |
|    [IMAGENET](#imagenet)    |       Object recognition      |   7341  |      DeCAF:4096     |    5   |       I      |     [7]     |
|    [AWA](#animals-with-attributes)    |       Animal recognition      |   30475  |      DeCAF:4096 SIFT/SURF:2000    |    50   |       I      |    [5]      |
|    [Office-Home](#office-home)    |       Object recognition      |   30475  |      Original Images    |    65   |       4 domains      |    [10]      |
|    [Cross-dataset Testbed](#testbed)    |       Image Classification      |   *  |      Decaf7    |    40   |       3 domains     |    [15]      |
|    [ImageCLEF](#imageclef)    |       Image Classification      |   *  |      raw    |    12   |       3 domains     |       [17]  |
|    [VisDA](#VisDA)    |       Image Classification / segmentation      |   *  |      raw    |    12/19   |       3 domains/3 domain     |       [18]  |



- - -


### Office+Caltech

#### Area

Visual object recognition

#### Introduction

Perhaps it is the **most popular** dataset for domain adaptation. Four domains are included: C(Caltech), A(Amazon), W(Webcam) and D(DSLR). In fact, this dataset is constructed from two datasets: Office-31 (which contains 31 classes of A, W and D) and Caltech-256 (which contains 256 classes of C). There are just 10 common classes in both, so the Office+Caltech dataset is formed.

Even for the same category, the data distribution of different domains is exactly different. The following picture [1] indicates this fact by the monitor images from 4 domains.

![](https://raw.githubusercontent.com/jindongwang/transferlearning/master/png/domain%20_adaptation.png)

#### Features

There are ususlly two kinds of features: SURF and DeCAF6. They are with the same number of samples per domain, resulting 2533 samples in total:

- C: 1123
- A: 958
- W: 295
- D: 157

And the dimension of features is:

- For SURF: 800
- For DeCAF6: 4096

#### Copyright

This dataset was first introduced by Gong et al. [1]. I got the SURF features from the website of [1], while DeCAF features from [10].

See benchmark results of many popular methods [here(SURF)](https://github.com/jindongwang/transferlearning/blob/master/doc/benchmark.md#officecaltech-surf) and [here(DeCaf)](https://github.com/jindongwang/transferlearning/blob/master/doc/benchmark.md#officecaltech10-decaf6).

#### Download

Download Office+Caltech original images [[Baiduyun](https://pan.baidu.com/s/14JEGQ56LJX7LMbd6GLtxCw)]

Download Office+Caltech SURF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZFrXk7ZifluxAGy3gjdstJBIcJv3fORIkHk)|[Baiduyun](https://pan.baidu.com/s/1bp4g7Av)]

Download Office+Caltech DeCAF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZprXk7Z1OmGWUuYioSJbWx3jWeCAhom5FPy)|[Baiduyun](https://pan.baidu.com/s/1nvn7eUd)]


- - -

### Office-31

This is the full Office dataset, which contains 31 categories from Amazon, webcam and DSLR.

See benchmarks on Office-31 datasets [here](https://github.com/jindongwang/transferlearning/blob/master/doc/benchmark.md#office-31).

#### Download

[Download Office-31 raw images](https://pan.baidu.com/s/1o8igXT4)

[Download Office-31 DeCAF6 and DeCAF7 features](https://pan.baidu.com/s/1o7XrAzw)

[Download Office-31 DeCAF features by Frame](https://pan.baidu.com/s/1i5KkNxb)

[Download Office-31 SURF features](https://pan.baidu.com/s/1kU6tv4F)

- - -

### MNIST+USPS

**Area** Handwritten digit recognition

It is also popular. It contains randomly selected samples from MNIST and USPS. Then the source and target domains are constructed using each other.

Download MNIST+USPS SURF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZHrXk7ZdIfYsBuRVtkPoAqvxL87qhgNw10V)|[Baiduyun](https://pan.baidu.com/s/1c8mwdo)]


- - -


### COIL20

**Area** Object recognition

It contains 20 classes. There are two datasets extracted: COIL1 and COIL2.

Download COIL20 SURF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZzrXk7ZQw37wqJsNSJVzN1DzH0FH7e3tOYV)|[Baiduyun](https://pan.baidu.com/s/1pKM1VCn)]


- - -


### PIE

**Area** Facial recognition

It is a relatively large dataset with many classes.

Download PIE SURF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZRrXk7ZwvHA9LPSyqSz7WSlECK5A0hNMR6X)|[Baiduyun](https://pan.baidu.com/s/1o8KFgtO)]


- - -



### VLSC

**Area** Image classification

It contains four domains: V(VOC2007), L(LabelMe), S(SUN09) and C(Caltech). There are 5 classes: 'bird', 'car', 'chair', 'dog', 'person'.

Download the VLSC DeCAF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZ8rXk7ZORx8jhQ6CzyItAp2qQHmMbFiyRW7)|[Baiduyun](https://pan.baidu.com/s/1nuNiJ0l)]


- - -



### IMAGENET

It is selected from imagenet challange.

Download the IMAGENET DeCAF dataset [[pCloud](https://my.pcloud.com/publink/show?code=kZ8rXk7ZORx8jhQ6CzyItAp2qQHmMbFiyRW7)|[Baiduyun](https://pan.baidu.com/s/1nuNiJ0l)]


- - -


### Animals-with-Attributes

Download the SURF/SIFT/DeCAF features [[pCloud](https://my.pcloud.com/publink/show?code=kZbrXk7ZYAgHIKa0Qa5W1Gi9VXbnMhzIo9GX)|[Baiduyun](https://pan.baidu.com/s/1mi7RYQW)]

- - -

### Office-Home

This is a **new** dataset released at CVPR 2017. It contains 65 kinds of objects crawled from the web. The main research goal is for domain adatpation algorithms benchmark.

The project home page is: http://hemanthdv.org/OfficeHome-Dataset/, the dataset can be downloaded there.

- - -

### Cross-dataset Testbed

This is a Decaf7 based cross-dataset image classification dataset. It contains 40 categories of images from 3 domains: 3,847 images in Caltech256(C), 4,000 images in ImageNet(I), and 2,626 images for SUN(S).

[Download the Cross-dataset testbed](https://pan.baidu.com/s/1o8MeVUi)

- - -

### ImageCLEF

This is a dataset from ImageCLEF 2014 challenge.

[Download the ImageCLEF dataset](https://pan.baidu.com/s/1lx2u1SMlSamsHnAPWrAHWA)

- - -

### VisDA

This is a dataset from VisDA 2017 challenge. It contains two subdatasets, one for image classification tasks and the other for image segmentation tasks.

[Download the VisDA-classification dataset](http://csr.bu.edu/ftp/visda17/clf/)

[Download the VisDA-segmentation dataset](http://csr.bu.edu/ftp/visda17/seg/)

- - -
 
For more image datasets, please refer to https://sites.google.com/site/crossdataset/home/files

# Benchmark

This file contains some benchmark results of popular transfer learning (domain adaptation) methods gathered from published papers. Right now there are only results of the most popular Office+Caltech10 datasets. You're welcome to add more results.

The full list of datasets can be found in [datasets](https://github.com/jindongwang/transferlearning/blob/master/data/dataset.md).

## Office+Caltech SURF

| **Dim** | **Method** | **C-A** | **C-W** | **C-D** | **A-C** | **A-W** | **A-D** | **W-C** | **W-A** | **W-D** | **D-C** | **D-A** | **D-W** |
|:---:|:--------:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| 100 | PCA+1NN | 36.95 | 32.54 | 38.22 | 34.73 | 35.59 | 27.39 | 26.36 | 31 | 77.07 | 29.65 | 32.05 | 75.93 |
| 100 | GFK+1NN | 41.02 | 40.68 | 38.85 | 40.25 | 38.98 | 36.31 | 30.72 | 29.75 | 80.89 | 30.28 | 32.05 | 75.59 |
| 100 | TCA+1NN | 38.2 | 38.64 | 41.4 | 37.76 | 37.63 | 33.12 | 29.3 | 30.06 | 87.26 | 31.7 | 32.15 | 86.1 |
| 100 | TSL+1NN | 44.47 | 34.24 | 43.31 | 37.58 | 33.9 | 26.11 | 29.83 | 30.27 | 87.26 | 28.5 | 27.56 | 85.42 |
| 100 | JDA+1NN | 44.78 | 41.69 | 45.22 | 39.36 | 37.97 | 39.49 | 31.17 | 32.78 | 89.17 | 31.52 | 33.09 | 89.49 |
| 100 | UDA+1NN | 47.39 | 46.56 | 48.41 | 41.41 | 43.05 | 42.04 | 32.41 | 34.45 | 91.08 | 34.19 | 34.24 | 90.85 |
| 30 | SA+1NN | 49.27 | 40 | 39.49 | 39.98 | 33.22 | 33.76 | 35.17 | 39.25 | 75.16 | 34.55 | 39.87 | 76.95 |
| 30 | SDA+1NN | 49.69 | 38.98 | 40.13 | 39.54 | 30.85 | 33.76 | 34.73 | 39.25 | 75.8 | 35.89 | 38.73 | 76.95 |
| 30 | GFK+1NN | 46.03 | 36.95 | 40.76 | 40.69 | 36.95 | 40.13 | 24.76 | 27.56 | 85.35 | 29.3 | 28.71 | 80.34 |
| 30 | TCA+1NN | 45.82 | 31.19 | 34.39 | 42.39 | 36.27 | 33.76 | 29.39 | 28.91 | 89.17 | 30.72 | 31 | 86.1 |
| 30 | JDA+1NN | 45.62 | 41.69 | 45.22 | 39.36 | 37.97 | 39.49 | 31.17 | 32.78 | 89.17 | 31.52 | 33.09 | 89.49 |
| 30 | TJM+1NN | 46.76 | 38.98 | 44.59 | 39.45 | 42.03 | 45.22 | 30.19 | 29.96 | 89.17 | 31.43 | 32.78 | 85.42 |
| 30 | SCA+1NN | 45.62 | 40 | 47.13 | 39.72 | 34.92 | 39.49 | 31.08 | 29.96 | 87.26 | 30.72 | 31.63 | 84.41 |
| 30 | JGSA+1NN | 53.13 | 48.47 | 48.41 | 41.5 | 45.08 | 45.22 | 33.57 | 40.81 | 88.54 | 30.28 | 38.73 | 93.22 |
| 20 | PCA+1NN | 36.95 | 32.54 | 38.22 | 34.73 | 35.59 | 27.39 | 26.36 | 29.35 | 77.07 | 29.65 | 32.05 | 75.93 |
| 20 | FSSL+1NN | 35.88 | 32.32 | 37.53 | 33.91 | 34.35 | 26.37 | 25.85 | 29.53 | 76.79 | 27.89 | 30.61 | 74.99 |
| 20 | TCA+1NN | 45.82 | 30.51 | 35.67 | 40.07 | 35.25 | 34.39 | 29.92 | 28.81 | 85.99 | 32.06 | 31.42 | 86.44 |
| 20 | GFK+1NN | 41.02 | 40.68 | 38.85 | 40.25 | 38.98 | 36.31 | 30.72 | 29.75 | 80.89 | 30.28 | 32.05 | 75.59 |
| 20 | TJM+1NN | 46.76 | 38.98 | 44.59 | 39.45 | 42.03 | 45.22 | 30.19 | 29.96 | 89.17 | 31.43 | 32.78 | 85.42 |
| 20 | VDA+1NN | 46.14 | 46.1 | 51.59 | 42.21 | 51.19 | 48.41 | 27.6 | 26.1 | 89.18 | 31.26 | 37.68 | 90.85 |
| no | 1NN | 23.7 | 25.76 | 25.48 | 26 | 29.83 | 25.48 | 19.86 | 22.96 | 59.24 | 26.27 | 28.5 | 63.39 |
| no | SVM | 55.64 | 45.22 | 43.73 | 45.77 | 42.04 | 39.66 | 31.43 | 34.76 | 82.8 | 29.39 | 26.62 | 63.39 |
| no | LapSVM | 56.27 | 45.8 | 43.73 | 44.23 | 42.74 | 39.79 | 31.99 | 34.77 | 83.43 | 29.49 | 27.37 | 64.31 |
| no | TKL | 54.28 | 46.5 | 51.19 | 45.59 | 49.04 | 46.44 | 34.82 | 40.92 | 83.44 | 35.8 | 40.71 | 84.75 |
| no | KMM | 48.32 | 45.78 | 53.53 | 42.21 | 42.38 | 42.72 | 29.01 | 31.94 | 71.98 | 31.61 | 32.2 | 72.88 |
| no | DTMKL | 54.33 | 42.04 | 44.74 | 45.01 | 36.94 | 40.85 | 32.5 | 36.53 | 88.85 | 32.1 | 34.03 | 81.69 |
| no | SKM+SVM | 53.97 | 43.31 | 43.05 | 44.7 | 37.58 | 42.37 | 31.34 | 35.07 | 89.81 | 30.37 | 30.27 | 81.02 |

**Results are coming from:**

- 1~5：[4]
- 6~15: [11]
- 16~21: [12]
- 22~28: [13]

- - -

## Office+Caltech10 Decaf6

Luckily, there is one article [16] that gathers the results of many popular methods on Decaf6 features. The benchmark is as the following image from that article:

![](https://raw.githubusercontent.com/jindongwang/transferlearning/master/png/result_office_caltech_decaf.jpg)

## Office-31

More and more researches chose to compare the accuracy on Office-31 datasets. Here is the comparison of both traditional and deep methods:

| Method | A - D | A - W | D - A | D - W | W-A | W-D | Average |
|:--------------:|:-----:|:-----:|:-----:|:-----:|:----:|:----:|:-------:|
| SVM | 55.7 | 50.6 | 46.5 | 93.1 | 43.0 | 97.4 | 64.4 |
| TCA | 45.4 | 40.5 | 36.5 | 78.2 | 34.1 | 84.0 | 53.1 |
| GFK | 52.0 | 48.2 | 41.8 | 86.5 | 38.6 | 87.5 | 59.1 |
| SA | 46.2 | 42.5 | 39.3 | 78.9 | 36.3 | 80.6 | 54.0 |
| DANN | 34.0 | 34.1 | 20.1 | 62.0 | 21.2 | 64.4 | 39.3 |
| CORAL | 57.1 | 53.1 | 51.1 | 94.6 | 47.3 | 98.2 | 66.9 |
| AlexNet | 63.8 | 61.6 | 51.1 | 95.4 | 49.8 | 99.0 | 70.1 |
| ResNet | 68.9 | 68.4 | 62.5 | 96.7 | 60.7 | 99.3 | 76.1 |
| DDC | 64.4 | 61.8 | 52.1 | 95.0 | 52.2 | 98.5 | 70.6 |
| DAN | 67.0 | 68.5 | 54.0 | 96.0 | 53.1 | 99.0 | 72.9 |
| RTN | 71.0 | 73.3 | 50.5 | 96.8 | 51.0 | 99.6 | 73.7 |
| RevGrad | 72.3 | 73.0 | 53.4 | 96.4 | 51.2 | 99.2 | 74.3 |
| DCORAL | 66.4 | 66.8 | 52.8 | 95.7 | 51.5 | 99.2 | 72.1 |
| DUCDA | 68.3 | 68.3 | 53.6 | 96.2 | 51.6 | 99.7 | 73.0 |
| JAN(AlexNet) | 71.8 | 74.9 | 58.3 | 96.6 | 55.0 | 99.5 | 76.0 |
| JAN-A(AlexNet) | 72.8 | 75.2 | 57.5 | 96.6 | 56.3 | 99.6 | 76.3 |
| JAN(ResNet) | 84.7 | 85.4 | 68.6 | 97.4 | 70.0 | 99.8 | 84.3 |
| JAN-A(ResNet) | 85.1 | 86.0 | 69.2 | 96.7 | 70.7 | 99.7 | 84.6 |

