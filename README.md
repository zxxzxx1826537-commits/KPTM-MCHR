# KPTM-DCHR

## File Description

1. `train.py`: Original training script with all original functions preserved
2. `automl_train.py`: Complete script for automatic hyperparameter optimization
3. `quick_automl.py`: Fast-test version of automatic optimization script
4. `HypergraphProteinRegressionModel.py`: Model file

## Features

### 1. Automatic Hyperparameter Tuning
Automatically optimize the following parameters:
- Learning rate (`lr`)
- Weight decay (`wd`)
- Dropout rate (`dropout`)
- Hidden layer dimension (`hid_feats`)
- Network fusion parameter (`lambda_param`)
- Training epochs (`epochs`)

### 2. Automatic Structure Optimization of Regression Head
Optimize the structure of regression head automatically:
- Number of layers (`n_regressor_layers`)
- Dimension of each layer (`regressor_layer_X`)

## Usage

### Quick Test (Recommended for first use)

```bash
python quick_automl.py
```
This executes a fast hyperparameter optimization process using a small dataset and fewer trials.

## Output
Two types of files will be generated after optimization:
  - best_hyperparameters.txt or quick_best_hyperparameters.txt: Records the optimal hyperparameter set.
  - best_hypergraph_protein_model.pth: Model weights with the best cross-validation performance.

## Notes
- Due to the large size of the data files, the datasets required for code execution are provided as attachments in Release.

## Requirements
```bash
Name                       Version             
dgl                          1.1.2.cu118        
python                       3.9.24              
pytorch                      2.5.1               
pytorch-cuda                 12.4                
```
