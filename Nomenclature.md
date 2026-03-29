| **Symbol**                               | Description                                                  | Definition / Comments                                        |
| ---------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| $G$                                      | Dec-POMDP tuple                                              | $G=\langle N, S, A, P, r, \Omega, O, \gamma \rangle$         |
| $\mathcal{N}$                            | Set of agents                                                | $\mathcal{N} = \{1, \dots, n\}$                              |
| $n$                                      | Total number of agents                                       |                                                              |
| $s, S$                                   | Global state and state space                                 | $s \in S$                                                    |
| $a_i, A$                                 | Action and action space of a single agent $i$                | $a_i \in A$                                                  |
| $\mathbf{a},\mathbf{A}$                  | Joint action vector and joint action space of all agents     | $\mathbf{a}=[a_1, \dots, a_n] \in \mathbf{A}\equiv A^n$      |
| $P(s' \vert s, \mathbf{a})$              | State transition probability function                        | $P(s' |s, \mathbf{a}): S \times \mathbf{A} \times S \rightarrow [0, 1]$ |
| $r(s,\mathbf{a})$                        | Shared reward function                                       | $r(s, \mathbf{a}): S \times \mathbf{A} \rightarrow \mathbb{R}$ |
| $\gamma$                                 | Discount factor                                              | $\gamma \in [0, 1)$                                          |
| $o_i, O$                                 | Local observation and observation space of a single agent    | $o_i \in O$                                                  |
| $\Omega(s, a_i)$                         | Observation function                                         | $\Omega(s, a_i): S \times A \rightarrow O$                   |
| $\tau_i, \mathcal{T}$                    | Action-observation history and history space of a single agent | $\tau_i \in \mathcal{T} \equiv (O \times A)^*$               |
| $\boldsymbol{\tau},\mathbf{T}$           | Joint action-observation history and joint history space of all agents | $\boldsymbol{\tau}=[\tau_1, \dots, \tau_n] \in \mathbf{T} \equiv \mathcal{T} ^n$ |
| $\pi_i(a_i \vert \tau_i)$                | Policy of agent $i$                                          | $$\pi_i(a_i|\tau_i):\mathcal{T}\times A \rightarrow[0, 1]$$  |
| $G_t$                                    | Discounted cumulative return                                 | $G_t = \sum_{k=0}^{\infty} \gamma^k r_{t+k}$                 |
| $Q_{tot}(\boldsymbol{\tau}, \mathbf{a})$ | Total joint action-value function                            | Estimated by the mixing network                              |
| $Q_i(\tau_i, a_i; \theta_i)$             | Individual action-value function                             | Estimated by agent $i$ with parameters $\theta_i$            |
| $V_i(\tau_i)$                            | Individual value function                                    |                                                              |
| $A_i(\tau_i, a_i)$                       | Individual advantage functions                               | $A_i(\tau_i, a_i) = Q_i(\tau_i, a_i) - V_i(\tau_i)$          |
| $A_{tot}(\boldsymbol{\tau}, \mathbf{a})$ | Joint advantage functions                                    |                                                              |
| $f_{mix}$                                | Mixing function                                              | e.g., QMIX or QPLEX                                          |
| $h_i^t, \mathbf{h}^t$                    | Hidden state                                                 | $\mathbf{h}^t=[h_1^t,\dots,h_n^t]$                           |
| $\mathcal{O}_{-i}^t$                     | Observations set of all agents except $i$ at time $t$        | $$\mathcal{O}_{-i}^t=\{o_j^t\}_{j\neq i}$$                   |
| $\mathcal{O}_{\mathcal{K}}^t$            | Observations partial subset of agents selected for communication | $$\mathcal{O}_\mathcal{K}^t=\{o_j^t\}_{j\in \mathcal{K}}$$   |
| $x_i^t, \mathbf{x}^t$                    | Intermediate representation after communication              | $\mathbf{x}^t=[x_1^t,\dots,x_n^t]$                           |
| $y_{tot}^t$                              | TD target for total Q-value                                  |                                                              |
| $\theta, \theta^-$                       | Online and target network parameters                         |                                                              |
| $d_e$                                    | Dimension of the embedding space                             |                                                              |
| $d_o$                                    | Dimension of the observation space                           |                                                              |
| $\alpha_{ij}^t$                          | Attention weight of agent $i$ to agent $j$ at time $t$       |                                                              |
| $o_i^t$                                  | Observation of agent $i$ at time $t$                         |                                                              |
| $\mathbf{m^t}$                           | Communication message                                        | $\mathbf{m^t}=[o_1^t,\dots,o_n^t]$                           |
| $c_i^t, \mathbf{c}^t$                    | Aggregated communication message                             | $\mathbf{c}^t=[c_1^t,\dots,c_n^t]$                           |
| $W_q, W_k, W_v,W_l$                      | Learnable projection matrices                                |                                                              |
| $\mathcal{K}$                            | Set of communicable neighbor agents                          | Deployment constraint                                        |
| $C$                                      | Information rate                                             |                                                              |
| $B, B'$                                  | Baseline and consumed bandwidth                              |                                                              |
| $S/N$                                    | Signal-to-noise ratio (SNR)                                  |                                                              |
| $k$                                      | Number of selected agents for comms                          | $k \le n$                                                    |
| $b_j, b_{max}$                           | Bit depth assigned and max bit depth                         |                                                              |
| $\bar{r}$                                | Average quantization ratio                                   |                                                              |
| $\eta$                                   | Bandwidth saving efficiency                                  |                                                              |
| $\Delta$                                 | Bound of the message value range                             |                                                              |
| $d$                                      | Dimension of the message                                     |                                                              |
| $m_j, \hat{m}_j$                         | High-precision and quantized messages of agent $j$           | $m_j \in [-\Delta, \Delta]^d$                                |
| $M,\hat{M}$                              | Global high-precision and quantized messages                 | $M=[m_1,\dots,m_n]$                                          |
| $\hat{\alpha}_{ij}$                      | Attention weights using quantized messages                   |                                                              |
| $\mathcal{E}$                            | Global reconstruction error                                  |                                                              |
| $\mathcal{L}$                            | Communication overhead                                       |                                                              |
| $\epsilon_j$                             | Local precision demand of agent $j$                          | Determines bit allocation for agent $j$                      |
