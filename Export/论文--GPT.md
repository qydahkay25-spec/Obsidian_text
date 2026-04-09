1. **Deep learning-based remote sensing retrieval of inland water quality: A review**  
    这篇更新，重点讲深度学习在内陆水体水质反演中的输入特征构造、模型结构和优化策略。
2. **Graph neural networks to model and optimize the operation of Water Distribution Networks: A review**  
    如果你准备把“图神经网络溯源”当主线，这篇必须看，它从 WDN 的物理/水力过程和常见图模型一起讲。

---

## 2) 预测模型类

1. **River water quality forecasting: a novel LSTM-Transformer approach enhanced by multi-source data**  
    这篇和你题目非常贴：自动监测数据 + 遥感土地类型 + 气象因子，一起做 TP/TN 预测。
2. **Machine learning-based evolution of water quality prediction model: An integrated robust framework for comparative application on periodic return and jitter data**  
    这篇适合看“数据去噪 + 特征选择 + LSTM”这一套怎么封装成完整预测框架。
3. **A long-term prediction model for key water quality based on transformer with parallel attention mechanism and adaptive spectral enhancement**  
    偏 Transformer 长时序建模，适合你做中长期预测时参考。
4. **Research on Water Quality Prediction Model Based on Spatiotemporal Weighted Fusion and Hierarchical Cross-Attention Mechanisms**  
    如果你想看“TCN/GRU/交叉注意力/时空融合”这种更复杂的预测模型，这篇比较贴。
5. **A hybrid deep learning approach to improve real-time effluent quality prediction in wastewater treatment plant**  
    这篇是 TCN-LSTM 混合模型，适合你看 hybrid 模型怎么做、怎么比较、怎么用 SHAP 解释。
6. **Water Quality Prediction Based on Machine Learning and Comprehensive Weighting Methods**  
    适合看传统 ML + 特征加权选择在水质预测里的写法。
7. **Advanced machine learning models for accurate water quality classification and prediction**  
    如果你想看 XGBoost/LightGBM 这类非深度学习强基线，这篇值得放到对比实验里。
8. **Predicting and investigating water quality index by robust machine learning approaches**  
    这篇更偏 WQI，但适合你看 RF/SVM/LSTM 这类经典对比怎么做。

---

## 3) 多源融合类

1. **River water quality forecasting: a novel LSTM-Transformer approach enhanced by multi-source data**  
    这篇既属于预测模型，也属于多源融合；它把自动监测、遥感地类、气象因素放在一个模型里。
2. **Monitoring water quality parameters in urban rivers using multi-source data and machine learning approach**  
    很适合你看“现场采样 + Sentinel-2 + 气象 + 土地利用”怎么融合成一个河流水质监测框架。
3. **A Deep Learning Algorithm for Multi-Source Data Fusion to Predict Effluent Quality of Wastewater Treatment Plant**  
    这篇很有参考价值，因为它把**水量、过程变量、能耗、水质指标**一起融合，特别像你后面“工况 + 水质”的写法。
4. **Multi-source and multimodal data fusion for improved management of a wastewater treatment plant**  
    这篇更强调**异步、异粒度、异质量、多模态**数据怎么融合，非常适合你写“多源异构数据”的方法背景。
5. **Deep learning-based remote sensing retrieval of inland water quality: A review**  
    虽然是综述，但对“输入特征如何从单纯光谱走向空间补丁和多源融合”总结得很有用。
6. **Integration of Machine Learning and Remote Sensing for Water Quality Monitoring**  
    适合你补“遥感 + ML”这一支多源融合背景。
7. **Multi-Source Data Fusion and Heuristic-Optimized Machine Learning for Large-Scale River Water Quality Inversion**  
    这篇把 Sentinel-2、气象、土地利用、景观格局指标一起融合，适合你参考“大尺度、多因素”融合思路。
8. **Multimodal remote sensing and meteorological estimation of long-term water quality in remote inland reservoirs**  
    适合你看“遥感 + 气象 + 长期样本”在水质估计中的融合套路。
9. **Leveraging remote sensing–enabled machine learning for river water quality …**  
    这篇强调遥感和高级 ML 的结合能提升河流水质预测，并建议纳入更高频事件数据、土地利用变化和气候波动。适合做你多源融合一章的延伸阅读。

---

## 4) 图模型 / 溯源类

这部分对你最重要。你老师给的题目里，“建筑给排水管网/灌区渠道拓扑 + 多节点监测 + 污染扩散路径”本质上就是这条线。

1. **Graph convolutional networks based contamination source identification across water distribution networks**  
    这是很值得看的早期图模型溯源论文，适合拿来当你的方法基线。
2. **Gated graph neural networks for identifying contamination sources in water distribution networks**  
    这篇更直接，就是面向 WDN 的污染源识别，把时空水质数据和流向信息一起建模。
3. **Real-time water quality prediction in water distribution networks using graph neural networks with sparse monitoring data**  
    虽然重点是全网水质预测，但它非常适合你借鉴“图构建 + 稀疏监测 + 全网推断”这套思路。
4. **Graph neural networks-based dynamic water quality state estimation in water distribution networks**  
    这篇解决的是“传感器不够、节点没测到，怎么估计全网状态”，对你后面做污染传播判断很有帮助。
5. **Dual-stream graph convolutional networks enable accurate real-time water quality prediction in water distribution networks with sparse observational data**  
    这是比较新的图模型文章，值得看它怎么进一步提升稀疏观测下的预测效果。
6. **Graph neural networks to model and optimize the operation of Water Distribution Networks: A review**  
    如果你要系统理解“图模型在 WDN 里到底都拿来做什么”，这篇综述很适合。
7. **Contaminant source identification in water distribution networks: A Bayesian model updating approach**  
    这篇不是 GNN，但它是经典溯源思路之一。你写相关工作时，拿来和图模型形成对比会很好。

---

## 你现在最值得优先看的 10 篇

如果你不想一下子读太多，先读这 10 篇就够你把开题现状搭起来：

1. **A Comprehensive Review of Machine Learning for Water Quality Prediction over the Past Five Years**
2. **Recent Progress on Surface Water Quality Models Utilizing Machine Learning**
3. **A Review of Water Quality Forecasting and Classification Using Machine Learning**
4. **River water quality forecasting: a novel LSTM-Transformer approach enhanced by multi-source data**
5. **Monitoring water quality parameters in urban rivers using multi-source data and machine learning approach**
6. **A Deep Learning Algorithm for Multi-Source Data Fusion to Predict Effluent Quality of Wastewater Treatment Plant**
7. **Graph convolutional networks based contamination source identification across water distribution networks**
8. **Gated graph neural networks for identifying contamination sources in water distribution networks**
9. **Real-time water quality prediction in water distribution networks using graph neural networks with sparse monitoring data**
10. **Graph neural networks-based dynamic water quality state estimation in water distribution networks**

## 按你的论文用途来分

### 写“研究现状”先读

- 1, 2, 3, 4, 5, 6, 9

### 借“预测模型”先读

- River water quality forecasting...
- Machine learning-based evolution...
- A long-term prediction model...
- Research on Water Quality Prediction Model Based on Spatiotemporal Weighted Fusion...
- A hybrid deep learning approach to improve real-time effluent quality prediction...

### 借“多源融合”先读

- Monitoring water quality parameters in urban rivers using multi-source data...
- A Deep Learning Algorithm for Multi-Source Data Fusion...
- Multi-source and multimodal data fusion for improved management...
- Integration of Machine Learning and Remote Sensing for Water Quality Monitoring

### 借“图模型溯源”先读

- Graph convolutional networks based contamination source identification...
- Gated graph neural networks for identifying contamination sources...
- Real-time water quality prediction in WDN using GNNs...
- Graph neural networks-based dynamic water quality state estimation...