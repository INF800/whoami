---
title: Understanding Q Learning - No Neural Nets Here!
updated: 2020-10-19 04:37
tags: 100DaysOfMLCode
category: 
- Reinforcement Learning
---

> Draft version 

Q-Learning does not use any black-box neural networks aka *Deep Q-Networks*. Instead, it uses Q-Table which makes Q-Learning more interpretable and elegant in it's own way. This blog is a brief introduction to Q-Learning.

<div class="divider"></div>

<p style="text-align: center">
    <img src="assets/blogs/rf/after.gif"> <br/>
    Implementation of Q-Learning <a href="https://github.com/INF800/game-one">with code</a>
</p>

## Basics First 

Q-Learning or reinforcement learning in general need two basic components to start with - one, an **Environment** and two, an **Agent**.

### 1. Environment

*For brevity, let us consider a maze as our environment and a payer-bot as an agent which can make some moves.*

States in an environment are the places where a player-bot can be. For example, in a 5x5 maze environment, there are 25 states where an agent can be at any point of time and can perform any action - `ArrowUp`, `ArrowDown`, `ArrowLeft` and `ArrowRight` being at that state. 

For any given **action as input** to an environment, we get set of **{observations, reward} as output** 

![](assets/blogs/rf/env.png)

Make sure to remember that in our maze environment, observation is the next-state the agent goes to because of performing input action in the environment. 

Reward of input action can be positive or negative or zero. In our case, 

- If player-bot falls in a pit reward is `-1`
- If it reaches destination, reward is `+1`
- Otherwise, no reward i.e reward is `0`

![](assets/blogs/rf/enveg.png)

> There will be some states in the environment leading to the end of the game - either by winning or by losing. When reaching that state, environment must reset. Let us call these states **Terminal States**

### 2. Agent

Agents have two main functions - making actions and learning.

#### A. Making Actions (Output of Agent)

An agent can make any of the actions mentioned above. It can either explore (make moves randomly) or exploit (make best moves). While training, moves are more random which generate optimal Q-Table (we will talk about in next section). For making best moves, Q-Table is used.

![](assets/blogs/rf/agent_action.png)


#### B. Learning (Input of Agent)

This is the most important function of an agent. An agent in Q-Learning algorithm learns based on following

- State `S` agent was in while making action `A`
- Reward of action `R`
- Next state `S_NEW` the agent moved to because of the action `A`


![](assets/blogs/rf/agentlearn.png)

> **Note:** We will discuss more about `Learn` in later sections. Remember what `S`, `A`, `R` and `S_new` stand for as they will be used extensively later.


So, the full framework with both Environment and Agent looks as follows

![](assets/blogs/rf/qlearn.png)


On a high level, this is how Q-Learning works. But magic happens inside the agent's `Learn` method explianed below.


<div class="divider"></div>


## How Does an Agent Learn?

Before answering that question, we must answer <i>"**What** does an agent learn?</i> Answer is Q-Table.

Q-Table in simple terms tells the agent **what action to perform while at any given state.**

> In a Q-Table, rows represent all possible states and columns represent the possible actions. Best action for
> any state is the action with highest Q-Value. 
>
> For example, when an agent is at position / state `(0,0)` the best possible action it can perform is `ArrowRight` because it has the
> highest value of `0.53`. Note that `ArrowDown` with `0.51` is not a bad choice; It is just not better. 
>
> ![A](assets/blogs/rf/qtable.png)
> 

After training (50 games in our case), exploiting the Q-Table will give the following *"best-actions"* wrt their states for a 5x5 maze.

![](assets/blogs/rf/bestmoves.png)


## Driving Mathematics Under The Hood 


The agent's `Learn` method creates / populates the Q-Table discussed above. It takes inputs mentioned in **2-B**.

Initially, before the training starts, Q-Table is initialized with all zeros. While training, we must make sure that all state-action pairs' Q-Values in Q-Table are increased from zero / decreased from zero suitably. Which is taken care of by the update rule below. Using the following equation, the Q-Values are altered for every move the agent makes.

When agent makes action `A` while at state `S`, `A`th column in `S`th row in Q-Table is updated using:

$$
\text{Q}_{new} \,\, = \,\, \text{Q}_{old} \,\, + \,\, \alpha \,\, (\text{update-term})
$$


### Designing the update-term

We know that reward is positive `+1` for best moves and `-1` for worst moves. And it is zero otherwise. So, if we set update-term as the immediate reward `R` we get from environment, 

$$
\text{update-term} \,\, = \,\, \text{R}
$$

There is a catch here. We are only considering immediate rewards. How can we incorporate future rewards as well? As we have `S_new` with us (and can lookup the latest Q-Table at any point of time), we can add the best i.e maximum possible Q-Value associated with `S_new` to immediate reward assuming that Q-Values behave just as rewards. So, the new reward term looks like - 

$$
\text{update-term} \,\, = \,\, \text{R} \,\, + \,\, \text{MaxQ}_{S_{new}}
$$

Wait, there is another catch here! Are the immediate and future rewards equally important? No. Immediate reward is more important. So decrease the future reward by a factor $$\gamma \in [0, 1]$$. 

$$
\text{update-term} \,\, = \,\, \text{R} \,\, + \,\, \gamma * \text{MaxQ}_{S_{new}}
$$

One final modification. We assumed that Q-Values act just like rewards. But if we use above update-term, the range of $$\text{Q}_{new}$$ will be greater/lesser than the range of rewards [-1, +1]. To make sure ranges are consistent, we subtract old Q-Value from reward term.

$$
\text{update-term} \,\, = \,\, \text{R} \,\, + \,\, \gamma * \text{MaxQ}_{S_{new}} \,-\, \text{Q}_{old}
$$



- In short, $$- \,\, \text{Q}_{old}$$ makes sure that $$\text{Q}_{new}$$ never gets greater than or lesser than the reward agent gets for it's actions.

- The reward-term is quite simple. It is the sum of immediate reward `R` and best Q-value for next state `S_new` reduced by a factor $$\gamma$$. The reduction factor makes sure that immediate reward is more important than the future reward.


And finally, *if and only if* `S_new` is a **terminal state**, there is no next move. Consequently, the reward-term does not need to care about best Q-value for next state `S_new` i.e we can ignore $$(\gamma * \text{MaxQ}_{S_{new}})$$. As a result, the complete update equation when `S_new` is a terminal state is

$$
\text{Q}_{new} \,\, = \,\, \text{Q}_{old} \,\, + \,\, \alpha \,\, \bigg[ R \,\,-\,\, \text{Q}_{old} \bigg]
$$

Generally, `0.9` is a good choice for $$\alpha$$ and $$\gamma$$ 

> Q-Values are exactly like rewards but created artificially by the update equations even if the reward for that state is zero.
>
> The more agent explores (makes random moves) the better will be Q-Table as it is generated **bottom-to-top** i.e updates in Q-Table is made first for the regions (terminal states) where reward is maximum / minimum and then slowly, all states are covered based on exploration and proximity to those terminal states.


<div class="divider"></div>

## Conclusion

This not in-depth explanation of Q-Learning algorithm but give fair understanding of how Q-Learning and reinforcement learning in general work. If you are planning to get your hands dirty, check out my implementation [here](https://github.com/INF800/game-one) try to tweak the code and play with it. Feel free to reach out to me if you have any comments, doubts, questions or suggestions via <span onclick="window.location='https://twitter.com/inf800'" class="iconify" data-icon="fa-brands:twitter" data-inline="false"></span>
[twitter](https://twitter.com/inf800)


<blockquote class="twitter-tweet"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/Day2?src=hash&amp;ref_src=twsrc%5Etfw">#Day2</a> of <a href="https://twitter.com/hashtag/100DaysOfMLCode?src=hash&amp;ref_src=twsrc%5Etfw">#100DaysOfMLCode</a> 🤗<br>Topic: Implementation of Q-Learning from scratch using <a href="https://twitter.com/hashtag/numpy?src=hash&amp;ref_src=twsrc%5Etfw">#numpy</a>, <a href="https://twitter.com/hashtag/reactjs?src=hash&amp;ref_src=twsrc%5Etfw">#reactjs</a> and <a href="https://twitter.com/hashtag/fastapi?src=hash&amp;ref_src=twsrc%5Etfw">#fastapi</a> 🐍<br><br>Blog: <a href="https://t.co/QrWgA6m7wx">https://t.co/QrWgA6m7wx</a><br>Code: <a href="https://t.co/DaciGR8TVN">https://t.co/DaciGR8TVN</a> <a href="https://t.co/zPiOHT0Uyv">pic.twitter.com/zPiOHT0Uyv</a></p>&mdash; Asapanna Rakesh (@inf800) <a href="https://twitter.com/inf800/status/1318051084993060865?ref_src=twsrc%5Etfw">October 19, 2020</a></blockquote> 

Thank you for reading this blog :)
