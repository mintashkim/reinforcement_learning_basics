# SARSA

As we can see in a diagram 4.14, policy iteration and value iteration develops into SARSA.
From now on, we can proudly say that we are actually working on the 'reinforcement learning' algorithm.
Let's see how policy iteration and value iteration turn into SARSA, and how does an agent learns through reinforcement learning such as SARSA.
  
Policy iteration is an alternation of "policy evaluation" and "policy improvement".
An agent finds value function by evaluation using current policy and greedily improves the policy using the value function.
Policy evaluation is to find a true value function for the current policy and policy improvement is to update the policy with the value function gained from evaluation.
  
One thing we have to notice is that the value function eventually converges to its true value if evaluation and improvement alternate throughout policy iteration, even it does not through a single evaluation.
This is called GPI(generalized policy iteration), which means the alternation of evaluation through the Bellman equation and greedy improvement.
In reinforcement learning, policy evaluation is conducted by using Monte Carlo prediction or temporal difference prediction.
Let's consider policy evaluation through temporal difference prediction.
Greedy policy improvement is a process in GPI which obtains a new policy from a given value function.
However, in temporal difference method, it updates a value function regarding cureent state.
Thus, it is impossible to improve every single policy for each state unlike GPI.
