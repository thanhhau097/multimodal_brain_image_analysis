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
| Modified DMF Net                                                                                                                       | Use MFUnit in skip connections | MFUnit                                                                    |    0.81131	0.90011	0.84194     | memory consuming (6M parameters), just use MF Unit in skip connection <br> epoch 599 [model](https://us-west-2.console.aws.amazon.com/s3/buckets/scsk-data/ocr_data/output/lionel/sagemaker-test-2020-03-05-02-32-11-026/output/?region=us-west-2&tab=overview) |
| UNet++: A Nested U-Net Architecture for Medical Image Segmentation                                                                                                                       | The re-designed skip pathways aim at reducing the semantic gap between the feature maps of the encoder and decoder sub-networks. We argue that the optimizer would deal with an easier learning task when the feature maps from the decoder and encoder networks are semantically similar | nested and dense skip connections.                                                                    |         | memory consuming (too deep) |
| Attention U-Net: Learning Where to Look for the Pancreas                                                                                                                                 | suppress irrelevant regions in an input image while highlighting salient features                                                                                                                                                                                                         | attention gate module                                                                                 |         |                  |
| Concurrent Spatial and Channel ‘Squeeze & Excitation’ in Fully Convolutional Networks                                                                                                    | recalibrating the feature maps adaptively, to boost meaningful features, while suppressing weak ones. We draw inspiration from the recently proposed squeeze & excitation (SE) module for channel recalibration of feature maps for image clas- sification                                | SE modules                                                                                            |         |                  |
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

|                 Model                 |  Params  | FLOPS | Dice ET | Dice WT | Dice TC | Hausdorff95 ET | Hausdorff95 WT | Hausdorff95 TC |
|:-------------------------------------:|:--------:|:-----:|:-------:|:-------:|:-------:|:--------------:|:--------------:|:--------------:|
|                 DMFNet                |  3880000 |       |  80.12 (79.574)  |  **90.62** (89.777)  |  **84.54** (84.114)  |      3.06      |      4.66      |      6.44      |
|  DMFNet + MFUnit in skip connections |  6871490 |       |  **81.131** |  90.011 |  84.194 |                |                |                |
| DMFNet + DMFUnit in skip connections | 11300299 |       |  79.661 |  89.896 | 84.189  |                |                |                |
|       Attention Unet   (one gate)    | 10881302 |       |         |         |         |                |                |                |
|       Attention Unet   (single module)    | 11226614 |       |         |         |         |                |                |                |
|       Attention Unet   (multi module)    | 12345818 |       |         |         |         |                |                |                |
|        DMFNet + csSE                  |  4110041 |       |         |         |         |                |                |                |
|   DMFNet + PE (same paper with csSE)  | 4108946  |       |         |         |         |                |                |                |
|      DMFNet + attention gate, focal Tversky loss function  |          |       |         |         |         |                |                |                |
|      DMFNet + separate inputs                 |          |       |         |         |         |                |                |                |
|                 DMFNet + multiscale inputs                               |          |       |         |         |         |                |                |                |
|                                       |          |       |         |         |         |                |                |                |
## Application of Medical Image Overview
I do a summarization of application from MICCAI 2019 papers [here](./research/application_medical_overview.md)
      |
