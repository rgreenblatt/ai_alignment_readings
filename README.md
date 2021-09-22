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
 - POMDPs (and other agent models?)
 - Scaling laws
 - Various current research avenues
   - interpretability
   - deceptiveness (particularly language models)
   - alignment strategies
     - iterated amplification [original paper](https://arxiv.org/abs/1810.08575) and 
       [summary](https://ai-alignment.com/iterated-distillation-and-amplification-157debfd1616)

       See Iterated Amplification subsection in the papers section for notes/questions
     - [11 proposals](https://www.alignmentforum.org/posts/fRsjBseRuvRhMPPE5/an-overview-of-11-proposals-for-building-safe-advanced-ai)
     - [multi agent safety](https://www.alignmentforum.org/posts/BXMCgpktdiawT3K5v/multi-agent-safety)
     - [reward modeling (paper on outer alignment techniques)](https://arxiv.org/pdf/1811.07871)
     - week [4 (how to learn from humans?)](https://www.eacambridge.org/agi-week-4) 
     + [5 (Decomposing tasks for outer alignment)](https://www.eacambridge.org/agi-week-5) of EA Cambridge course (TODO: pick subset)
   - general theory (MIRI stuff, etc.)
 - timelines: [decent guide](https://www.cold-takes.com/where-ai-forecasting-stands-today/)
 - [orthogonality thesis and instrumental convergence](https://www.nickbostrom.com/superintelligentwill.pdf)
 - concerns/issues with current approaches (deep learning, etc.)
   - [specification gaming/reward hacking](https://deepmindsafetyresearch.medium.com/specification-gaming-the-flip-side-of-ai-ingenuity-c85bdb0deeb4)
   - [risks from learned optimization](https://www.lesswrong.com/s/r9tYkB2a8Fp4DN8yB)
     - mesa optimization
     - [gradient hacking](https://www.lesswrong.com/posts/uXH4r6MmKPedk8rMA/gradient-hacking)
 - [tool vs agent AIs](https://www.gwern.net/Tool-AI) (and why we are likely to end up with agent AIs
 - [week 6 (other paradigms for safety work)](https://www.eacambridge.org/agi-week-6) of EA Cambridge course (TODO: subset)
 - AI governance
   - [week 7](https://www.eacambridge.org/agi-week-7) of EA Cambridge course (TODO: subset)
   - TODO more stuff here
 - 

## Career advice
 - [via Rohin Shah](https://rohinshah.com/faq-career-advice-for-ai-alignment-researchers/)
 - [80000 hours guide for ML engineering](https://80000hours.org/articles/ml-engineering-career-transition-guide/) and
    [associated podcast](https://80000hours.org/podcast/episodes/olsson-and-ziegler-ml-engineering-and-safety/)
 - [reproducing deep rl papers](http://amid.fish/reproducing-deep-rl)

## Papers

### Iterated amplification
 - [original paper](https://arxiv.org/abs/1810.08575)
 - Claim is this allows for creating an agent which "approximates the behavior
   of an exponentially large team of copies of [the human expert]". 

   Is this sufficient for having high capabilities? Are there behaviors which
   can't be reached simply via this large team?  In other words, are there
   behaviors the human won't recognize as good which we want?

 - Note that the paper uses this technique on a variety of toy problems and
   compares to pure supervised learning (which is possible for those problems).

### Learning to summarize from human feedback
 - [https://arxiv.org/abs/2009.01325](https://arxiv.org/abs/2009.01325)
 - Human feedback with reinforcement learning beats predication/imitation. Uses
   reward model (to reduce quantity of feedback needed)
 - Allows for producing superhuman summaries (predication/imitation are worse
   than human and can only get as good, not better)
 - trained via reddit tldr
 - fine tuned gpt-3 style model (fewer params, ~2 Billion and ~7 Billion param models tested)
 - reward model generalizes better than the summary model itself

