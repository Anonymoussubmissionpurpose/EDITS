# EDITS
Open source code for paper "EDITS: Modeling and Mitigating Data Biasfor Graph Neural Networks".

## Environment
Experiments are carried out on a Titan RTX with Cuda 10.1. 

Details can be found in requirements.txt.

Notice: Cuda is enabled for default settings.

## Usage
Default dataset for node classification and link prediction is ACM and BlogCatalog, respectively.
Use as
```
python train.py
```
for preprocessing and 
```
python classification.py
```
for downstream node classification task.

## Log example for node classification

*Directly do node classification task with the orginal attributed network:


*Debiasing attributed network with EDITS:
```
python train.py
```
```
****************************Before debiasing****************************
Attribute bias : 
Sum of all Wasserstein distance value across feature dimensions: 0.017159402967899848
Average of all Wasserstein distance value across feature dimensions: 0.0009533001648833249
Structural bias : 
Sum of all Wasserstein distance value across feature dimensions: 0.01976526986139568
Average of all Wasserstein distance value across feature dimensions: 0.0010980705478553154
****************************************************************************
100%|██████████| 500/500 [13:25<00:00,  1.61s/it]
Preprocessed datasets saved.
```
*Carry out node classification task with the output of EDITS:
```
python classification.py
```
```
****************************After debiasing****************************
Attribute bias : 
Sum of all Wasserstein distance value across feature dimensions: 0.005456557063655252
Average of all Wasserstein distance value across feature dimensions: 0.00038975407597537516
Structural bias : 
Sum of all Wasserstein distance value across feature dimensions: 0.007008246510664321
Average of all Wasserstein distance value across feature dimensions: 0.000500589036476023
****************************************************************************
100%|██████████| 1000/1000 [01:46<00:00,  9.40it/s]
Optimization Finished!
Total time elapsed: 106.4210s
Delta_{SP}: 0.05891537959413723
Delta_{EO}: 0.032898650194463586
F1: 0.7528969621046038
AUC: 0.8648256436864998
```
