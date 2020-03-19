# AIigatou_AI
> Team #15 in #AI_Artathon 2020

In this project I'll explaine our pipeline from the preprocessing of our datasets, training CycleGAN model, till we finaly upscaled the output and discared the noise. **checkout our original [dataset](https://drive.google.com/drive/folders/1KKrFin2dVa_hObgy3ihSyd_K7xtYSWsh?usp=sharing)**


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


>`WebApp`
- [Try it Out](https://item-catalog-254722.appspot.com/)

>`Info`
- [Appreciation](#appreciation)
- [FAQ](#faq)
- [Team](#team)
- [Credits](#credits)


## Datasets Preprocessing
In the cycleGAN archetucture, there are two GAN models. Each GAN model need to be trained on distinguished dataset inorder to come with something new. Since my team and I want to work with our own dataset, we came up with a way to have differnet representation of our dataset. We took our dataset, applay segmentation to it, then took the segmented dataset, then took the outlines of it. This may look similar to the pix2pix method `but we did not paire the images`. Simply we augmented the two datasetes after we took the outlines of the outlies of the segmented data.

### Segmentation
In order to get our segmented dataset, we used unsupervised algorithm `K-mean` to cluster the colors in an image.  For expermintal purposes we tried to to cluster 2 colors in an image and 3 colors. Then we notice that some of the images looks abslotly different with the different clusters number. So for some cases we took the both clustering results.
| Original | Segmententation 3 | Segmentation 2 |
| ------------- | ------------- | ------------- |
|![](Images/segmentation/1.png "Original Image")| ![](Images/segmentation/2.png "Segmented to 3 colors")| ![](Images/segmentation/3.png "Segmented to 2 colors")|

### Outlines 
We tried to use the Segmented dataset as the Dataset B with the Original dataset as Dataset A, but we were not pleased with the outcomes. Therefore, we thought about a way to increase the varaity between our A/B datasets, and this is how we get to extract the outlines of our drawings as the second dataset. `Please notice that this is NOT paired images approach`.
We extracted the outlines of our segmented drawings.
| 3 Colors Segment | Outline | 2 Colors Segment | Outline |
| ------------- | ------------- | ------------- |------------- |
| ![](Images/outlines/1.png "Segmented to 3 colors")|  ![](Images/outlines/2.png "Outline from 3 Colors Segment")| ![](Images/outlines/3.png "Segmented to 2 colors")| ![](Images/outlines/4.png "Outline from 2 Colors Segment")|


### Augmentation 
Finally the last step in preprocessing, we used `Augmentor` in order increase the number of examples in out dataset.  We have initially 121 original drawings from our artist, we segmented these images and then took the outlines to have a second dataset. Then we augmented these two datasets differently to gaine 500 examples each to trian our cycleGAN. We took our time in order to get the optimal augmentatios pipeline for our dataset. We experment with earasing, flip_top_down, chainging colors, random_distortion, gaussian_distortion, zooming, and rotate for more than 15˚. But as cool as these augmentation options are, they did not work well with our dataset. So our pipeline consist of (random flip, random 90˚ rotate, random 15˚ rotate) for 70% of each dataset and resize all of them to (256px * 256px). These are examples of our final two datasets.
| Datasets | The | Joy Of | Augmentation |
| ------------- | ------------- | ------------- | ------------- |
| *Dataset A*     | ![](Images/augmentation/2.png)|  ![](Images/augmentation/1.png)| ![](Images/augmentation/3.png)|
| *Dataset B*     | ![](Images/augmentation/4.png)|  ![](Images/augmentation/5.png)| ![](Images/augmentation/6.png)|

## Model Training
We choose to train CycleGAN model becuse of several reasons. One of the reasons is that we got inspired by the art of [Helena Sarin](https://twitter.com/glagolista) and her method. She used her own dataset to traine a cycleGAN model to make a beatiful art pieces of flowers. We were initially aiming to traine a GAN model but the intresing archetucture of CycleGAN make it need for less data to train on which is perfect in our case since our dataset is originals of our artsit. 

### Training
After training our CycleGAN for 50 EPOCHS, we got excited to reach the best results possible. So we tried to run it again and again untill we reached the point where the images dose not make sense anymore. each 25 EPOCHS takes almost 1 hour. But don't worry, we were saving our checkpoints. The total training time with good results was around 25 hour.
| Searching | For the Training | Sweet Spot |
| ------------- | ------------- | ------------- |
| 100 EPOCHS | 200 EPOCHS | 300 EPOCHS  |
| ![](Images/training/100_EPOCHS.png) | ![](Images/training/200_EPOCHS.png) | ![](Images/training/300_EPOCHS.png)  |
| 500 EPOCHS  | 600 EPOCHS  | 700 EPOCHS  |
| ![](Images/training/500_EPOCHS.png) | ![](Images/training/600_EPOCHS.png)  | ![](Images/training/700_EPOCHS.png)  |


## Postprocessing
After we trained our model, and was pleased and inspired by the generated images, now we need to fix the matter of the images quality to be more appealing to the eye. We used `Waifo` tool to reach our goal.

### Upscale
We applied this method twice to reach the desired output scale.
| Generated 256x256 | Scale to 512x512 | Scale to 1024x1024|
| ------------- | ------------- | ------------- |
| ![](Images/postprocessing/0.png) | ![](Images/postprocessing/s1.png)|  ![](Images/postprocessing/s2.png)|

### Noise
We aplllied the noise reduction with the noise level 3 also twice.
| Generated | Reduce Noise | Reduce Noise |
| ------------- | ------------- | ------------- |
| ![](Images/postprocessing/0.png) | ![](Images/postprocessing/n1.png)|  ![](Images/postprocessing/n2.png)|

## Info 
### Appreciation
Thank you for giving us this chanse to learn valuable skilles. Thank you `Backyard` for provide us with top top people in the field of Creative AI, and help us whenever we needed help. Thank you `Gene Kogen` for your fun intro to creative AL. Thank you `Prof.Philippe Pasquier` for teaching us wide range of AI algorithms. Thank you `Ellen Nickles` for intruduce us to RunwayML. Special big thanks to `Meredith Thomas, Sofia Crespo, and Feileacan McCormick` for getting our hands dirty with the algorithms, tools and scripts. Thank you `Albert Barque-Duran` for helping us to formulate our conceps.

### FAQ
Run the program in the exact same order presented. Remember to select the GPUs in the notebooks setting, Hardware accelerator.

### Team
| The Designer | The Artist | The Geek |
| ------------- | ------------- | ------------- |
| ![](Images/team/Afaaf.png) | ![](Images/team/Ali.png)|  ![](Images/team/Maha.png)|
| Afaaf | Ali | Maha |

## Credits
[Augmentor](https://github.com/mdbloice/Augmentor)
[Cyclegan](https://www.tensorflow.org/tutorials/generative/cyclegan)
[Waifu2x](https://github.com/nagadomi/waifu2x)
