# Color-aware two-branch DCNN for efficient plant disease classification
This repository contains code for the paper "Color-aware two-branch DCNN for efficient plant disease classification" by Joao Paulo Schwarz Schuler, Santiago Romani, Mohamed Abdel-Nasser, Hatem Rashwan and Domenec Puig.

## Abstract
Deep convolutional neural networks (DCNNs) have been successfully applied to plant disease detection. Unlike most existing studies, we propose feeding a DCNN CIE Lab instead of RGB color coordinates. We modified an Inception V3 architecture to include one branch specific for achromatic data (L channel) and another branch specific for chromatic data (AB channels). This modification takes advantage of the decoupling of chromatic and achromatic information. Besides, splitting branches reduces the number of trainable parameters and computation load by up to 50\% of the original figures using modified layers. We achieved a state-of-the-art classification accuracy of 99.48\% on the Plant Village dataset and 76.91\% on the Cropped-PlantDoc dataset.

## Citing this Paper
TBC very soon.
