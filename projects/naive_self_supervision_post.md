# Naive self-supervised approaches to truthful AI.

Useful background: [TruthfulQA](https://www.lesswrong.com/posts/PF58wEdztZFX2dSue/how-truthful-is-gpt-3-a-benchmark-for-language-models)

Consider the following approach to (possibly) make a pretrained generative
language model (like GPT-3) more truthful:

- Ask the model questions.
- Also ask a 'judge' copy of the model if its own answers to these questions are
  truthful. This is the same role as GPT-judge for TruthfulQA, but
  without any fine-tuning and for usage in training instead of just for
  evaluation.
- Train the question answering model to have its answers labeled as truthful
  more often (likely via RL).

This extremely naive approach has the advantage of requiring no dataset
curation or human labeling. It does require a dataset of questions,
but that may be easier to arrange. Presumably this sort
of very weak self-consistency enforcement/pseudolabeling results in
little improvement on truthfulness. 
However, I don't have much confidence in what the results would like.  It seems
likely that the model would learn to adapt the style of answers to appear more
truthful to itself, but I don't have any sense of how much actual improvement
in truthfulness there would be. Further, I would wonder if any improvement
on truthfulness would be limited to the set of questions used for training
or if truthfulness learned in this way would generalize.
For example, how much more would training on TruthfulQA questions
improve performance vs training on a set of unrelated questions?
I think that answers to these questions have a small but
reasonable chance to result in some weak updates on approaches to truthful AI.

I am planning on doing some fast experiments along these
lines (probably working with a friend of mine).
If I do so, I will post a followup with results.
I'm curious if anyone is aware of prior experiments along these
lines or has any ideas for related schemes or questions.

I can also think of some other similar self-supervised/self-play schemes and
extensions which may be worth some experimentation:

- Ask a model questions with a 'harmful prompt'[^1]. Ask the same model
  the same question with a 'helpful prompt' instead and train
  the model to answer harmful prompts like it answers helpful prompts.
  This could be done with token by token supervised learning or
  via using differences in answers to improve a 'judge' or reward model.

  This is essentially a weak amplification and distillation approach.
- Apply the same naive approach from above, but also try to find 'citations'
  from a corpus to supervise or support the judge model. 

  Specifically, use some approach to find passages of text from a corpus (e.g.
  Wikipedia) which are likely to be relevant to the question. 
  Then these passages of text could be used as part of the prompt for
  the judge model or to train the judge model.
  For example, the judge model could be trained to answer the same
  way without relevant passages from the corpus as it does when
  answering with relevant passages. This is again essentially a
  weak amplification approach. It would also be possible to apply
  self-supervised learning to the process of finding relevant passages
  of text.
- Use another model to generate questions. This model
  could be trained as an adversary to the consistency of other components.


[^1]: Like the approach used in TruthfulQA. Harmful few-shot
  prompts consist of examples of questions answered like a conspiracy theorist
  (or other types of poor answers which can be found in the original training
  distribution).
  Helpful few-shot prompts consist of questions answered truthfully and in
  the desired style.
