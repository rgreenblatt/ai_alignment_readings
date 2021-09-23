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

## TODO
 - [circuits papers](https://distill.pub/2020/circuits/) (distill analysis of single neural net)
 - [understanding RL vision](https://distill.pub/2020/understanding-rl-vision/) (maybe some good projects along these lines...)


