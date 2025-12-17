### **RMSEP（预测集均方根误差**)
RMSEP 是**回归 / 预测模型**中评估模型泛化能力的核心指标，专门针对**预测集（测试集）** 计算，反映模型对未知数据的预测精度，取值越小，模型预测效果越好。
#### **核心定义与公式**

**公式**：$\text{RMSEP} = \sqrt{\frac{1}{n}\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$

**其中**：

- **$y_i$**：预测集（测试集）中第 $i$ 个样本的真实值
    
- **$\hat{y}_i$**：模型对预测集中第 $i$ 个样本的预测值
    
- **$n$**：预测集中的样本数量
    
#### **关键解读**

- **单位与量纲**
    
    - RMSEP 的计算结果与原始目标变量的**单位一致**（例如，预测浓度为 mg/L，则 RMSEP 的单位也为 mg/L）。这使得其数值具有直观的物理或业务意义，能直接反映预测值与真实值的平均偏差幅度。
        
- **与 RMSE 的区别**
    
    - **RMSE（均方根误差）**：是一个通用术语，可用于计算训练集或测试集的误差。它衡量的是模型在**特定数据集**上的拟合精度。
        
    - **RMSEP（预测均方根误差）**：特指在独立的**预测集（测试集）** 上计算的 RMSE。它专门用于评估模型对**未知新数据**的预测能力，是衡量模型**泛化能力**的核心指标。在化学计量学、光谱分析、机器学习等预测建模领域被广泛使用。
        
- **理想值**
    
    - RMSEP **趋近于 0** 是理想状态，表明模型对未知数据的预测非常精准，几乎不存在系统偏差。数值越小，代表模型的泛化预测性能越好。
### 方式 1：手动实现 RMSEP（公式还原）


```python
def calculate_rmsep(y_true, y_pred):
    """
    手动计算预测集均方根误差（RMSEP）
    :param y_true: 预测集真实值（np.array/list）
    :param y_pred: 预测集预测值（np.array/list）
    :return: RMSEP值
    """
    y_true = np.array(y_true)
    y_pred = np.array(y_pred)
    # 计算均方误差
    mse = np.mean((y_true - y_pred) ** 2)
    # 开平方得到RMSEP
    rmsep = np.sqrt(mse)
    return rmsep

# 调用计算
rmsep_manual = calculate_rmsep(y_pred_set, y_pred_set_pred)
print(f"手动计算 RMSEP = {rmsep_manual:.4f}")  # 示例结果：0.1291
```

### 方式 2：调用 sklearn 简化计算（推荐）


```python
def calculate_rmsep_sklearn(y_true, y_pred):
    """通过sklearn的mean_squared_error计算RMSEP"""
    mse = mean_squared_error(y_true, y_pred)
    rmsep = np.sqrt(mse)
    return rmsep

# 调用计算
rmsep_sklearn = calculate_rmsep_sklearn(y_pred_set, y_pred_set_pred)
print(f"sklearn 计算 RMSEP = {rmsep_sklearn:.4f}")  # 结果与手动一致
```

#### 关键注意事项

1. **数据范围**：RMSEP 仅针对**预测集 / 测试集**计算，切勿用训练集数据（否则会高估模型性能）；
2. **异常值影响**：RMSEP 对异常值敏感（平方项会放大极端偏差），计算前需清洗预测集中的异常值；
3. **结果解读**：
    - 对比不同模型时，RMSEP 越小说明模型泛化能力越强；
    - 结合 R²（预测集）和 SMAPE 综合判断：若 RMSEP 小且 R² 高、SMAPE 低，说明模型整体预测性能优秀；
4. **量纲统一**：若需跨数据集对比模型，可将 RMSEP 归一化（如除以真实值的均值），得到无量纲的 “相对 RMSEP”。
