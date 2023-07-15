# Policy Iteration

Once a policy, has been improved using to yield a better policy, we can then compute ![](inimgtmp731.png) and improve it again to yield an even better ![](inimgtmp732.png). We can thus obtain a sequence of monotonically improving policies and value functions:  
  

![](imgtmp35.png)

  
where ![](inimgtmp733.png) denotes a policy _evaluation_ and ![](inimgtmp734.png) denotes a policy _improvement_. Each policy is guaranteed to be a strict improvement over the previous one (unless it is already optimal). Because a finite MDP has only a finite number of policies, this process must converge to an optimal policy and optimal value function in a finite number of iterations.

This way of finding an optimal policy is called _policy iteration_. A complete algorithm is given in Figure  [4.3](node43.html#fig:policy-iteration). Note that each policy evaluation, itself an iterative computation, is started with the value function for the previous policy. This typically results in a great increase in the speed of convergence of policy evaluation (presumably because the value function changes little from one policy to the next).

**Figure 4.3:** Policy iteration (using iterative policy evaluation) for ![](inimgtmp735.png). In the "![](inimgtmp736.png)" step in 3, it is assumed that ties are broken in a consistent order.

 ![](pseudotmp1.png)

Policy iteration often converges in surprisingly few iterations. This is illustrated by the example in Figure  [4.2](node41.html#fig:4gridconv). The bottom-left diagram shows the value function for the equiprobable random policy, and the bottom-right diagram shows a greedy policy for this value function. The policy improvement theorem assures us that these policies are better than the original random policy. In this case, however, these policies are not just better, but optimal, proceeding to the terminal states in the minimum number of steps. In this example, policy iteration would find the optimal policy after just one iteration.

**Example 4.2: Jack's Car Rental**   Jack manages two locations for a nationwide car rental company. Each day, some number of customers arrive at each location to rent cars. If Jack has a car available, he rents it out and is credited $10 by the national company. If he is out of cars at that location, then the business is lost. Cars become available for renting the day after they are returned. To help ensure that cars are available where they are needed, Jack can move them between the two locations overnight, at a cost of $2 per car moved. We assume that the number of cars requested and returned at each location are Poisson random variables, meaning that the probability that the number is ![](inimgtmp737.png) is ![](inimgtmp738.png), where ![$\lambda $](img1.png) is the expected number. Suppose ![$\lambda $](img1.png) is 3 and 4 for rental requests at the first and second locations and 3 and 2 for returns. To simplify the problem slightly, we assume that there can be no more than 20 cars at each location (any additional cars are returned to the nationwide company, and thus disappear from the problem) and a maximum of five cars can be moved from one location to the other in one night. We take the discount rate to be ![](inimgtmp739.png) and formulate this as a continuing finite MDP, where the time steps are days, the state is the number of cars at each location at the end of the day, and the actions are the net numbers of cars moved between the two locations overnight. Figure  [4.4](node43.html#fig:jacks) shows the sequence of policies found by policy iteration starting from the policy that never moves any cars.

![](QED.png)

  

**Figure 4.4:** The sequence of policies found by policy iteration on Jack's car rental problem, and the final state-value function. The first five diagrams show, for each number of cars at each location at the end of the day, the number of cars to be moved from the first location to the second (negative numbers indicate transfers from the second location to the first). Each successive policy is a strict improvement over the previous policy, and the last policy is optimal.

  

**Exercise 4.4 (programming)**   Write a program for policy iteration and re-solve Jack's car rental problem with the following changes. One of Jack's employees at the first location rides a bus home each night and lives near the second location. She is happy to shuttle one car to the second location for free. Each additional car still costs $2, as do all cars moved in the other direction. In addition, Jack has limited parking space at each location. If more than 10 cars are kept overnight at a location (after any moving of cars), then an additional cost of $4 must be incurred to use a second parking lot (independent of how many cars are kept there). These sorts of nonlinearities and arbitrary dynamics often occur in real problems and cannot easily be handled by optimization methods other than dynamic programming. To check your program, first replicate the results given for the original problem. If your computer is too slow for the full problem, cut all the numbers of cars in half.

_**Exercise 4.5**_   How would policy iteration be defined for action values? Give a complete algorithm for computing ![](inimgtmp740.png), analogous to Figure  [4.3](node43.html#fig:policy-iteration) for computing ![](inimgtmp741.png). Please pay special attention to this exercise, because the ideas involved will be used throughout the rest of the book.

_**Exercise 4.6**_   Suppose you are restricted to considering only policies that are _![](inimgtmp742.png)\-soft_, meaning that the probability of selecting each action in each state, ![](inimgtmp743.png), is at least ![](inimgtmp744.png). Describe qualitatively the changes that would be required in each of the steps 3, 2, and 1, in that order, of the policy iteration algorithm for ![](inimgtmp745.png) (Figure  [4.3](node43.html#fig:policy-iteration)).

* * *

[![next](next.png)](node44.html) [![up](up.png)](node40.html) [![previous](prev.png)](node42.html) [![contents](contents.png)](node1.html)  
**Next:** [4.4 Value Iteration](node44.html) **Up:** [4\. Dynamic Programming](node40.html) **Previous:** [4.2 Policy Improvement](node42.html)   **[Contents](node1.html)**

Mark Lee 2005-01-04
