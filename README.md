# Multimodal Brain Tumor Segmentation 

## [Medical Application Overview](./research/application_medical_overview.md) (optional, no need to read)
## [Documents](./research/documents.md)
## [Literature Review](./research/literature_review.md)

## IDEA
Original Result:  0.79574	0.89777	0.84114
Compare to paper: 80.12       90.62       84.54

- Design new model: cascaded, because they are overlap
- Multi-stage DMF
- Apply variant of UNet architecture, compare to UNet architecture
- Consider post-processing step to ignore 0.0 results.

| Paper                                                                                                                                                                                    | What can be handled?                                                                                                                                                                                                                                                                      | Methods                                                                                               | Results | Note             |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|---------|------------------|
| UNet++: A Nested U-Net Architecture for Medical Image Segmentation                                                                                                                       | The re-designed skip pathways aim at reducing the semantic gap between the feature maps of the encoder and decoder sub-networks. We argue that the optimizer would deal with an easier learning task when the feature maps from the decoder and encoder networks are semantically similar | nested and dense skip connections.                                                                    |    0.81131	0.90011	0.84194     | memory consuming <br> epoch 599 |
| Attention U-Net: Learning Where to Look for the Pancreas                                                                                                                                 | suppress irrelevant regions in an input image while highlighting salient features                                                                                                                                                                                                         | attention gate module                                                                                 |         |                  |
| Concurrent Spatial and Channel ‘Squeeze & Excitation’ in Fully Convolutional Networks                                                                                                    | recalibrating the feature maps adaptively, to boost meaningful features, while suppressing weak ones. We draw inspiration from the recently proposed squeeze & excitation (SE) module for channel recalibration of feature maps for image clas- sification                                | SE modules                                                                                            |         |                  |
| MultiResUNet : Rethinking the U-Net Architecture for Multimodal Biomedical Image Segmentation                                                                                            | Semantic Gap between the Corresponding Levels of Encoder-Decoder                                                                                                                                                                                                                          | MultiRes blocks                                                                                       |         |                  |
| A NOVEL FOCAL TVERSKY LOSS FUNCTIONWITH IMPROVED ATTENTION U-NET FOR LESION SEGMENTATION                                                                                                 | highly imbalanced data and small ROI segmentation                                                                                                                                                                                                                                         | attention gate, focal Tversky loss function, multiscale input                                         |         |                  |
| Dense Multi-path U-Net for Ischemic Stroke Lesion Segmentation in Multiple Image Modalities<br>IVD-Net: Intervertebral disc localization and segmentation in MRI with a multi-modal UNet | instead of combining the available image modalities at the input, each of them is processed in a different path to better exploit their unique information.                                                                                                                               | separate input, dense connection, inception module                                                    |         |                  |
| A Hierarchical Probabilistic U-Net for Modeling Multi-Scale Ambiguities                                                                                                                  | In order to learn a flexible distribution that can account for multiple scales of variations                                                                                                                                                                                              | a conditional variational auto-encoder (cVAE) that uses a hierarchical latent space decomposition. We |         |                  |
| ResUNet-a: a deep learning framework for semantic segmentation of remotely sensed data                                                                                                   | better convergence properties and behaves well even under the presence of highly imbalanced classes                                                                                                                                                                                       | novel variant loss function                                                                           |         |                  |
|                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                           |                                                                                                       |         |                  |

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

| Model |    |  1 |    |    |  2 |    |    |  3 |    |    |  4 |    |    |  5 |    |    | Average |    |
|:-----:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:-------:|:--:|
|       | WT | TC | ET | WT | TC | ET | WT | TC | ET | WT | TC | ET | WT | TC | ET | WT |    TC   | ET |
|  DMF  |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |    |         |    |

## Application of Medical Image Overview
I do a summarization of application from MICCAI 2019 papers [here](./research/application_medical_overview.md)
      |
