# Notes on Intro to RL
 - [https://spinningup.openai.com/en/latest/spinningup/rl_intro.html#](https://spinningup.openai.com/en/latest/spinningup/rl_intro.html#)
 - interestingly, the examples they give aren't really the most impressive RL
   examples. Looks they almost entirely include examples from OpenAI itself...
   IMO most impressive is YouTube recommendation algo (real commercial
   application).  Probably left out due to controversy and/or timing.
 - We assume that state is markov (e.g. MDP/POMDP)
 - Policy: function from state to action
   - deterministic: pick specific action
   - stochastic: distribution over actions
     - Categorical: distribution over fixed discrete states (typically log prob
       is used for scaling reasons)
     - Diagonal Gaussian: used for continuous
        - Sample from multivariate Gaussian with only diagonal entries in the
          covariance matrix.
        - Model maps from state to means.
        - variances can be function of state (e.g. via deep NN) or independent
          parameters which vary in some other way
        - More typical to do standalone parameters for variances (reflects
          exploration, exploitation trade off)
        - What are downsides to only diagonal entries in covariance matrix?
          Seems plausible you could do better at least in theory.
        - This is a very specific parametric approach, are there other sane parametric approaches?
          What about less parametric closer to non-parametric approaches?
        - What are the inductive biases of this approach? (in general, any
          distribution over the full reals must have some sort of reasonably
          strong prior, you can't have non-negligible mass everywhere)
 - Trajectory: sequence of states and actions
 - infinite-horizon discounted return: returns for remainder of time weighted
   by exponential decay
 - Value functions of states:
   - On-Policy Value function: expected return starting in some state and using
     some policy
   - Optimal Value function: expected return starting in some state and using
     optimal policy
   - Also have Action-Value functions (for example On-Policy Action-Value
     function), which is expected return when taking a specific action at that
     state and then following the policy afterword (action doesn't have to
     correspond in any sense to the policy)
 - Bellman equation + bellman backup (maybe memorize this later)
 - advantage function: how much better to take action in some state over a
  policy pi assuming you still use pi afterword
 - model free vs model based:
   - model based builds model of environment which allows for explicit
     planning: then can use distillation like AlphaZero. Ground truth model
     usually not available which makes this worse. If model is biased,
     agent may perform very poorly.
   - I think there are some plausible alignment advantages to model based approaches
   - model-free generally more popular
 - What to learn:
   - policies
   - action-value functions (Q-functions). TODO: what does learning this mean
     in this context?
   - value functions. TODO: what does learning this mean in this context?
   - environment models
 - model free RL what to learn:
   - policy optimization
     - A2C/A3C
     - PPO
     - typically on-policy: updates on performed on recent version of data, maybe less sample efficient
   - Q-Learning
     - DPQ
     - C51 (what's up with the weird number names...)
     - off-policy: updates on all training data
     - can have issues because only indirectly optimizing for perf.
   - possible to interpolate between policy optimization and Q-Learning
     - DDPG
     - SAC
 - TODO: Maybe read more about model based RL later...
 - [simple policy gradient](https://spinningup.openai.com/en/latest/spinningup/rl_intro3.html#deriving-the-simplest-policy-gradient)
   - straight forward derivation
   - intuition is that we weight returns of trajectories by the log probability of the trajectories
   - estimate expectation using sample mean of set of trajectories 
   - possible to subtract out baseline from the reward without changing expectation (might improve performance)
   - common to subtract out the on-policy value function (see above)
   - TODO checkout [generalized advantage estimation](https://arxiv.org/abs/1506.02438)
   - TODO: reread/implement
 - [trust region policy optimization (TRPO)](https://spinningup.openai.com/en/latest/algorithms/trpo.html)
   - largest step to improve performance while holding KL-divergence in policies below some threshold
 - [proximal policy optimization (PPO)](https://spinningup.openai.com/en/latest/algorithms/ppo.html)
   - reduce policy changes without explicit KL-divergence limit (allow trade offs)
   - clipping approach and penalty approach
   - typically clipping approach used

      
# TODO 
 - go back through this and Ankify once my knowledge of importance is more solid.



# Project ideas (beyond simple)
 - Try portfolio agent method (change training approach throughout training 




