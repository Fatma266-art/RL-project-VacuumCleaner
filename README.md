# 🤖 Vacuum Cleaner RL — Q-Learning vs SARSA

> Comparing off-policy and on-policy Temporal Difference methods on a custom grid environment

---

## 📌 Project Overview

This project implements and compares two Temporal Difference (TD) Reinforcement Learning algorithms — **Q-Learning** and **SARSA** — on a custom 8×8 grid vacuum cleaning environment built entirely from scratch (no external RL library).

**Course:** Reinforcement Learning (AI318) — Third Year  
**Faculty:** Artificial Intelligence, Menoufia University  
**Instructor:** Dr. Mahmoud Emam

---

## 📁 Project Structure

```
RL complete project/
├── RL_Vacuum_Project.ipynb          # Main RL notebook
├── env_preview.png                  # Grid environment visualization
├── plot1_learning_curves.png        # Reward & coverage over episodes
├── plot2_policy_value.png           # Policy grid + value function overlay
├── plot3_comparison.png             # Q-Learning vs SARSA comparison
├── trajectory_ql.gif                # Q-Learning agent trajectory animation
└── trajectory_sarsa.gif             # SARSA agent trajectory animation
```

---

## 🌍 Environment — `GridVacuumEnv`

| Property | Value |
|----------|-------|
| Grid size | 8 × 8 |
| State | (agent_row, agent_col, dirty_cells_tuple) |
| Actions | Up, Down, Left, Right, Clean |
| Reward | +10 clean dirt, −1 per step, −5 hit wall, +50 all clean |
| Episode end | All cells clean OR max steps reached |
| Reset | `soft_reset()` — same grid layout every episode for consistent Q-table |

---

## 🤖 Algorithms

### Q-Learning (Off-Policy TD)
- Learns the optimal Q-value regardless of the policy being followed
- Update: `Q(s,a) ← Q(s,a) + α [r + γ max Q(s',a') − Q(s,a)]`
- Explores with ε-greedy; updates toward the greedy (optimal) action

### SARSA (On-Policy TD)
- Learns the Q-value for the policy actually being followed
- Update: `Q(s,a) ← Q(s,a) + α [r + γ Q(s',a') − Q(s,a)]`
- More conservative — penalizes risky exploratory moves during training

---

## ⚙️ Training Configuration

| Hyperparameter | Value |
|----------------|-------|
| Episodes | 500 |
| Max steps/episode | 200 |
| Learning rate (α) | 0.1 |
| Discount factor (γ) | 0.95 |
| Epsilon (ε) start | 1.0 |
| Epsilon decay | 0.995 |
| Epsilon min | 0.01 |

---

## 📊 Notebook Sections

1. Imports & Constants
2. Environment — `GridVacuumEnv` (Fixed State Encoding)
3. Environment Preview
4. Q-Learning Training
5. SARSA Training
6. Learning Curves (reward + coverage)
7. Policy Grid + Value Function Overlay
8. Evaluation — 10 runs × 30 episodes
9. Algorithm Comparison Plot
10. Final Summary & Key Findings
11. Trajectory Animation (GIF export)

---

## 🎬 Trajectory Animations

- `trajectory_ql.gif` — Q-Learning agent navigating and cleaning the grid
- `trajectory_sarsa.gif` — SARSA agent doing the same

The agent (🔴 red) starts from the yellow tile and cleans all dirty cells.

---

## 🛠️ Tech Stack

`Python` · `NumPy` · `Matplotlib` · `Pillow` (GIF export) · No external RL library
