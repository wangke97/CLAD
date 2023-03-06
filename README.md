### CLAD: A Contrastive Learning based Approach for Background Debiasing

This repository contains codes for [CLAD: A Contrastive Learning based Approach for Background Debiasing (BMVC 2022)](https://arxiv.org/abs/2210.02748). 

We propose a contrastive learning framework, CLAD, for reducing the effect of image background in image classification. Through design of contrastive samples, CLAD is trained to encourage semantic focus on object foregrounds and penalize using features from the background. Please follow the following steps.

#### Setup

**Install requirements**: ```pip install -r requirements.txt```

**Download datasets**:    We evaluate our method on the [ImageNet-9](https://github.com/MadryLab/backgrounds_challenge) dataset, and created two foreground sets, with either GrabCut or U2-Net, by segmentation on the original images (for the train set ONLY). The dataset can be downloaded [here](https://drive.google.com/file/d/1FMnN8wd-XmnScV6mwWIeKXXnK0-zgoBL/view?usp=share_link), and unzipped to the datasets directiory. 

Note that if you are using the original ImageNet-9 dataset, we suggest you to generate the foreground segmentations yourself with either [GrabCut](https://docs.opencv.org/3.4/d8/d83/tutorial_py_grabcut.html) or [U2-Net](https://github.com/xuebinqin/U-2-Net) as we described in the paper rather than directly use the one in ImageNet-9 dataset, as the original ImageNet-9 dataset is saved in JPEG version which lowers the image quality and introduces noise in inpaiting foreground when generating positive samples. 

#### Usage

##### Train and evaluate model with the following commands.

* Train baseline:
```python main_clad_bg.py --with_con_loss 0```
* Train CLAD:
```python main_clad_bg.py --with_con_loss 1```
* Train CLAD+:
```python main_clad_bg.py --with_con_loss 1 --with_pos_loss 1```