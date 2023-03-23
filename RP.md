# Research Proposal

## Background

Brain MRI is an important method for doctor to diagnose disease. Using deep neural network and one split test method proposed by this
[paper](https://arxiv.org/abs/2103.04985)
may help us find out key region that indicates the disease and calculate its significance.

## Dataset

Collect dataset from 
[kaggle_competition](https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection).
This dataset consist of 98 MRI images of healthy brain and 155 MRI images of brain with tumor. They are labeled as 'no' and 'yes'. Images from dataset appear like this:

![pic](https://storage.googleapis.com/kagglesdsdata/datasets/165566/377107/yes/Y114.JPG?X-Goog-Algorithm=GOOG4-RSA-SHA256&X-Goog-Credential=databundle-worker-v2%40kaggle-161607.iam.gserviceaccount.com%2F20230212%2Fauto%2Fstorage%2Fgoog4_request&X-Goog-Date=20230212T110652Z&X-Goog-Expires=345600&X-Goog-SignedHeaders=host&X-Goog-Signature=09e42b628e378360b55394457697cdfb96ee83e25225649865b0c229f633cd3a28997c5842933a15afcd26c47e235e0c079f33e71517b67fcecbf1ee3eda622ea454c5c5349887fca9e3f1c576b1c4a6cd3de0d11e3e8ca1c5a8a77fb319d63e98dbaba07e064a7f838416eee586e989f53ce58bdc2ea171e6ad20087dc464cabcd0ba067e5f000d55efe7f76bb0a8510b7a0f298c1d988ee6e539021d0ce66bac8f63267bd0c3e87662e51455fbe2447796945120381010d561f9e5873e491cad3f9323ac1ae6b194b30c2fbd690418683929ccde7137507560592552d9fa1b722ae5b219ab4ff3549b0b053cd3daeea1a4895166b7f9d0748eda03a8811bd2 "Brain MRI")

## Research Method

By applying dnn-test method proposed in the paper, we can calculate the p-value of selected region, which represent the sigificance. Hopefully, I will apply algorithm to detect landmark so that the program can automatically recognize tumor area. Idealy the project will help us find out tumor region and calculate the significance of the region, which provide evidence for diagnosis.
