---
noteId: "6b01abd00f8611eea038e3eb8b9b08a3"
tags: []
layout: default
title: Data processing, model training, and testing
parent: Machine Learning
nav_order: 2
---

# Data processing, model training, and testing
Check the [code](https://github.com/PaynatPierre/hackaton_voiture_autonome/tree/master/src) of the best team of the hackathon.  

You will probably need some specific library to execute your model:
- Scipy: $ python -m pip install scipy
- Torch, torchvision, torchaudio (?) $ pip3 install torch torchvision torchaudio
- Cv_bridge 

{: .note}
On windows, it is necessary to [have ROS](http://127.0.0.1:4000/Robot_MuSHR/docs/2_mushr/2_install_ros1/) to obtain cv_bridge. Note, once you have a ROS, make sure your Python environment is connected to it.

## Data preprocessing
The [link](https://github.com/anr-multitrans/Hackathon-3IA-MultiTrans/blob/main/src/hackaton_voiture_autonome-master/preprocess_data.py) of the code.

Modify the [data path](https://github.com/PaynatPierre/hackaton_voiture_autonome/blob/c26ddffd598f8be3c66b389b1107df25124698b8/src/config.py#L10).

## Model training
The [link](https://github.com/anr-multitrans/Hackathon-3IA-MultiTrans/blob/main/src/hackaton_voiture_autonome-master/main.py) of the code.

{: .note}
Use the NEF server in Inria.
1. [Request an account](https://nef-services.inria.fr/account/request)  
2. Login 
3. Run your code with some [sample script](https://gitlab.inria.fr/lohl/nef-templates-maasai) 

## Model testing
You can test your model on your own PC with a bag playing. To do this you need to [install ros](http://127.0.0.1:4000/Robot_MuSHR/docs/2_mushr/2_install_ros1/) on your computer first.
