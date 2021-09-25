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

## TODO
 - [circuits papers](https://distill.pub/2020/circuits/) (distill analysis of single neural net)
 - [understanding RL vision](https://distill.pub/2020/understanding-rl-vision/) (maybe some good projects along these lines...)


