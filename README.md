# Multimodal Brain Tumor Segmentation 

## [Medical Application Overview](./research/application_medical_overview.md) (optional, no need to read)
## [Documents](./research/documents.md)
## [Literature Review](./research/literature_review.md)

## IDEA
- Design new model: cascaded, because they are overlap
- Multi-stage DMF
- Apply variant of UNet architecture

## Experiments
My code is located at: https://github.com/thanhhau097/pytorch-3dunet which was folked from https://github.com/wolny/pytorch-3dunet with modification.

Code references:
- ~~https://github.com/pykao/BraTS2018-tumor-segmentation: models, criterions, transforms [[1](https://github.com/pykao/BraTS2018-tumor-segmentation)]~~
- ~~https://github.com/MIC-DKFZ/BraTS2017: dataset~~
- https://github.com/China-LiuXiaopeng/BraTS-DMFNet: ***main*** (3)
- https://github.com/xf4j/brats18/tree/master/models: (pre_processingN4ITK)
- https://github.com/wolny/pytorch-3dunet [[2](https://github.com/wolny/pytorch-3dunet)] (5)

# TODO
1. Training with DMFNet with k-fold
2. Modify architecture 
3. Try other loss function

## Application of Medical Image Overview
I do a summarization of application from MICCAI 2019 papers [here](./research/application_medical_overview.md)
      |
