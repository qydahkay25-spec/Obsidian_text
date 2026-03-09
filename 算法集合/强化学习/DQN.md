# 一、DQN（Deep Q Network）

## 1 DQN 是什么

**DQN = 深度Q网络**

它是把 **Q-learning + 神经网络** 结合起来的强化学习算法。

核心思想：

> 用神经网络来逼近 Q 函数 Q(s,a)Q(s,a)Q(s,a)。

提出于 **2015年** 的著名论文：

- Human-level control through deep reinforcement learning  
    作者：Volodymyr Mnih 等人（来自 DeepMind）
    

这篇论文让 AI 在 **Atari 游戏**中达到接近人类水平。

---

# 二、DQN 解决的问题

传统 **Q-learning** 有一个问题：

如果状态很多：

状态数 × 动作数

Q表会非常大。

例如：

10000 × 10

就无法存储。

因此：

**用神经网络来预测 Q 值**

Q(s,a;θ)Q(s,a;\theta)Q(s,a;θ)

输入：

state

输出：

每个动作的 Q 值

例如：

输入：状态 s  
  
输出：  
Q(左)=2.1  
Q(右)=5.4  
Q(上)=3.2  
Q(下)=1.1

选择：

最大Q值动作

---

# 三、DQN 网络结构

state s  
   │  
   ▼  
神经网络  
   │  
   ▼  
Q(s,a1) Q(s,a2) Q(s,a3)

例如：

输入：84×84游戏画面  
  
CNN提取特征  
  
输出：动作Q值

---

# 四、DQN 的三个关键技术

DQN 能成功主要靠 **三大技术**。

---

## 1 经验回放（Replay Buffer）

存储历史数据：

(s, a, r, s')

训练时：

**随机采样**

作用：

- 打破数据相关性
    
- 提高训练稳定性
    

---

## 2 目标网络（Target Network）

DQN 使用 **两个网络**：

Q 网络  
Target Q 网络

更新目标：

y=r+γmax⁡Q′(s′,a′)y=r+\gamma \max Q'(s',a')y=r+γmaxQ′(s′,a′)

其中：

Q'

来自 **目标网络**

作用：

**防止训练震荡**

---

## 3 ε-greedy 探索

智能体需要探索：

策略：

ε概率：随机动作  
1-ε概率：最大Q动作

例如：

ε = 0.1

10% 随机探索。

---

# 五、DQN 训练流程

初始化 Q 网络  
初始化 ReplayBuffer  
  
循环：  
  
    观察状态 s  
    ε-greedy 选择动作 a  
    执行动作  
  
    获得 r, s'  
  
    存入 buffer  
  
    从 buffer 采样 batch  
  
    更新 Q 网络

---

# 六、DQN 的特点

优点：

- 能处理 **高维状态**
    
- 比传统 Q-learning 强很多
    

缺点：

❗只能用于：

离散动作空间

例如：

左 / 右  
跳 / 不跳

不能处理：

连续动作

比如：

转角 0°–360°  
速度 0–100

所以提出：

**DDPG**