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

### Difference between (3) and (5), what things in (3) should be integrate into (5)?
- Customized preprocessing data

### Step-by-Step

1. Load pretrained DMF model and check loss, dice 
2. train DMF model to check if we can get same result
3. Integrate into 3dUnetPytorch repo.
4. Start training using 3dUnetPytorch repo.

### Other plan
1. Train model, try to improve it 
2. with original model, try to modify loss function, preprocessing data,... to get best loss function and data.
3. With modified architecture


|                    | Technique                      |Org Unet| TBD     | TBD    | Note |
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
