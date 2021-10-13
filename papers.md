# Papers

My thoughts on some papers.

## Iterated amplification
 - [https://arxiv.org/abs/1810.08575](https://arxiv.org/abs/1810.08575)
 - Summaries may also be helpful
 - Claim is this allows for creating an agent which "approximates the behavior
   of an exponentially large team of copies of [the human expert]". 

   Is this sufficient for having high capabilities? Are there behaviors which
   can't be reached simply via this large team?  In other words, are there
   behaviors the human won't recognize as good which we want?

 - Note that the paper uses this technique on a variety of toy problems and
   compares to pure supervised learning (which is possible for those problems).

## Learning to summarize from human feedback
 - [https://arxiv.org/abs/2009.01325](https://arxiv.org/abs/2009.01325)
 - Human feedback with reinforcement learning beats predication/imitation. Uses
   reward model (to reduce quantity of feedback needed)
 - Allows for producing superhuman summaries (predication/imitation are worse
   than human and can only get as good, not better)
 - trained via reddit tldr
 - fine tuned gpt-3 style model (fewer params, ~2 Billion and ~7 Billion param models tested)
 - reward model generalizes better than the summary model itself

## Multimodal neurons
 - [https://distill.pub/2021/multimodal-neurons/](https://distill.pub/2021/multimodal-neurons/)
 - Cool paper
 - Looks at CLIP neural net (contrastive language-image pre-training)
 - neurons exist which activate on concepts like 'spiderman' and 'evil' for variety of images and text
 - typographic attacks are worth noting (randomly add text to images to force misclassification)

## Scalable agent alignment via reward modeling
 - [https://arxiv.org/abs/1811.07871](https://arxiv.org/abs/1811.07871)
 - Note that paper is just basic reward modeling background until section 5 on page 12.
 - summary/outline paper
 - ideas:
   - Online feedback  (deals with reward model degenerate behavior that shows
     up frequently in training)
   - off-policy feedback: human feedback on outcomes which don't show up in
     training, typically because they are undesirable (not clear how to do this
     in general)
   - natural language feedback
     - advantages:
       - plausibly denser than other feedback
       - natural for humans
       - may generalize better
       - may be easier to interpret
     - this seems very hard...
   - model based RL: learn a model and use explicit planning algorithm like Monte Carlo tree search
     - explicit planning
     - can get feedback on plan or future actions
     - if training must be online (and with consequences), possible to inspect plan and avoid
   - constraints
     - could be enforced by a separate model
     - theoretically useful when large negative leads to large positive reward
       via reward hacking
     - this approach seems to assume that avoid some large negative rewards at
       any cost can be a good heuristic  (not obvious to me...)
   - adversarial training or finding failure modes more generally
     - plausibly high data cost
     - hard in the general case (e.g. RSA 2048)
   - uncertainty estimation
     - somewhat harder with neural nets than some other approaches
     - could use ensembles, explicitly calibration, or other
   - modify inductive bias to avoid poor behavior
   - I skipped section on other approaches and verifying alignment (maybe better covered elsewhere)
 - recursive reward modeling
   - type of iterated amplification, but with reward modeling instead of
     supervised/imitation learning
   - do error accumulate? or self-correct?
   - assumes that evaluation is easier than doing the thing itself
   - assumes that agents can be useful in further evaluation (unclear exactly how this hierarchy can be built)
 - claim of the overall approach is that good reward model is
   important/valuable approach
 - maybe also weaker claim that other stuff is easy (fulfilling capabilities of
   reward model/inner alignment easier)

## Reward modeling papers (brief)

### Pitfalls of learning reward function online
 - [https://arxiv.org/pdf/2004.13654.pdf](https://arxiv.org/pdf/2004.13654.pdf)
 - goes through some potential issues with online learning for (potentially)
   intelligent agents
 - outlines ideas of unriggability (agent can't make reward function easier
   to optimize) and uninfluencedability (operates by learning fact about
   environment e.g., true reward func)
 - uninfluencedability implies unriggability

### Quantifying differences in reward functions
 - [https://arxiv.org/pdf/2006.13900.pdf](https://arxiv.org/pdf/2006.13900.pdf)
 - builds distance measure for comparing reward functions
 - supposedly not too much computation to accurately approximate
 - claim some advantages vs other approaches
 - distance from optimal should follow reward (some theoretical guarantees)
 - pseudometric
 - could be useful for evaluation without even having to consider policy

### Learning human objectives by evaluating hypothetical behavior
 - [https://arxiv.org/pdf/1912.05652.pdf](https://arxiv.org/pdf/1912.05652.pdf)
 - some other algorithm for learning reward model (supervised?)
 - what is a forward dynamics model? (just predict next state?)
 - so maybe hypothetical behaviors synthesized off-policy?
   - how can that work in general? (typically interesting behaviors occur
    after agent is trained)
 - some sort of approach to guess unsafe states without user query
 - what does it mean to synthesis hypothetical behavior 'from scratch'?
 - where does off-policy data come from?
 - so idea is to construct trajectories to test with high value of information (VOI)
 - can't be computed, so instead we use optimization with several criteria
 - off-policy data used to train generative model (evaluates probs of trajectory)

## Open Questions in Creating Safe Open-ended AI
 - [https://arxiv.org/abs/2006.07495](https://arxiv.org/abs/2006.07495)
 - goes through idea of open ended search for agents (or non-agents)
 - How sensitive is search to initial conditions?
 - How can we control end result of search? Unexpected and hard to predict
   results occur in physical living systems, e.g. ecosystem tampering
 - Can we interpret agents which may have architecture which have been
   searched and aren't human designed? (plausibly much harder than deep NN
   interpretability)
 - How can/should human interact with search (via feedback or similar) to improve results?
 - Simulation reality generalization

## Chris Olah's views on AGI safety
 - benefits of interpretability/transparency (done well) 
   - could catch problems early (probably not with very clever deceptive
     alignment)
   - test how well interpretability/transparency work with adversarial
     games (between humans)
   - could improve design process and understanding
   - use as part of the objective to ensure reasoning is done 'how we want'
     (this seems likely to run into Goodhart type issues).  In other words,
     make 'showing your work' part of the process.
   - model diffing: how do high level representations differ over
     training/between models
 - microscope AI (see tool vs agent concerns above)
 - does interpretability break down?
   - Chris thinks strong interpretability is possible (it's possible to
     turn neural net into large amount of human understandable 'code')
   - currently seems to get easier as models get more powerful (better
     abstractions)
   - plausible it will get harder again as models become superhuman
 - Chris thinks it's possible to direct the ML field more toward deliberate
   design via interpretability (this seems doubtful to me).

## Introduction to circuits
 - [https://distill.pub/2020/circuits/zoom-in/](https://distill.pub/2020/circuits/zoom-in/)
 - focus purely on CNN (do results generalize?)
 - key claim is 'universality': analogous features and circuits form across
   models and tasks
 - thought: if features + circuits model is true, it shouldn't be that hard to
   trim down/modify neural net to make it more computationally efficient
   (probably needing to retrain for a bit afterword).  It also shouldn't be too
   hard to modify how recognition is done (avoid correlations we don't want for
   example, like arm with dumbbell example)
 - features involve union of many poses/orientations with some fuzziness 
 - polysemantic neurons can correspond to many things making interpretability harder
   (maybe less likely to exist in bigger/more over-parameterized neural nets?)
 - article doesn't make a strong case for universality, but the claim seem plausible to me

## Open problems is cooperative AI
 - [https://arxiv.org/abs/2012.08630](https://arxiv.org/abs/2012.08630)
 - example problem: autonomous cars, may have many agents interacting
 - Is this concerned with AI in the colloquial sense (decently advanced ML systems) or with transformative AI/AGI?
 - Needed capabilities:
   - Understanding other agents
   - Communication
   - Commitments: eliminating/reducing incentives to renege on agreements (e.g. iterated prisoners dilemma)
   - institutions (seems somewhat orthogonal to the above which are basically agent capabilities)
 - the little drawing they use for people are kind of absurd...
 - individual vs planner prospective (from AGI point of view, seems clear to me
   that we converge to planner regardless)
 - institutions maybe can select equilibrium (not clear to me that this notion of an institution is useful for AGI, plausibly for transformative AI)
 - cooperation may require same beliefs/predictions (NOTE: by aumann's agreement theorem, agents can maybe come to the same beliefs - requires trust)
 - maybe shared understanding of superrationality is useful
 - changing equilibrium likely to be harder
 - didn't read further, decided wasn't good use of time

## Proximal Policy Optimization Algorithms
 - [https://arxiv.org/abs/1707.06347](https://arxiv.org/abs/1707.06347)
 - Why is TRPO not compatible with noise or parameter sharing (read paper
   eventually)?
 - Alternation between sampling and multiple epochs of optimization? So we can
   (and maybe should) optimize off-policy? (see * for answer)
 - multiple versions of surrogate objective (analogous to reward shaping), but
   clip empirically is best
 - Multiple optimization steps on same trajectory can work with policy
   gradient, but doesn't work empirically (over updates) *
 - Pretty simple, we just clip on ratio
 - also, we can train policy with multiple steps of gradient descent by
   making sure to stop when KL is over some threshold. Standard sample efficiency
   vs performance trade-offs apply of course.
 - Nothing too complicated.

## GAE
 - [https://arxiv.org/abs/1506.02438](https://arxiv.org/abs/1506.02438)
 - simple approach for estimating advantage using exponentially weighted sum of
   TD-residual
 - should be lower variance (with some bias)
 - we have to eat bias regardless due to how value function is generally
   estimated
 - a decent amount of time spent on derivation, but I think intuition is
   reasonably clear

## Learning from human preferences
 - [https://arxiv.org/abs/1706.03741](https://arxiv.org/abs/1706.03741)
 - standard rl, but with supervised reward function estimate
   (important question: do they use policy/value function model for reward
   function too?)
   - I think answer to question is no, but I don't recall seeing it in the
     paper anywhere.
   - It doesn't seem to me like sharing params is a good idea given that
     training is totally separate (probably hard to mix batching as would be
     probably important with standard SGD)
 - reward model is latent factor explaining human preference
 - preference probability depends exponentially on sum of
   this latent reward
   - just elo system (preferences instead of wins)
   - standard approach used in previous papers
 - depending exponentially is nice for a few reasons:
   - allows for factoring out states/actions which give same reward
   - maybe has nice interpolation? (not sure)
   - maybe matches actual empirical preference probabilities?
 - NOTE: see simple modifications
 - lol, 1/e proportion of data used for validation
 - need to assume always 10% error chance in rating
 - queries for human rater selected based on ensemble empirical
   uncertainty. (maybe doesn't perform all that well)
   - ideally should sample based on expected value of information
   - could use a different approach for uncertainty (really we just want
     relative uncertainty, we only care about which is the most uncertain)
   - take a look at later similar works (summarization...) to see if any
     updates in the method
 - how did they queue up the trajectories back to back?
 - how many epochs for supervised reward model?

## Fine tuning language models from human feedback
 - [https://arxiv.org/abs/1909.08593](https://arxiv.org/abs/1909.08593)
 - fine tuning with kl penalty originally comes from earlier paper
 - tasks:
   - continue text and match style
   - summarization (I think this goes poorly/degenerates due to human feedback)
 - online vs offline data collection
   - similar for style
   - online better for summarization
 - reward model uses originally pretrained model as base (to avoid weight
   corruption presumably). Section 4.2 claims this is to avoid overfitting, but
   actually its not exactly clear this was the issue based on what they say.
 - same exponential/elo loss as in learning from human preferences 
 - online data collection is hard
   - complex software with many parts that can break
   - hard to debug
   - need to filter out poor labellers soon?
 - lol, section 4.4...
 - [some of the code](https://github.com/openai/lm-human-preferences)


## Summarization from Human Feedback
 - [https://arxiv.org/abs/2009.01325](https://arxiv.org/abs/2009.01325) 
 - TLDR dataset from reddit
 - standard summary length
 - reward model is trained totally offline! (on human summaries and on
   supervised output)
 - to avoid issues with overfitting reward model, loss minimizes
   KL divergence from supervised model
   - this probably handicaps model considerably
   - but, if dataset is accessible, should be easier to reproduce their
     results
 - value function with separate params from policy (presumably also
   pretrained)
   - claim is that this is to avoid destroying the pretrained
     policy
   - unclear if how much other stuff they tried (e.g., param freezing etc.)
 - TODO: go over again (mostly just read methods and skimmed results)


## TODO
 - recall exact encoder decoder language model structure for GPT/BeRT
 - [circuits papers](https://distill.pub/2020/circuits/) (distill analysis of single neural net)
 - [understanding RL vision](https://distill.pub/2020/understanding-rl-vision/) (maybe some good projects along these lines...)
 - [Evaluating Arguments One Step at a Time](https://ought.org/updates/2020-01-11-arguments)
   - experiment with humans along the lines of ai safety via debate (but
     trying to evaluate sub claims: test distributing the work)


