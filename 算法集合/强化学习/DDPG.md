# 七、DDPG（Deep Deterministic Policy Gradient）

DDPG 是 **解决连续动作问题** 的算法。

提出论文：

- Continuous control with deep reinforcement learning  
    作者：Timothy P. Lillicrap 等人（DeepMind）
    

---

# 八、DDPG 的核心思想

DDPG 使用：

**Actor–Critic 架构**

Actor：输出动作  
Critic：评价动作

结构：

state  
  │  
  ▼  
Actor  
  │  
action  
  ▼  
Critic  
  │  
Q(s,a)

---

# 九、Actor 和 Critic

## 1 Actor（策略网络）

输入：

state

输出：

action

例如：

转向角 = 0.35  
速度 = 2.1

---

## 2 Critic（价值网络）

输入：

state + action

输出：

Q(s,a)

表示：

这个动作好不好。

---

# 十、DDPG 的四个网络

DDPG 有 **四个神经网络**：

Actor  
Actor_target  
  
Critic  
Critic_target

作用：

稳定训练。

---

# 十一、DDPG 的训练思想

### Critic 更新

目标：

y=r+γQ′(s′,μ′(s′))y=r+\gamma Q'(s',\mu'(s'))y=r+γQ′(s′,μ′(s′))

损失：

L=(Q(s,a)−y)2L=(Q(s,a)-y)^2L=(Q(s,a)−y)2

---

### Actor 更新

目标：

让 Critic 给更高评分。

策略梯度：

∇J=∇aQ(s,a)∇θμ(s)\nabla J = \nabla_a Q(s,a)\nabla_\theta \mu(s)∇J=∇a​Q(s,a)∇θ​μ(s)

---

# 十二、DDPG 训练流程

初始化 Actor Critic  
初始化 ReplayBuffer  
  
循环：  
  
    state s  
  
    Actor(s) → action  
  
    加探索噪声  
  
    执行动作  
  
    得到 r,s'  
  
    存入 buffer  
  
    采样 batch  
  
    更新 Critic  
  
    更新 Actor  
  
    更新 target 网络

---

# 十三、DQN vs DDPG 对比

|特点|DQN|DDPG|
|---|---|---|
|类型|Value-based|Actor-Critic|
|动作|离散|连续|
|网络|一个Q网络|Actor + Critic|
|输出|Q(s,a)|action|
|应用|游戏|控制问题|

---

# 十四、直观理解

### DQN

输入 state  
输出 每个动作Q值  
选最大Q

例如：

左=2  
右=5  
上=1

选择：

右

---

### DDPG

输入 state  
直接输出 action

例如：

转角=0.35  
速度=2.1

---

# 十五、一句话总结

**DQN**

> 用神经网络学习 Q(s,a)，适合离散动作。

**DDPG**

> 用 Actor-Critic 学习连续动作策略。

---

如果你是 **准备做算法研究或者写论文**，我建议你一定再理解三个算法，因为它们是 **DDPG 的升级版**：

TD3  
PPO  
SAC

尤其是 **TD3（DDPG 改进版）**，现在很多论文都会用。
