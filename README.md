# KPTM-DCHR
# 蛋白质超图神经网络自动化调参指南

本文档介绍了如何使用自动化机器学习工具对蛋白质超图神经网络进行超参数优化。

## 文件说明

1. `train.py`: 原始训练脚本，保持原有功能
2. `automl_train.py`: 完整的自动化超参数优化脚本
3. `quick_automl.py`: 快速测试版自动化优化脚本
4. `HypergraphProteinRegressionModel.py`: 支持动态配置回归头的模型

## 功能特性

### 1. 自动化超参数调优
支持自动优化以下参数：
- 学习率 (`lr`)
- 权重衰减 (`wd`)
- Dropout率 (`dropout`)
- 隐藏层维度 (`hid_feats`)
- 网络融合参数 (`lambda_param`)
- 训练轮数 (`epochs`)

### 2. 回归头结构自动优化
支持自动优化回归头的：
- 层数 (`n_regressor_layers`)
- 每层维度 (`regressor_layer_X`)

## 使用方法

### 快速测试（推荐首次使用）

```bash
python quick_automl.py
```

这将执行一个快速的超参数优化过程，使用较小的数据集和较少的试验次数。

### 完整优化

```bash
python automl_train.py
```

这将执行完整的超参数优化过程，可能需要较长时间。

## 自定义配置

### 修改搜索空间
在 `quick_automl.py` 或 `automl_train.py` 中的 `objective` 函数里修改参数搜索空间：

```python
# 示例：修改学习率搜索范围
args.lr = trial.suggest_float('lr', 1e-5, 1e-2, log=True)  # 更宽的范围
```

### 修改试验次数
在脚本末尾修改试验次数：

```python
# 修改为执行更多试验
study = run_quick_automl(n_trials=50)
```

## 输出结果

优化完成后会生成以下文件：
1. `best_hyperparameters.txt` 或 `quick_best_hyperparameters.txt`：包含最佳超参数
2. `best_hypergraph_protein_model.pth`：在交叉验证中表现最好的模型权重

## 注意事项

1. **计算资源**：完整优化可能需要大量时间和计算资源
2. **GPU支持**：如果系统中有GPU，代码会自动使用
3. **内存管理**：大数据集可能会占用较多内存，请根据硬件配置适当调整数据规模
4. **早停机制**：内置早停机制防止过拟合

## 故障排除

如果遇到内存不足错误，可以尝试：
1. 减少试验次数
2. 使用快速测试脚本
3. 减少交叉验证折数
4. 减少蛋白质数据量







## 数据获取
有些数据文件太大，发布在Release中。
所有数据下载到本地后，根据本地路径修改代码。

















Requirements:
# Name                       Version             
dgl                          1.1.2.cu118        
python                       3.9.24              
pytorch                      2.5.1               
pytorch-cuda                 12.4                
