# ai_alignment_readings

## Meta sources:
 - [https://www.eacambridge.org/agi-safety-fundamentals](https://www.eacambridge.org/agi-safety-fundamentals)
 - [key papers in deep rl](https://spinningup.openai.com/en/latest/spinningup/keypapers.html)

## General background I found non obvious and useful

Note, assumes you already buy that AI alignment is serious issue etc. Weakly assumes background on ideas
such as in Superintelligence by Bostrom.

 - [bitter lesson](http://www.incompleteideas.net/IncIdeas/BitterLesson.html):
   discusses how computation has been limiting factor in practice
 - [prosaic ai](https://ai-alignment.com/prosaic-ai-control-b959644d79c2): idea
   that scaling up current DL (particularly language models) could result in AGI
 - [80000 hours with Paul Christiano](https://80000hours.org/podcast/episodes/paul-christiano-ai-alignment-solutions/): 
   a bit old. Reflects Paul's thoughts on likely time lines and scenarios (not 'brain in a box', slower takeoff). 
 - maybe various models of intelligence/superintelligence (I currently don't think this is very important)
   - e.g.: [https://www.alignmentforum.org/posts/x3fNwSe5aWZb5yXEG/reframing-superintelligence-comprehensive-ai-services-as](https://www.alignmentforum.org/posts/x3fNwSe5aWZb5yXEG/reframing-superintelligence-comprehensive-ai-services-as)
 - [most important century series](https://www.cold-takes.com/roadmap-for-the-most-important-century-series/#our-wildly-important-era) 
 consider also the less wrong version: [most important century sequence](https://www.lesswrong.com/s/yYxggfHYRrqnJXuRx) 
   (most of this is standard case for AI alignment + some ideas from [age of em](https://en.wikipedia.org/wiki/The_Age_of_Em))

## Subscriptions

All of this is available via RSS

 - [alignment forum](https://www.alignmentforum.org/)
 - [less wrong](https://www.lesswrong.com/) This is less directly relevant. But there is a decent amount here which isn't also cross posted
   to alignment forum (alignment forum and less wrong have a very similar cohort).
 - [alignment newsletter](https://rohinshah.com/alignment-newsletter/)

## Concepts you should know about
 - timelines: [decent guide](https://www.cold-takes.com/where-ai-forecasting-stands-today/)
 - [orthogonality thesis and instrumental convergence](https://www.nickbostrom.com/superintelligentwill.pdf)
 - concerns/issues with current approaches (deep learning, etc.)
   - [specification gaming/reward hacking](https://deepmindsafetyresearch.medium.com/specification-gaming-the-flip-side-of-ai-ingenuity-c85bdb0deeb4)
   - [risks from learned optimization](https://www.lesswrong.com/s/r9tYkB2a8Fp4DN8yB)
     - mesa optimization
     - [gradient hacking](https://www.lesswrong.com/posts/uXH4r6MmKPedk8rMA/gradient-hacking)
 - [alignment landscape](https://ai-alignment.com/ai-alignment-landscape-d3773c37ae38) (diagram on components of making AI go well)
   - corrigibility in general is hard
 - Various current research avenues
   - deceptiveness (particularly language models)
   - alignment strategies (prosaic)
     - iterated amplification [original paper](https://arxiv.org/abs/1810.08575) and 
       [summary](https://ai-alignment.com/iterated-distillation-and-amplification-157debfd1616)

       See Iterated Amplification subsection in papers.md for notes/questions
     - reward modeling more generally
     - [deep rl from human preferences](https://openai.com/blog/deep-reinforcement-learning-from-human-preferences/). Otherwise known as backflip paper.
     - [11 proposals](https://www.alignmentforum.org/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai)
     - tool vs agent concerns
      - [microscope ai](https://www.alignmentforum.org/posts/X2i9dQQK3gETCyqh2/chris-olah-s-views-on-agi-safety#Building_microscopes_not_agents) IMO this 
        seems like a very uncompetive and narrow strategy (in terms of capabilities) (Chris Olah likely agrees)
      - [Why tool AIs want to be Agent AIs](https://www.gwern.net/Tool-AI)
     - [multi agent safety](https://www.alignmentforum.org/posts/BXMCgpktdiawT3K5v/multi-agent-safety)
     - [reward modeling (paper on outer alignment techniques)](https://arxiv.org/pdf/1811.07871)
     - [assistance games](https://www.alignmentforum.org/posts/qPoaA5ZSedivA4xJa/our-take-on-chai-s-research-agenda-in-under-1500-words)
       when optimization task is human desire fufillment and multiple feedback rounds exist
         - requires optimization algorithm to take into account uncertainty: objective not known (related is corrigibility)
         - Example: [cooperative inverse reinforcement learning (CIRL)](https://arxiv.org/abs/1606.03137)
         - relaxes fully specificed objective (we don't know how to specify)
         - see also [benefits of assistance games](https://drive.google.com/file/d/1Xp9p6RLNjZrgsdEbGIJK61FnV_drDTQf/view)
     - [cooperative inverse reinforcement learning (CIRL)](https://arxiv.org/abs/1606.03137)
         - model/approach in which ai learns human preferences and human investiages their own preferences in cooperative game
         - reduces to POMDP
     - [ambitious vs narrow value learning](https://ai-alignment.com/ambitious-vs-narrow-value-learning-99bd0c59847e)
       Related, consider idea that we should avoid AIs which need to model human preferences (for example 
       [microscope ai](https://www.alignmentforum.org/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai#5__Microscope_AI)
       or [stem ai](https://www.alignmentforum.org/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai#6__STEM_AI))
     - [AI safety via debate](https://openai.com/blog/debate/)
       - agents debate with human judge
       - theory is that this may converge to correct/aligned actions. this requires that debate favors correct arguments in some sense.
   - interpretability and transparency
     - [Chris Olah's views on AGI safety](https://www.alignmentforum.org/posts/X2i9dQQK3gETCyqh2/chris-olah-s-views-on-agi-safety)
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
   - general theory (MIRI stuff, etc.)
     - [embedded agents](https://intelligence.org/2018/10/29/embedded-agents/)
       - This is very worth reading. I don't know why I didn't read this
         earlier, this nicely clarifies why we should care about decision
         theory and some other things
       - How do we model/understand agents which are part of the environment (like us)
       - Particularly in the case where accurate predication, simulation, and similar are possible
       - Leads to subproblems:
         - decision theory 
           - many open mathematical problems
           - generally focused on [updateless decision theory](https://www.lesswrong.com/posts/de3xjFaACCAk6imzv/towards-a-new-decision-theory) 
         - embedded world model: how to model the world as an entity which is smaller than (inside of) the world
           - breaks Bayesian assumptions
           - logical uncertainty, we may know all the details of something, but
             be unable to compute the results (not clear to me why this is a
             theoretical problem in practice, haven't read much about it)
         - robust delegation: making well aligned successor without being able to predict actions of successor
           - applies to aligning initial agent to human preference and further iterations
           - corrigibility maybe important
         - subsystem alignment: parts of agent just obey physical laws, so they must also be aligned

 - [tool vs agent AIs](https://www.gwern.net/Tool-AI) (and why we are likely to end up with agent AIs
 - [week 6 (other paradigms for safety work)](https://www.eacambridge.org/agi-week-6) of EA Cambridge course (TODO: subset)
 - Scaling laws
 - POMDPs (and other agent models?)
 - AI governance
   - [week 7](https://www.eacambridge.org/agi-week-7) of EA Cambridge course (TODO: subset)
   - TODO more stuff here
 - 

## Career advice
 - [via Rohin Shah](https://rohinshah.com/faq-career-advice-for-ai-alignment-researchers/)
 - [80000 hours guide for ML engineering](https://80000hours.org/articles/ml-engineering-career-transition-guide/) and
    [associated podcast](https://80000hours.org/podcast/episodes/olsson-and-ziegler-ml-engineering-and-safety/)
 - [reproducing deep rl papers](http://amid.fish/reproducing-deep-rl)

## Learning RL
 - [spinning up](https://spinningup.openai.com/en/latest/user/introduction.html)
