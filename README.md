# KPTM-DCHR
We proposed a model, named KPTM-DCHR, to predict the number of lysine modification types that a protein may undergo. The entire procedure contained six consecutive modules. In Module (A), a protein similarity calculation process was performed by integrating protein sequence and domain architecture information, where sequence similarities were computed using normalized Levenshtein distance and Gaussian kernel-based PseAAC similarity, while domain similarity was obtained through a hybrid TF-IDF strategy with neighbor domain augmentation. In Module (B), two complementary hypergraphs, including a KNN-like hypergraph and a spectral clustering-based hypergraph, were constructed based on the protein similarity network to capture the local physical connectivity and global functional similarity of proteins, respectively. In Module (C), the pre-trained ProtT5 model was adopted to extract raw protein features from amino acid sequences, generating the initial protein feature matrix. In Module (D), hypergraph convolution was performed on the constructed hypergraphs to learn high-order structural representations of proteins. In Module (E), a dual-channel attention mechanism was introduced to adaptively fuse the features learned from different hypergraph branches, generating the final fused protein embeddings. In Module (F), a four-layer multilayer perceptron was applied to the fused embeddings to perform regression prediction, thereby producing the final output for the number of lysine modification types of each protein.
![uploading](https://github.com/zxxzxx1826537-commits/img/blob/main/1.png)








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
