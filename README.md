# Adversarial Pyramid Progressive Attention U-Net
This repository contains the implementation of the paper <a href="https://link.springer.com/chapter/10.1007/978-3-030-32692-0_18">Semi-supervised Multi-task Learning with Chest X-Ray Images.</a> This propose adversarial pyramid progressive attention u-net (APPAU-Net) model for jointly performing segmentation of lungs and classification of diseases from chest radiographs. 


## Model
The APPAU-Net model consists of two major building blocks, a segmentor \mathbf{S} and a discriminator \mathbf{D} (Figure). \mathbf{S} primarily performs segmentation prediction $\hat{y}$ from a given image \mathbf{x}. \mathbf{S} consists of a pyramid encoder and a progressive attention-gated decoder modifying a U-Net. The \mathbf{S} network receives the image input \mathbf{x} at different scales in different stages of the encoder. The segmentor \mathbf{S} predicts segmentation $\hat{y}$ from a given image \mathbf{x}. The discriminator \mathbf{D} predicts the class label $\hat{z}$ from image-real label pair $(x, y); z = 0\dots n$ are real disease classes and $z = n + 1$ is an extra class denoting the prediction.

![](appaunet-final.png?raw=true)



## Dataset
Three chest X-Ray datasets were used in the experiments:<br>
<a href="http://academictorrents.com/details/ac786f74878a5775c81d490b23842fd4736bfe33">Montgomery County X-ray Set</a> contains 80 normal and 58 abnormal X-Rays with manifestations of tuberculosis. [1][2] <br>
<a href="http://academictorrents.com/details/462728e890bd37c05e9439c885df7afc36209cc8">Shenzhen Hospital X-ray Set</a> provides 340 normal X-Rays and 275 abnormal X-Rays with various extent of tuberculosis. [1][2] <br>
<a href="http://db.jsrt.or.jp/eng.php">Japanese Society of Radiological Technology (JSRT)</a> includes 154 nodule and 93 non-nodule images.[3]


## How to Use
Select the loss function and the network from the following options for the segmentation-only task. While for multi-tasking, the networks are fixed `Pyramid Progressive Attention U-Net` as the Segmentor S and a conv-net as the Discriminator D.

### Single Task: Segmentation Only
##### Choice of Loss Functions
<ol>
  <li>XE Loss</li>
  <li>Tversky Loss</li>
  <li>Dice Loss</li>
  <li>KL-Tversky Loss</li>
</ol>

##### Choice of Segmentation Networks
<ol>
  <li>U-Net</li>
  <li>Pyramid U-Net</li>
  <li>Progressive U-Net</li>
  <li>Attention U-Net</li>
  <li>Pyramid Progressive U-Net</li>
  <li>Pyramid Attention U-Net</li>
  <li>Progressive Attention U-Net</li>
  <li>Pyramid Progressive Attention U-Net</li>
</ol>

### Multi-Task
##### Choice of Network
<ol>
  <li>Adversarial Pyramid Progressive Attention U-Net</li>
</ol>

##### Choice of Loss Functions
<ol>
  <li>Tversky Loss</li>
  <li>XE-Tversky Loss</li>
  <li>KL-Tversky Loss</li>
</ol>



## Citation
Please cite:

Imran AAZ, Terzopoulos D (2019) Semi-supervised Multi-task Learning with Chest X-Ray Images. In: Suk HI., Liu M., Yan P., Lian C. (eds) Machine Learning in Medical Imaging. MLMI 2019. Lecture Notes in Computer Science, vol 11861. Springer, Cham

```
@inproceedings{abdullah2019semi,
title={Semi-supervised Multi-task Learning with Chest X-Ray Images},
author={Abdullah-Al-Zubaer Imran, and Terzopoulos, Demetri},
booktitle={Machine Learning in Medical Imaging: 10th International Workshop, MLMI 2019, Held in Conjunction with MICCAI 2019, Shenzhen, China, October 13, 2019, Proceedings},
volume={11861},
pages={151},
year={2019},
organization={Springer Nature}
}
```

## References
1. Candemir S, Jaeger S, Musco J, Xue Z, Karargyris A, Antani SK, Thoma GR, Palaniappan K. Lung segmentation in chest radiographs using anatomical atlases with nonrigid registration. IEEE Trans Med Imaging. 2014 Feb;33(2):577-90. doi: 10.1109/TMI.2013.2290491. PMID: 24239990

2. Jaeger S, Karargyris A, Candemir S, Folio L, Siegelman J, Callaghan FM, Xue Z, Palaniappan K, Singh RK, Antani SK. Automatic tuberculosis screening using chest radiographs. IEEE Trans Med Imaging. 2014 Feb;33(2):233-45. doi: 10.1109/TMI.2013.2284099. PMID: 24108713

3. Shiraishi J, Katsuragawa S, Ikezoe J, Matsumoto T, Kobayashi T, Komatsu K, Matsui M, Fujita H, Kodera Y, and Doi K.: Development of a digital image database for chest radiographs with and without a lung nodule: Receiver operating characteristic analysis of radiologists’ detection of pulmonary nodules. AJR 174; 71-74, 2000



