# Color-aware two-branch DCNN for efficient plant disease classification
This repository contains the source code for the paper [Color-aware two-branch DCNN for efficient plant disease classification](https://www.researchgate.net/publication/361511874_Color-Aware_Two-Branch_DCNN_for_Efficient_Plant_Disease_Classification) by Joao Paulo Schwarz Schuler, Santiago Romani, Mohamed Abdel-Nasser, Hatem Rashwan and Domenec Puig.

## Abstract
Deep convolutional neural networks (DCNNs) have been successfully applied to plant disease detection. Unlike most existing studies, we propose feeding a DCNN CIE Lab instead of RGB color coordinates. We modified an Inception V3 architecture to include one branch specific for achromatic data (L channel) and another branch specific for chromatic data (AB channels). This modification takes advantage of the decoupling of chromatic and achromatic information. Besides, splitting branches reduces the number of trainable parameters and computation load by up to 50\% of the original figures using modified layers. We achieved a state-of-the-art classification accuracy of 99.48\% on the Plant Village dataset and 76.91\% on the Cropped-PlantDoc dataset.

## 3 Minutes Intro Video
[![Watch the video](https://img.youtube.com/vi/u4vZZmBMFLw/0.jpg)](https://youtu.be/u4vZZmBMFLw)

## The Raw Experiment Files
The source code for the experiments described in the paper can be found at the raw folder:
* [Plant Village with baseline model](https://github.com/joaopauloschuler/two-branch-plant-disease/tree/main/raw/baseline-plant-village).
* [Plant Village with L+AB branches model](https://github.com/joaopauloschuler/two-branch-plant-disease/tree/main/raw/two-paths-plant-village).
* [Cropped-PlantDoc with L+AB branches model](https://github.com/joaopauloschuler/two-branch-plant-disease/tree/main/raw/two-paths-cropped-plant-doc).

## Results
Raw notebook files with source code for tables [3](https://github.com/joaopauloschuler/two-branch-plant-disease/blob/main/raw/two-paths-plant-village/two_path_inception.ipynb), [4](https://github.com/joaopauloschuler/two-branch-plant-disease/blob/main/raw/two-paths-cropped-plant-doc/Cropped-PlantDoc-Mixed-Layer-Search-Table-4.ipynb) and [5](https://github.com/joaopauloschuler/two-branch-plant-disease/blob/main/raw/two-paths-cropped-plant-doc/Cropped-PlantDoc-LAB-Filter-Search-Table-5.ipynb) are available.
<p align="center"><img align="center" src="raw/table3.png"></img></p>
<p align="center"><img align="center" src="raw/table4.png"></img></p>
<p align="center"><img align="center" src="raw/table5.png"></img></p>

## Create Your Own L+AB Model
You'll need to import the [K-CAI Neural API](https://github.com/joaopauloschuler/k-neural-api). Then, you can create a 20%L+80%AB Inception V3 model with 6 mixed layers as per example:
```
import os

if not os.path.isdir('k'):
  !git clone https://github.com/joaopauloschuler/k-neural-api.git k
else:
  !cd k && git pull

!cd k && pip install .

l_ratio = 0.2

model = cai.models.compiled_two_path_inception_v3(
  input_shape=(224,224,3),
  classes=38, 
  two_paths_first_block=True,
  two_paths_second_block=False,
  l_ratio=l_ratio,
  ab_ratio=(1-l_ratio),
  max_mix_idx=5, 
  model_name='two_path_inception_v3'
)
```

## Further Reading
You may be interested in our other paper about [making plant disease classification noise resistant](https://github.com/joaopauloschuler/two-path-noise-lab-plant-disease). You may also be interested at optimizing deeper layers of a DCNN: [V1](https://github.com/joaopauloschuler/kEffNetV1) and [V2](https://github.com/joaopauloschuler/kEffNetV2).

## Running the Code
Due to library updates, the code used for the paper doesn't run on current tensorflow/keras. As of the writting of this readme file, the current version of tensorflow is 2.8. An updated version of the code was done after the paper publication. This version is now compatible with tensorflow 2.8:
* [RGB - Baseline](https://github.com/joaopauloschuler/two-branch-plant-disease/blob/main/2.8/code_example_baseline_v2_8.ipynb). [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joaopauloschuler/two-branch-plant-disease/blob/main/2.8/code_example_baseline_v2_8.ipynb)
* [CIE L* a* b* - Light-Chroma Separated Branches](https://github.com/joaopauloschuler/two-branch-plant-disease/blob/main/2.8/code_example_two_paths_v2_8.ipynb). [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/joaopauloschuler/two-branch-plant-disease/blob/main/2.8/code_example_two_paths_v2_8.ipynb)

## Give this Project a Star
This project is an open source project. If you like what you see, please give it a star on github.

## Citing this Paper
```
@article{Schuler_2022_2branches,
  title={Color-Aware Two-Branch DCNN for Efficient Plant Disease Classification}, 
  volume={28}, 
  url={https://mendel-journal.org/index.php/mendel/article/view/176},
  DOI={10.13164/mendel.2022.1.055},
  number={1},
  journal={MENDEL},
  author={Schwarz Schuler, Joao Paulo and Romani, Santiago and Abdel-Nasser, Mohamed and Rashwan, Hatem and Puig, Domenec},
  year={2022},
  month={Jun.},
  pages={55-62}
}
```
