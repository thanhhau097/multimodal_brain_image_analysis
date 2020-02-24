# Multimodal Brain Tumor Segmentation 

## [Medical Application Overview](./research/application_medical_overview.md)
## [Documents](./research/documents.md)
## [Literature Review](./research/literature_review.md)

## IDEA
- Use techniques of previous research
- Design new loss function (using the idea of previous paper)
- Reduce size of models
- Handle the open problems of previous research
- Design new model: cascaded, because they are overlap

## Experiments
My code is located at: https://github.com/thanhhau097/pytorch-3dunet which was folked from https://github.com/wolny/pytorch-3dunet with modification.

Code references:
- https://github.com/pykao/BraTS2018-tumor-segmentation: models, criterions, transforms [[1](https://github.com/pykao/BraTS2018-tumor-segmentation)]
- https://github.com/MIC-DKFZ/BraTS2017: dataset
- https://github.com/China-LiuXiaopeng/BraTS-DMFNet: ***main***
- https://github.com/xf4j/brats18/tree/master/models: (pre_processingN4ITK)
- https://github.com/wolny/pytorch-3dunet [[2](https://github.com/wolny/pytorch-3dunet)]

### Step-by-Step
1. Train model with only WT label, try to improve it.
2. Train model will all labels, in parallel/separate-cascade/end2end cascade


|                    | Technique                      | UNet[1]| ResUnet | UNet[2]| Note |
|--------------------|--------------------------------|--------|---------|--------|------|
| Original           | Original  + Normalize          |        |         |        |      |
| Preprocessing      |                                |        |         |        |      |
|                    | N4ITK                          |        |         |        |      |
|                    | multiscale                     |        |         |        |      |
|                    | domain adaption                |        |         |        |      |
|                    | other transforms               |        |         |        |      |
| Model Architecture |                                |        |         |        |      |
|                    | VAE                            |        |         |        |      |
|                    | Cascade end-to-end             |        |         |        |      |
|                    | Cascade seperately             |        |         |        |      |
|                    | ASPP                           |        |         |        |      |
|                    | Increase network width         |        |         |        |      |
|                    | Attention with SE block        |        |         |        |      |
|                    | parallel model training (7)    |        |         |        |      |
| Loss Function      |                                |        |         |        |      |
|                    | Focal loss                     |        |         |        |      |
|                    | Soft loss                      |        |         |        |      |
| Post processing    |                                |        |         |        |      |
|                    | CRF                            |        |         |        |      |

## Application of Medical Image Overview
I do a summarization of application from MICCAI 2019 papers [here](./research/application_medical_overview.md)
      |
