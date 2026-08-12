# Inverse Reinforcement Learning (IRL) 入门指南

本项目包含了逆向强化学习（Inverse Reinforcement Learning, IRL）的核心概念介绍与学习资料。

## 💡 什么是逆向强化学习 (IRL)？

在传统**强化学习（RL）**中，智能体的目标是根据已知的**奖励函数（Reward Function）**来学习最优策略（Policy）。

而在**逆向强化学习（IRL）**中：
- **已知**：环境动力学、专家（Expert）的示范轨迹（Demonstrations）。
- **求解**：反推专家的**奖励函数（Reward Function）**，进而推导出接近专家的最优策略。

---

## 🎯 核心经典算法

1. **Apprenticeship Learning via Inverse Reinforcement Learning** (Abbeel & Ng, 2004)
   - 基于特征匹配（Feature Matching），通过最大化边际间隔求解奖励函数。
2. **Maximum Entropy IRL (MaxEnt IRL)** (Ziebart et al., 2008)
   - 引入最大熵原理，解决专家轨迹非最优以及多义性（Ambiguity）问题。
3. **Deep Maximum Entropy IRL** (Wulfmeier et al., 2015)
   - 使用深度神经网络拟合复杂的非线性奖励函数。

---

## 📚 本项目文件说明

- `irl_handout.pdf`: IRL 讲义与入门总结 PDF
- `irl_handout.tex`: LaTeX 源码文件
- `IRL.pdf`: 经典论文与参考资料集

---

## 🚀 快速开始

可以通过查看 `irl_handout.pdf` 了解更详细的推导与公式。
