# AIigatou_AI
> Team #15 in #AI_Artathon 2020

In this project I'll explaine our pipeline from the preprocessing of our datasets, training CycleGAN model, till we finaly upscaled the output and discared the noise. 

## Table of Contents

>`Preprocessing`
- [Dataset Segmentation](#segmentation)
- [Dataset Outlines](#outlines)
- [Dataset Augmentation](#augmentation)

>`Model Training`
- [CycleGAN](#training)

>`Postprocessing`
- [Upscale](#upscale)
- [Noise Reduction](#noise)


>`Website`
- [Try it Out](#features)

>`Info`
- [Team](#team)
- [FAQ](#faq)

## Datasets Preprocessing
In the cycleGAN archetucture, there are two GAN models. Each GAN model need to be trained on distinguished dataset inorder to come with something new. Since my team and I want to work with our own dataset, we came up with a way to have differnet representation of our dataset. We took our dataset, applay segmentation to it, then took the segmented dataset, then took the outlines of it. This may look similar to the pix2pix method b`ut we did not paire the images`. Simply we augmented the two datasetes after we took the outlines of the outlies of the segmented data.

### Segmentation 
| Original | Segmententation 3 | Segmentation 2 |
| ------------- | ------------- | ------------- |
|![](O_I_01.png "Original Image")| ![](S_2C_I_01.png "Segmented to 3 colors")| ![](S_1C_I_01.png "Segmented to 2 colors")|

### Outlines 
| 3 Colors Segment | Outline | 2 Colors Segment | Outline |
| ------------- | ------------- | ------------- |------------- |
| ![](S_2C_I_01.png "Segmented to 3 colors")|  ![](L_S_2C_I_01.png "Outline from 3 Colors Segment")| ![](S_1C_I_01.png "Segmented to 2 colors")| ![](L_S_1C_I_01.png "Outline from 2 Colors Segment")|


### Augmentation 
| 3 Colors Segment | Outline | 2 Colors Segment | 
| ------------- | ------------- | ------------- |
| ![](S_2C_I_01.png "Segmented to 3 colors")|  ![](L_S_2C_I_01.png "Outline from 3 Colors Segment")| ![](S_1C_I_01.png "Segmented to 2 colors")|
| ![](S_2C_I_01.png "Segmented to 3 colors")|  ![](L_S_2C_I_01.png "Outline from 3 Colors Segment")| ![](S_1C_I_01.png "Segmented to 2 colors")|

## Model Training

### Training

## Postprocessing

### Upscale
### Noise
