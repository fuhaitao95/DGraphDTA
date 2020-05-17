# DGraphDTA
Inspired by GraphDTA, a method for predicting the affinity of drug-protein based on graph neural network is proposed, which is called DGraphDTA (double Graph DTA predictor). The method can predict the affinity only using the molecule SMILES and protein sequence. This repo gits from GraphDTA, and compared with GraphDTA, the method constructs both the graph of protein and small molecule at the same time to improve the accuracy. The protein graph is constructed according to contact map.

<div align=center><img width="900" height="400" src="https://github.com/595693085/DGraphDTA/blob/master/figures/architecture.png"/></div>

## dependencies
numpy == 1.17.4 <br>
kreas == 2.3.1 <br>
Pconsc4 == 0.4 <br>
pytorch == 1.3.0 <br>
PyG (torch-geometric) == 1.3.2 <br>
hhsuite (https://github.com/soedinglab/hh-suite)<br>
rdkit == 2019.03.4.0 <br>
ccmpred (https://github.com/soedinglab/CCMpred) <br>

## data preparation
1. Prepare the data need for train. Get all msa files of the proteins in datasets (for more detail description of datasets, please refer to [datasets](https://github.com/hkmztrk/DeepDTA/blob/master/data/README.md)), and using Pconsc4 to predict all the contact map. A script in the repo can be run to do all the steps: <br>
**python scripts.py** <br><br>
2. And if you want to skip the long time preparation, please directly download the contact map and msa files which we already generated from [files](https://drive.google.com/open?id=1rqAopf_IaH3jzFkwXObQ4i-6bUUwizCv). For more detailed generating information, please refer to the "scripts.py". Then copy the corresponding two folders to each dataset dir. For example:  <br>
(1) download the data.zip and unzip it. <br>
(2) copy two folders called "aln" and "pconsc4" from davis to the /data/davis of your repo, so do the KIBA. <br>


## train 
Run the training code. <br>
**python training.py 0 0** <br>
where the two parameters are dataset selection, gpu selection.

## test
Must run after the train step. This step is to reproduce the experiments. <br>
**python test.py 0 0** <br>
and the parameters are same to the training.
