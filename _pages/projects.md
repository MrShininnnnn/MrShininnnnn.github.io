---
layout: projects
title: "Projects"
permalink: /projects/
---
# Natural Language Processing
1. **Colorful Extended Cleanup World** <a href="https://github.com/MrShininnnnn/CECW"><img src="/assets/images/github-alt-brands.svg" width="15px"> GitHub </a>
> **Introduction**
> We published a benchmark, namely, Colorful Extended Cleanup World (CECW), to study synonymous generalization. We hope it can promote the research in related fields, as well as yours.
> **Example Sequence Pairs**
> |                       Command                       | Textual Expression |
> |:----------------------------------------------------|:-------------------|
> |                  go to the red room                 | F R                |
> | go to the red room and then go to the blue room     | F & R F B          |
> | go to red room but do not enter yellow room         | & F R G ! Y        |
> | go through the red or blue room to the yellow room  | F &丨R B F Y       |
> | push the chair from the red room into the blue room | F & R F X          |
> | go to the red room move chair to the green room     | F & R F Z          |

# Reinforcement Learning

1. **Temporal Differences Learning**  <a href="https://github.com/MrShininnnnn/Temporal-Differences-Learning"><img src="/assets/images/github-alt-brands.svg" width="15px"> GitHub </a>
> **Introduction**  
> We reproduced the Figure 3, 4, 5 in Richard Sutton’s 1988 paper *[Learning to Predict by the Methods of Temporal Differences](https://github.com/MrShininnnnn/Temporal-Differences-Learning/raw/master/reference/Learning_to_Predict_by_the_Methods_of_Temporal_Differences.pdf)*. We furthered explored with some assumptions on sequence length and sample duplication.  
> **Original Figures**  
> <p align="center"><img src="https://github.com/MrShininnnnn/Temporal-Differences-Learning/raw/master/img/exp_2.png" alt="Original Figures" width="600" /></p>
> **Reproduced Figures**  
> <p align="center"><img src="https://github.com/MrShininnnnn/Temporal-Differences-Learning/raw/master/img/figure_3.png" alt="Reproduced Figure 3" width="200" /> <img src="https://github.com/MrShininnnnn/Temporal-Differences-Learning/raw/master/img/figure_4.png" alt="Reproduced Figure 4" width="200" /> <img src="https://github.com/MrShininnnnn/Temporal-Differences-Learning/raw/master/img/figure_5.png" alt="Reproduced Figure 5" width="200" /></p>

2. **SARSA Frozen Lake** <a href="https://github.com/MrShininnnnn/SARSA-Frozen-Lake"><img src="/assets/images/github-alt-brands.svg" width="15px"> GitHub </a>
> **Introduction**  
> We trained a SARSA agent to play the Frozen Lake game.
> <p align="center"><img src="https://github.com/MrShininnnnn/SARSA-Frozen-Lake/blob/master/img/frozen_lake_0.png?raw=true" alt="Frozen Lake" width="200" /></p>
> **Random Strategy vs. SARSA Agent**
> <p align="center"><img src="https://github.com/MrShininnnnn/SARSA-Frozen-Lake/blob/master/img/result_img_0.png?raw=true" alt="Random Strategy" width="300" /><img src="https://github.com/MrShininnnnn/SARSA-Frozen-Lake/blob/master/img/result_img_1.png?raw=true" alt="SARSA Agent" width="300" /></p>

3. **DDQN Lunar Lander** <a href="https://github.com/MrShininnnnn/DDQN-Lunar-Lander"><img src="/assets/images/github-alt-brands.svg" width="15px"> GitHub </a>
> **Introduction**  
> We reproduced a Double Deep Q-Network (DDQN) to earn more than +200 reward on average over 100 trials in the game [Lunar Lander](https://gym.openai.com/envs/LunarLander-v2/).
> <p align="center"><img src="https://github.com/MrShininnnnn/DDQN-Lunar-Lander/blob/master/res/Lunar_Lander.gif?raw=true" alt="Lunar Lander"  width="320" /></p>
> <p align="center">(https://gym.openai.com/envs/LunarLander-v2/)</p>
> **Random Agent (Left) vs. Our DDQN Agent (Right)**
> <p align="center"><img src="https://github.com/MrShininnnnn/DDQN-Lunar-Lander/blob/master/res/Random_Agent.gif?raw=true" alt="Random Agent" width="320" /><img src="https://github.com/MrShininnnnn/DDQN-Lunar-Lander/blob/master/res/DDQN_Agent.gif?raw=true" alt="DDQN Agent" width="311" /></p>