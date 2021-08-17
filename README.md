# Graph Neural Networks for Particle Momentum Estimation in the CMS Trigger System

## Abstract

The Compact Muon Solenoid (CMS) is a detector at the Large Hadron Collider (LHC) located near Geneva, Switzerland. The CMS experiment detects the resulting particles from the collusion and measures their kinematics using various sub detectors working in concert. High momentum muons are significant objects for many physics analyses at CMS. Therefore, an accurate momentum assignment scheme differentiating low momentum muons (background) from high momentum muons (signal) is crucial to the Endcap Muon Track Finder (EMTF) trigger. The first algorithm implemented in the trigger system was a discretized boosted decision tree. In this study, we study the use of deep learning algorithms (Fully Connected Neural Networks (FCNNs), Convolutional Neural Networks (CNNs) and Graph Naural Networks (GNNs)) at the trigger level that requires highly optimized inference. We develop and benchmark the GNNs for momentum regression in the trigger system.

** Models **

Codes used to train and test the models are available under `Models` folder. Training results for FCNN and CNN models can be found in `GSoC v5.ipynb` and `GSoC v6.ipynb`. The difference between two scripts is the generation of 2D images for the CNN model. In the former, Phi angle, Theta angle and Front/Rear hit features are used to locate exact locations of the hits in 4 detectors as follows:

![image](https://user-images.githubusercontent.com/66868163/129752327-1932b0eb-bda7-4c04-9c5f-26b303fb0d23.png)

Then, linear interpolation is utilized to obtain the complete trajectory of the muons as below:

![image](https://user-images.githubusercontent.com/66868163/129753031-08faa3c3-8ac5-48a9-8a5e-316a4bada7b4.png)

Since a great part of the images are empty, they introduce redundancy in the feature space. To eliminate this problem, we crop the generated images while keeping the whole trajectory within the bounds as follows:

![image](https://user-images.githubusercontent.com/66868163/129753693-1d1e6a3d-0358-4b7b-a2b6-f22c9ef3be33.png)

