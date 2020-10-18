---
title: Understanding Q-Learning - No Neural Nets Here!
updated: 2020-10-18 23:37
tags: 100DaysOfMLCode
category: 
- Reinforcement Learning
---

The algorithm we are going to discuss does not use any black-box *Deep-Q-Networks*. Instead, we use Q-Table which more interpretable and elegant in it's own way. I tried to make this blog as short as possible with simple terminology to make sure it is reader-friendly and cover important concepts only. Nothing more. Nothing less. Happy Reading!

<div class="divider"></div>

<p align="center">
    <img src="assets/blogs/rf/after.gif">
</p>

## Basics First 

We need two main things for our algorithm - one, an Environment and two, an Agent

### 1. Environment

*For brevity, let us consider a maze as our environment and a payer-bot as an agent which can make some moves.*

States in an environment are the places where a player-bot can be. For example, in a 5x5 maze environment, there are 25 states where an agent can be at any point of time and can perform any action - `ArrowUp`, `ArrowDown`, `ArrowLeft` and `ArrowRight`. 

For any given **action as input** to an environment, we get set of **{observations, reward} as output** 

![](assets/blogs/rf/env.png)

Make sure to remember that in our maze environment, observation is the next-state agent goes to because performing input action in the environment. 

Reward of input action can be positive or negative or zero. In our case, 

- If player-bot falls in a pit reward is `-1`
- If it reaches destination, reward is `+1`
- Otherwise, no reward i.e reward is `0`

![](assets/blogs/rf/enveg.png)

> There will be some states in environment leading to the end of the game - either by winning or by losing. When reaching that state, environment must reset. Let us call these states **Terminal States**

### 2. Agent

Agent has two main funtions - making actions and learning.

#### A. Making Actions (Output of Agent)

Agent can make any of the actions mentioned above. It can either explore (make moves randomly) or exploit (make best moves). While training, moves are more random which generate optimal Q-Table (we will talk about in next section). For making best moves, Q-Table is used.

![](assets/blogs/rf/agent_action.png)


#### B. Learning (Input of Agent)

This is the most important function of an agent. An agent in Q-Learning algorithm learns based on following

- State `S` agent was in while making action `A`
- Reward of action `R`
- Next state `S_NEW` the agent moved to because of the action `A`


![](assets/blogs/rf/agentlearn.png)

> **Note:** we will discuss more about `Learn` in later sections


So, the full framework with both Environment and Agent looks as follows

![](assets/blogs/rf/qlearn.png)


On a high level, this is how Q-Learning works. But magic happens inside agent's `Learn` method dicussed below.


<div class="divider"></div>


## How Does an Agent Learn?

Before answering that question, we must answer <i>"**What** does an agent learn?</i> Answer is Q-Table.

Q-Table in simple terms tell agent **what action to perform while at any given state.**

> In a Q-Table, rows represent all possible states and columns represent the possible actions. Best action for
> any state is the action with highest Q-Value. 
>
> For example, when agent is at position / state `(0,0)` the best possible action it can perform is `ArrowRight` because it has
> highest value of `0.53`. Note that `ArrowDown` with `0.51` is not a bad choice; It is just not better. 
>
> ![A](assets/blogs/rf/qtable.png)
> 

After training (50 games in our case), exploiting the Q-Table will give the following actions wrt their states for a 5x5 maze.

![](assets/blogs/rf/bestmoves.png)


## Driving Mathematics Under The Hood 


The agent's `Learn` method creates / populates the Q-Table discussed above. It takes the following as inputs

- Output of environment for any iteration `R` and `S_new`
- The previous state `S` of Agent `A` and and the action it performed while at that state

Initially, before the training starts, Q-Table is initialized with all zeros. Then, using the following equation, the values are altered for every move the agent makes.

When agent makes action `A` while at state `S`, `A`th column in `S`th row in Q-Table is updated using:

$$
\text{Q}_{new} \,\, = \,\, \text{Q}_{old} \,\, + \,\, \alpha \,\, (\text{update-term})
$$

where $$\alpha$$ is learning rate. The update-term when `S_new` is not a terminal state is -

$$
\text{update-term} \,\, = \,\, \text{reward-term} \,\, - \,\, \text{Q}_{old}
$$

- In short, $$- \,\, \text{Q}_{old}$$ makes sure that $$\text{Q}_{new}$$ never gets greater than or lesser than the reward agent gets for it's actions.

- The reward-term is quite simple. It is the sum of immediate reward `R` and best Q-value for next state `S_new` reduced by a factor $$\gamma$$. The reduction factor makes sure that immediate reward is more important than the future reward.

So, the complete update equation when `S_new` is not a terminal state is

$$
\text{Q}_{new} \,\, = \,\, \text{Q}_{old} \,\, + \,\, \alpha \,\, \bigg[ R \,\,+\,\, \bigg( \gamma * \text{Max}(\text{Q}_{S_{new}}) \bigg) \,\,-\,\, \text{Q}_{old} \bigg]
$$

And when `S_new` is a terminal state, there is no next move. Consequently, the reward-term does not need to care about best Q-value for next state `S_new`. As a result, the complete update equation when `S_new` is a terminal state is

$$
\text{Q}_{new} \,\, = \,\, \text{Q}_{old} \,\, + \,\, \alpha \,\, \bigg[ R \,\,-\,\, \text{Q}_{old} \bigg]
$$

Generally, `0.9` is a good choice for $$\alpha$$ and $$\gamma$$ 

> Q-Values are exactly like rewards but created artificially by the update equations even if the reward for that state is zero.
>
> The more agent explores (random moves) the better will be Q-Table as it is generated **bottom-to-top** i.e updates in Q-Table is made first for the regions (terminal states) where reward is maximum / minimum and then slowly covers all states based on exploration and closeness to those terminal states.


<div class="divider"></div>

## Finally

This not in-depth explanation of Q-Learning algorithm but give fair understanding of how Q-Learning and reinforcement learning in general work. If you are planning to get your hands dirty, check out my implementation [here](https://github.com/rakesh4real/game-one) try to tweak the code and play with it. Feel free to reach out to me if you have any comments, doubts, question or suggestions via [twitter](https://twitter.com/inf800)

Thank you for reading this blog :)