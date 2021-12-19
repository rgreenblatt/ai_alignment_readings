# Papers

My thoughts on some papers.

## Iterated amplification

- [https://arxiv.org/abs/1810.08575](https://arxiv.org/abs/1810.08575)
- Summaries may also be helpful
- Claim is this allows for creating an agent which "approximates the behavior
  of an exponentially large team of copies of [the human expert]".

  Is this sufficient for having high capabilities? Are there behaviors which
  can't be reached simply via this large team? In other words, are there
  behaviors the human won't recognize as good which we want?

- Note that the paper uses this technique on a variety of toy problems and
  compares to pure supervised learning (which is possible for those problems).

## My Understanding of Paul Christiano's Iterated Amplification AI Safety Research Agenda

- [https://www.lesswrong.com/posts/PT8vSxsusqWuN7JXp/my-understanding-of-paul-christiano-s-iterated-amplification](https://www.lesswrong.com/posts/PT8vSxsusqWuN7JXp/my-understanding-of-paul-christiano-s-iterated-amplification)
- maybe see also critique from yudkowsky
- claims approach is slow
- unclear if idealised even works at all (idealized is HCH)
- maybe IDA is just useful for finding tools useful for building aligned ai
  (instead of the aligned ai itself)
- aiming for 'intent alignment' (trying to do what we want) and competent
- solves 'intent alignment' via corrigibility (which maybe mostly implies
  intent alignment)
- maybe corrigibility easier than other approaches to alignment:
  - doesn't require early competence in inferring prefs
  - stable
  - notation of 'broad basin of attraction'
- idealized version called HCH: infinitely large exponential stack of humans
  which stabilizes to 'something'
  - might not be safe
  - might not be powerful (if can't be subdivided)
  - intractable
  - is corrigible
- we need 'informed oversight':
  - overseer must be aware of intentions + beliefs
  - to avoid:
    - unintended consequences
    - actions just to gain trust
- how could this fail:
  - can't be implemented competitively
  - HCH doesn't do what we need:
    - power
    - corrigible

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
- Note that paper is just basic reward modeling background until section 5 on
  page 12.
- summary/outline paper
- ideas:
  - Online feedback (deals with reward model degenerate behavior that shows up
    frequently in training)
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
  - model based RL: learn a model and use explicit planning algorithm like
    Monte Carlo tree search
    - explicit planning
    - can get feedback on plan or future actions
    - if training must be online (and with consequences), possible to inspect
      plan and avoid
  - constraints
    - could be enforced by a separate model
    - theoretically useful when large negative leads to large positive reward
      via reward hacking
    - this approach seems to assume that avoid some large negative rewards at
      any cost can be a good heuristic (not obvious to me...)
  - adversarial training or finding failure modes more generally
    - plausibly high data cost
    - hard in the general case (e.g. RSA 2048)
  - uncertainty estimation
    - somewhat harder with neural nets than some other approaches
    - could use ensembles, explicitly calibration, or other
  - modify inductive bias to avoid poor behavior
  - I skipped section on other approaches and verifying alignment (maybe better
    covered elsewhere)
- recursive reward modeling
  - type of iterated amplification, but with reward modeling instead of
    supervised/imitation learning
  - do error accumulate? or self-correct?
  - assumes that evaluation is easier than doing the thing itself
  - assumes that agents can be useful in further evaluation (unclear exactly
    how this hierarchy can be built)
- claim of the overall approach is that good reward model is important/valuable
  approach
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
- so they do just use random policies (isn't that likely to be very weak in
  exploration?)
- embed states for easier optimization via VAE
- classify states with straight forward labels
- 'acquisition function': how useful human feedback on trajectory would be
  - maximize reward model uncertainty (logits are close)
  - maximize predicted reward (focus on things which are supposed to be really good)
  - minimize predicted reward (focus on unsafe)
  - novelty: maximize euclidean distance between state embeddings
- query trajectory optimizes acquisition function + log prob (to ensure
  probable trajectory is selected)
- model based control using forward predictor needed for training reward model
- ok, so actually not that much going on... (probably not very general
  approach...)

### PEBBLE: Feedback-Efficient Interactive Reinforcement Learning via Relabeling Experience and Unsupervised Pre-training

- improving sample efficiency
- pre-train with unsupervised exploration (intrinsic motivation) prior to building reward
  model to improve efficiency (how much does this actually matter in practice?)
- use reward model off-line as well for off-policy training: relabel experience
- standard preference between clips from teacher
- why does off-policy matter for improving sample efficiency from perspective
  of human? (having trained reward model is supposed to fix this...)
  - claims this improves things a lot
  - presumably, issue is that on-policy with low sampling rate overfits to
    reward model
  - so then reward model generalization is less of an issue when
    just relabeling previous experiences which are part of the labeled
    distribution
- train using SAC for off policy!
- exact same formulation of reward model loss from learning from human prefs
- ensemble disagreement basically seems best...
- not much too this paper, feel like it could have been TL DR...
- should probably implement something like this for my projs

### B-Pref: Benchmarking preference-base reinforcement learning

- benchmark for preference-based RL
- simulates teachers with varying degrees of irrationality
- metrics based on robustness to this
- assumes choices are:
  - invalid/no ordering
  - equal
  - left/right better
- approach looks like:
  - have some \delta for rewards too close.
  - if max trajectory total reward too low, skip
  - if trajectory total rewards close (within \delta), equal pref
  - otherwise, find which is better (but with stochastic irrationality model)
    and finally make mistake with prob \epsilon
- to find out which is better, rewards are discounted extra and we use \beta
  irrationality coeff as inverse softmax temperature: everything gets close
  with small \beta, small differences pulled apart with large \beta
  (why didn't they just call it softmax temp...)
- rationality coeff just how 'discerning' agent is (as its softmax temp)
- consider normalized returns
- test variety of teachers with/without various failures to check robustness. examples:
  - myopic has extra discount
  - stoc likely to mislabel with high temp
  - etc
- just compare orig to PEBBLE (same authors, so a touch incestuous, but hey, it's academia...)
- should probably check this for my projs


### Active Preference-based learning of reward functions

- again, active learning, where trajectories selected for labeling
- trajectory synth
- assumes fixed d-dimensional feature function and then forces reward function
  to be inner product of this feature and a learned weight (at least pretty sure \phi is fixed)
- so this is why this doesn't work in the general case: this model is FAR too
  constrained (typically we learn reward model as deep function, but this requires a linear reward model
  on some fixed feature!) Maybe possible to learn feature and then re update multipliers?
  (but it does seem like all the juice is in the reward model...)
- so probably can't be used for atari/backflip/etc
- but constrained approach allows for reasoning about bayesian update with
  uniform prior
- Ok, so this is basically not general and not useful in practice.
- but if you can reduce to this case, it is possible to do some well-founded
  optimization with PRoVen gUaRAnTEes (with cool stuff like volume removal from
  the hypothesis space)
- Not reading in more detail, because I now know why this isn't worthwhile


### Reward-rational (implicit) choice: A unifying formalism for reward learning

- human leaks preferences via actions (turning off robot in various cases,
  pushing robot, etc.)
- way to interpret all info (actions, suggestions, direct prefs) in unifying
  formalism
- consider every action as a reward-rational implicit choice:
  - choice from implicit set of options
  - approximately rational for reward
- possible to make sense of behavior via:
  - knowing set of options
  - knowing (intended) effect of these options on robot behavior (paper doesn't
    use intended, but that is actually needed right? e.g. IRL)
- can be hard to get grounding or set of options, (though sometimes easy)
- model choice via 'Boltzmann-rational' policy (same standard softmax approach
  with rationality constant \beta)
  - apparently this is max-ent, huh
- TODO: maybe reread in a sec



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
    (this seems likely to run into Goodhart type issues). In other words,
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
  (probably needing to retrain for a bit afterword). It also shouldn't be too
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
  (and maybe should) optimize off-policy? (see \* for answer)
- multiple versions of surrogate objective (analogous to reward shaping), but
  clip empirically is best
- Multiple optimization steps on same trajectory can work with policy
  gradient, but doesn't work empirically (over updates) \*
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

## Truthful question answering/changing biases of pretrained models

### TruthfulQA

- truthful question dataset
- also train GPT-judge as metric for success on dataset (ideally don't just fit
  to GPT-judge...)
- test various prompts and look at truthfulness perf of existing language models
- size doesn't necessarily improve perf

### Papers in this area to read

- [Queens are powerful too](https://arxiv.org/abs/1911.03842): reduce gender
  bias in model via changing training
- [Understanding capabilities, limitation, impact of models](Understanding capabilities, limitation, impact of models)
- [Recipes for safety in open-domain chatbots](https://arxiv.org/abs/2010.07079)
- [Process for Adapting Language Models to Society (PALMS)](https://cdn.openai.com/palms.pdf)
- [FEVEROUS: Fact Extraction and VERification Over Unstructured and Structured information](https://arxiv.org/abs/2106.05707)
- (also note that language model learning from human prefs is relevant here)
- Should probably be more? (I haven't looked too carefully...)
- generally looking at redwood research proj

## Cooperative Inverse Reinforcement Learning (CIRL)

- [https://arxiv.org/abs/1606.03137](https://arxiv.org/abs/1606.03137)
- robots payoff is actual human reward
- robots distribution over reward model parameters is sufficient statistic
- optimal (or at least better) teaching is important (e.g., finding important
  sample to train on)
- apprenticeship is type of cirl
- recommend approach of 'converge to right purpose over training' (learn purpose)

## Understanding RL vision

- [https://distill.pub/2020/understanding-rl-vision/](https://distill.pub/2020/understanding-rl-vision/)
- uses attribution (apparently standard approach?, look into this) and
  dimensionality reduction (e.g. PCA)
- requires procedural generation
- evidence for 'diversity hypothesis': interpretable features/abstractions tend
  to arise only if training distribution is diverse enough (in the right 'way')
- they only do single frame input (atari typically does 4 frame input and
  recurrent is also common): does this effect generality of results?
- on coin run, value function just estimates time discounted prob of getting
  coin (coin is only reward)
- attribution to 'highlight' objects which pos/neg influence output
- ~train object recognizer on hidden layer to be able to attribute/understand
  which objects effect network output? (not sure I understand where the 'hidden
  layer' which recognizes objects comes from)~
- actually dimensionality reduction is just used to figure out which objects
  are which (seems like different objects 'happen' to correspond to 'strongest'
  dimensions)
- to regain intuition look and play with video under model analysis section
  (wow distill is the shit...)
- some of the object categories do seem a bit fuzzy, but most important (coin,
  saw) are coherent
- applies analysis to:
  - figure out what happens in failure (seems like this is mostly caused by
    incorrect MDP assumption: state given to model is only part of state and
    model doesn't have any memory. Really needs memory if state is only
    partially observed...)
  - incorrect GAE values indicate likely hallucination, able to find some
  - able to edit model to cause fatalities (some more easily than others)
- How much harder/easier is this with bigger recurrent model on harder game?
  (e.g. alphastar or openai5)
- How much harder/easier is this with non-visual input? (e.g. alphastar or
  similar)
- attribution:
  - used to see how input affects specific output
  - can also be applied to output of hidden layer as input or output
  - (uses integrated gradients, TODO: look into this)
  - in this case, consider hidden layer output as output into the rest of the
    model, do pos/neg attribution and then do pixel-wise non-negative matrix
    factorization (NMF) (TODO: look into this?)
- there are some questions for further research (might make for good project):
  - validity of diversity hypo
  - relationship between diversity, interp, generalization, model size
  - failure cases of this approach
  - quantify diversity
  - how can interpretability be done without diversity?
  - RL:
    - how to interpret on non-visual inputs (think about text model interp...)?
      Also abstract features in vision models.
    - can this approach (or similar) be used to actually improve reliability?
    - can training be changed to improve reliability?
- to review, just look back over (pretty pics!)

## Evaluating arguments one step at a time

- study of factored cognition using just humans (ought)
- dividing up args into short and structured chunks
- test of AI safety via debate (and similar)
- only one step shown for each checker
- can work in some cases, but brittle because isn't consensus on whether step
  is valid (maybe would work for proofs? trivially works for proofs in many
  formal languages for some chunk sizes)
- uses ebert reviews (is this really a good dataset? isn't optimized for
  argumentative qual)
- adversarial setup
- 'claim tree' (subclaims and quotes)
- also rebuttals and supporting quotes
- I don't really feel like I know what to conclude. Somehow results in no
  update at all? I this just because I wasn't sure what to expect, research is
  exactly what I would expect, or because research is useless?
- It looks like ought hasn't published that much, but this is representative of
  the type of stuff they have published.

## Switch transformers

- sparse transformer
- plausible considerably more computationally efficient for a give level of
  loss
- do the types of things it gets right differ substantially from higher param,
  but not sparse approach?
- just replaces dense FF with sparse switched layer (otherwise normal transformer)
- note that most of params in dense FF
- distributed approach splits weights by device
- param switching approach is from [https://arxiv.org/abs/1701.06538](https://arxiv.org/abs/1701.06538)
  - they use softmax with top-k with k > 1 to ensure gradients
  - also mention possible to due k = 1 with RL like approach (mention REINFORCE
    (aka vanilla policy gradient), but should be possible with other on-policy
    approaches)
- somehow they route to only a single expert (k = 1)? are they using RL like approach?
- expert per device
- capacity multiplier so that there is a fixed max tokens per expert (device) per batch
- if too many tokens for expert, layer values are yeeted and tokens are purely
  residual (so batch items can interfere with each other... lol just standard
  random deep learning noise,
  who needs correctness anyway...)
- possible to distill sparse nets for further improvements
- also load balancing loss
- use bfloat16
- can use expert dropout to reduce overfit
- ok, so we still multiply by route
  prob (despite pure greedy sampling) in order to ensure grad flow: [checkout this code](https://github.com/labmlai/annotated_deep_learning_paper_implementations/blob/master/labml_nn/transformers/switch/__init__.py)
  (but wow is this mad sketch. some weird scale dependence...)
- presumably all top-k MoE uses this approach and doesn't instead normalize to
  true selection prob (which is always 1 with k = 1)
- I find this so sketchy, but blessings of scale...
- legit everything is ill founded (just multiplier, token yeeting, params to
  the max, bfloat16)
- TODO: anything else I would want to extract from this?

## My take on Vanessa Kosoy's take on AGI safety

- [https://www.alignmentforum.org/posts/SzrmsbkqydpZyPuEh/my-take-on-vanessa-kosoy-s-take-on-agi-safety](https://www.alignmentforum.org/posts/SzrmsbkqydpZyPuEh/my-take-on-vanessa-kosoy-s-take-on-agi-safety)
- technical ai safety alignment also called 'single-single' alignment problem
  (instruction manual for making FAI)
- algorithms first vs desiderata first
- route:
  - formal desiderata (if ai satisfies these _desired_ conditions, then ai is safe)
    - probably requires something like utility function
  - prove algo satisfies desiderata (regret upper bound)
  - as needed, start with simplified desiderata and weaker (large computational
    requirements) alg, then make both more realistic
- to me, it seems exceptionally unlikely to prove anything of direct relevance.
  even the most directly relevant proofs in computational learning theory thus
  far aren't that relevant (and they tend to be impossibility results which
  aren't what we are looking for here)
- issues with traps:
  - current RL approaches require random exploration
  - so, to determine outcome is bad, outcome must be tested.
  - but in non-episodic contexts where permanence is an issue, it's possible to
    lock in permanently worse reward (trap)
  - proposed solution: delegative RL (allow agent to delegate when it isn't
    sure how to avoid trap, then the agent which is delegated to can avoid
    trap)
    - seems to require human to do all(!) exploration
    - also seems to require that human obeys some guarantees?
    - we don't require that human actions can't result in trap: some action
      could have low probability of being trap
  - solve humans committing actions which could be trap via quantilization
    - randomly sample from best actions human could have taken
    - 'less' optimization
    - I don't understand why this is supposed to help on average, maybe
      something, something goodhart?
- issues with realizability: infra-bayesianism
  - realizability better discussed elsewhere (e.g.
    https://www.alignmentforum.org/s/Rm6oQRJJmhGCcLvxh)
  - approach is to solve this with move from bayesianism -> infra-bayesianism
  - not clear why directly needed for this agenda, something with the
    desiderata? (mentions agent doesn't have to be following this model, but I
    don't understand why this is important for desiderata)
  - infra-bayesianism abstracts over hypothesises via convex sets of
    probability distributions (technical details complex...)
- non-cartesian daemons
  - where the hell (hah, get it) does this term come from? (google definition
    of cartesian daemon doesn't seem to correspond...)
  - usage of channels other than input/output (e.g., hacking sandbox)
  - violates assumption for provable guarantees
    - which maybe implies provable guarantees don't require intent alignment
      (otherwise, why would hacks be concern?)
  - maybe solvable with homomorphic encryption (but this is unusable slow!)

## Power dynamics as a blind spot or blurry spot in our collective world-modeling, especially around AI

- [https://www.lesswrong.com/posts/WjsyEBHgSstgfXTvm/power-dynamics-as-a-blind-spot-or-blurry-spot-in-our](https://www.lesswrong.com/posts/WjsyEBHgSstgfXTvm/power-dynamics-as-a-blind-spot-or-blurry-spot-in-our)
- claims that LessWrong doesn't consider power dynamics sufficiently (over
  focused on single-single)
- may be because MIRI originally started with simple single-single agenda
- may also be because original alignment community wanted to avoid talking
  about arms races to avoid having an arms race.
- I'm not sold that technical AI researchers should be all that concerned with
  things other than single-single: I think technical work for multi-multi has single-single
  as a prereq.

## Reframing impact sequence

- pretty pictures oooh
- impact can be decomposed into value impact and objective impact
- value impact
  - impact on specific values
  - exists independent of time and space
  - exists even if it doesn't effect you
- objective impact
  - impacts ability to achieve goals in future
  - space specific
  - often general over many agents with different goals
- impact iff changes ability to get what is wanted: attainable utility (AU)
- kind of obvious I think?
- impact is not primary about world state: is about attainable utility
- impact doesn't depend on ontology: thus impact isn't about world states
- impact happens to agent, not to world
- impact isn't related to change in identities or states (if doesn't effect AU)
- anticipated utility depends on expectations, so different agents may have
  different understandings of each other's anticipated utility (see
  robber/client
  [here](https://www.lesswrong.com/s/7CdoznhJaLEKHwvJW/p/coQCEe962sjbcCqB9))
- power as ability to achieve goals in general (behind veil of ignorance of
  reward function)
- power seeking depends on time prefs
- power seeking depends on reward distribution
- in general, reward functions best optimized by seeking power
- catastrophe: high impact for you, destroys your ability to get what you want
- objective catastrophe: high impact for many agents, destroys many agents
  abilities to get what they want
- consider going back through some of the later posts again (I kinda feel like
  I'm missing something (but not strongly))
- attainable utility preservation: do what you want, but don't seek power in
  general
  - should be a distance measure which pushes catastrophe far away (reduces the
    reward)
  - note: considering optimal policies 
  - only can (by definition) create weaker agents
- TODO: go through later posts again and refine thoughts

## Advanced artificial agents intervene in the provision of reward

- general result/scenario wrt learned reward (based on observations from the
  agent itself in some sense)
- applies for arbitrarily advanced agent (perfect planning etc)
- wireheading related?
- proof?
- agent may be uncertain between undesirable 'wireheadable' hypothesis and correct hypothesis
  - choices between the two depend on inductive biases
  - hypothesis 'intervenes in provision of reward'
- straight forward, but slightly more detailed argument that agents are likely
  to interfere with provisioning of reward
- TODO: take another look through this paper and other papers by Michael

## Causal inference using invariant predication

- collect models that are invariant to interventions and assume they are (more)
  causal
- allows for obtaining confidence intervals for which factors are causal
- maybe look into structural equation models
- use causal relationships for statistical estimation
- they are interested in Bayes net notion of causality: which predictors X are
  directly pointing to the target Y
- Ok, I am not going to look into this more right now, but it might be relevant
  in the future.

## Subagents and impact measures

- didn't read in that much detail
- rough idea is that conservative agency approaches have surprising issues
  (subagents used as example, but likely these issues show up in other cases)

## Late 2021 MIRI Conv

### Alignment difficulty

- Supposing we have (reasonably) aligned AI first, Eliezer says that act
  outside overton window needed to ensure safety (stop other ais from being
  made)
- Eliezer said the first (sketchy) alignment solution looks like mostly don't
  think about x and ok do think about y, but only safe thoughts (I feel like I
  don't understand this model, what about things like conservativeness. Also
  thought crime approach just seems really hard.)
- On systems which are more intelligent but much less agentic than humans
  - Eliezer basically says these systems are very unlikely to emerge like this
    given how current research (maybe deep learning more generally)
    works under his model of intelligence (is this definitions debate? On review, no.)
  - Eliezer says something like: to be powerful, system must be very 'close' to
    agentic system in some sort of modeling capability (car analogy), so hard
    to hold away from this (at least with current learning approaches).
- Eliezer says stack more layers doesn't get to true AGI (so no strong scaling
  hypothesis + longer timelines)
- On math/prover AI:
  - Eliezer says something like: No route to safety via this AI (or any other
    obvious and verifiable domain?). I (and Ngo) basically agree.
  - Eliezer says something like: doing math well requires something like goal
    directed consequentialist behavior
- Eliezer says something like: fundamental similarity
  between tasks which probably leads to consequentialism (with current
  techniques). This is dangerous.

  (as summarized by Ngo)
- Eliezer says something like: current ML techniques generalize Superhuman at X
  to take over the world.  Depends on X and architecture, but all
  profitable/useful for alignment X are dangerous.
- Eliezer says something like: science AI would be very close to modeling
  itself and have abilities to take over world (crux maybe: would it bother?)
- Ngo says something like: self-modeling unlikely to occur in science/math
  contexts
- So far my crux seems to be inner alignment/why would the model care about
  long term actions (in cases where model is process based instead of outcome
  based, clearly outcome is dangerous).
  - ah, deontology claims basically get at this
- is deontology natural way for mind to work?
  - does train for obedience result in deontologically obedient agent (or just
    diff utils)
  - Eliezer says something like: you will get optimization for correlates, not the thing itself
- Eliezer, summarized by Richard (paraphrased by me): To avoid catastrophe,
  whoever builds AGI first will have to a) align it sufficiently, b) decide not
  to scale it up to alignment failure  and c) do some pivotal act that prevents
  others from scaling it up to that level. But on our current trajectory, our
  alignment techniques will be very far from adequate to create an AI that
  safely performs any such pivotal act."
- deep connection between solving any useful problem and taking over the world
  (competent intelligence + goals + long term planning)
- Ngo says possible to make a agent way too weak to take over the world, but
  also useful for alignment research (or other such tasks). Because humans
  poorly optimized for task.
  - Eliezer responds that this probably insufficient for pivotal act.
- there's a bunch more stuff in here I don't have notes on
- particularly, see Nate's summaries

### AI capability gains

- Eliezer says he "expect[s] GDP not to depart from previous trendlines before
  the world ends"
- Eliezer says: "My read on the entire modern world is that GDP is primarily
  constrained by bureaucratic sclerosis rather than by where the technological
  frontiers lie" (I don't think I buy this... Ngo also doesn't buy)
  
BIG TODO on more of these posts (and maybe better notes)

## Imitative Generalisation (AKA 'Learning the Prior')

- [https://www.alignmentforum.org/posts/JKj5Krff5oKMb8TjT/imitative-generalisation-aka-learning-the-prior-1](https://www.alignmentforum.org/posts/JKj5Krff5oKMb8TjT/imitative-generalisation-aka-learning-the-prior-1)
- learn labeling 'instructions'
- learn prior over labeling instructions
- learn classifier on labels in original dataset
- use instructions to have humans label new dataset
- Profit?
- instructions need to capture everything AI could learn and be human readable
- like microscope AI, but with specific procedure
- does human (or amplified human) understandable thing exist?

## ELK

- [https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit](https://docs.google.com/document/d/1WwsnJQstPq91_Yh-Ch2XRL8H_EpsnjrC1dwZXR37PC8/edit)
- attaching a head to answer questions is insufficient because could use wrong
  model
- various regularization approaches fail in worst case, but might still help.


## TODO

- [circuits papers](https://distill.pub/2020/circuits/) (distill analysis of
  single neural net. I am somewhat familiar, but maybe go back over and take
  some notes on all sections)
- more stuff from ambassadors at EAG
- some new architectures/language models in general:
  - maybe read more about clip?
  - ? (haven't spent much time looking into what to read...)
  - now think this doesn't matter as much
- reread open phil rfps 
- invariant predication and causal inference
- michael cohen: [https://www.michael-k-cohen.com/](https://www.michael-k-cohen.com/)
- cartesian frames (maybe start with 'chu are you'), I now kinda think this is
  useless nerd bait, field is pretty dead
- [late 2021 MIRI convs](https://www.lesswrong.com/s/n945eovrA3oDueqtq)
- [readings/notes on research](https://forum.effectivealtruism.org/posts/qnF4rozLunaQz85zg/some-readings-and-notes-on-how-to-do-high-quality-efficient)
- [assistance via empowerment](https://arxiv.org/abs/2006.14796)
- maybe read some of [ai governance fundamentals material](https://forum.effectivealtruism.org/posts/68ANc8KhEn6sbQ3P9/ai-governance-fundamentals-curriculum-and-application)
- maybe read: [agency stuff](https://www.lesswrong.com/posts/qJBkcGW4GitfQ4BBy/agency-what-it-is-and-why-it-matters)
- [Against evolution as an analogy for how humans will create AGI](https://www.lesswrong.com/posts/pz7Mxyr7Ac43tWMaC/against-evolution-as-an-analogy-for-how-humans-will-create)
- [modeling transformative AI risk](https://www.lesswrong.com/s/aERZoriyHfCqvWkzg)
