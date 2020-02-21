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
Code references:
- https://github.com/pykao/BraTS2018-tumor-segmentation
- https://github.com/China-LiuXiaopeng/BraTS-DMFNet
- https://github.com/shiba24/3d-unet
- https://github.com/xf4j/brats18/tree/master/models


|                    | Technique                      | Result | Note |
|--------------------|--------------------------------|--------|------|
| Original           | Original  + Normalize          |        |      |
| Preprocessing      |                                |        |      |
|                    | N4ITK                          |        |      |
|                    | multiscale                     |        |      |
|                    | domain adaption                |        |      |
|                    | other transforms               |        |      |
| Model Architecture |                                |        |      |
|                    | VAE                            |        |      |
|                    | Cascade end-to-end             |        |      |
|                    | Cascade seperately             |        |      |
|                    | ASPP                           |        |      |
|                    | Increase network width         |        |      |
|                    | Attention with SE block        |        |      |
|                    | parallel model training (7)    |        |      |
| Loss Function      |                                |        |      |
|                    | Focal loss                     |        |      |
|                    | Soft loss                      |        |      |
| Post processing    |                                |        |      |
|                    | CRF                            |        |      |

## Application of Medical Image Overview
I do a summarization of application from MICCAI 2019 papers [here](./research/application_medical_overview.md)
