# DSSP-LR
Dynamic State-Space Pruning with Localized Reactivation

An adaptive structural reinforcement learning framework designed to reduce unnecessary exploration in large tabular environments while enabling fast recovery in non-stationary conditions.

Overview

Traditional tabular Reinforcement Learning (RL) algorithms suffer from inefficient exploration, especially in large state spaces where agents repeatedly revisit useless states and dead-end trajectories.

This project introduces:

DSSP-LR (Dynamic State-Space Pruning with Localized Reactivation)

A topology-aware RL framework that:

dynamically prunes unrewarding regions,
validates environment connectivity using graph theory,
compresses the effective state space,
and rapidly adapts to environmental changes without resetting the learned policy.

The framework combines:

Reinforcement Learning
Graph-Theoretic Reachability Validation
Dynamic Environment Restructuring
Localized Optimistic Exploration
Core Idea

Instead of allowing the agent to endlessly explore every state:

Failed trajectories are tracked in batches
Frequently useless states become pruning candidates
A BFS connectivity check verifies that the target remains reachable
Safe states are permanently converted into walls
The environment gradually shrinks into optimized corridors

When the environment changes dynamically:

only local regions near the disruption are reopened,
optimistic Q-values are injected,
and the agent rapidly discovers alternative detours.
Key Features
Dynamic state-space compression
BFS/DFS graph safety validation
Localized reactivation mechanism
Optimistic initialization for rapid adaptation
Non-stationary environment support
Reduced exploration complexity
Structural environment optimization
Framework Architecture
Failed Episodes
       ↓
Batch State Tracking
       ↓
Candidate Pruning
       ↓
BFS Connectivity Validation
       ↓
Safe Structural Compression
       ↓
Dynamic Obstacle Detection
       ↓
Localized Reactivation
       ↓
Optimistic Q-Value Injection
       ↓
Rapid Detour Discovery
Mathematical Foundation
Standard Q-Learning Update
Q(s,a)←Q(s,a)+α[R+γ
a
′
max
	​

Q(s
′
,a
′
)−Q(s,a)]
Effective State-Space Compression
S
eff
	​

=S∖F
b
	​

Localized Reactivation
F
updated
	​

=F
b
	​

∖R
local
	​

Experimental Environment
30×30 Grid World
900 total states
Dynamic obstacle insertion
Non-stationary topology
Tabular Q-Learning baseline
Results
Final Performance
Original state space: 900 states
Pruned states: 592
Compression achieved: >65%
Final optimized escape path: 33 steps
Observed Behavior

The framework:

reduced redundant exploration,
compressed dead-end regions,
and adapted rapidly after environmental disruptions.
Repository Structure
.
├── paper/
│   └── DSSP-LR_paper.tex
│
├── src/
│   ├── environment.py
│   ├── dssp_lr.py
│   ├── q_learning.py
│   └── visualization.py
│
├── results/
│   ├── learning_curve.png
│   ├── compression_map.png
│   └── training_logs.txt
│
├── README.md
└── requirements.txt
Future Work

Potential future extensions include:

Deep Reinforcement Learning (DQN / PPO)
Continuous state-space pruning
Multi-agent DSSP-LR
Probabilistic graph validation
Convergence guarantees
Real-world robotics applications
Research Direction

DSSP-LR is not intended to replace RL algorithms.

Instead, it acts as a:

structural meta-framework for adaptive exploration optimization.

The framework modifies the environment topology itself while preserving reachability constraints through graph-theoretic validation.

Citation

If you use this work in research or projects, please cite:

@article{dssp_lr_2026,
  title={Dynamic State-Space Pruning with Localized Reactivation (DSSP-LR)},
  author={Djafri, Zakaria},
  year={2026}
}
Author

Djafri Zakaria
📧 zakidjafri53@gmail.com
