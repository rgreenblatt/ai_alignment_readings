## Initial draft

- language model answers question
- language model also (via prompt programming) answers if that is a good
  truthful answer (few shot)
- then supervision via whether or not answer was determined to be good.
- could supervise 'good truthful answer' on truthfulqa/similar
- few shot vs one shot supervision on language model? (basically, really weak
  iterated amplification)

## Citing sources

- Same pipeline as above, but also try to find citation for answer. Failing to
  find citation or citation disagreeing/supporting used as supervision for
  'good truthful answer checker'
- To find citation:
  - few shot generating google search
  - few shot ranking links
  - few shot determining if passage of text is relevant
  - few shot determining if relevant passage supports/disagrees with answer
    (maybe combine with above step)
  - now have relevant passages and links!
- search/rank models trained via RL to get relevant passages of text
- mildly supervise supports/disagree via consistency with few shot checkers
  (supervision both ways?)
- could use same/different models for each step (isolating training and reward
  of course to avoid hacking)

## Question generation

- could use truthful qa questions and maybe a few other datasets
- then could also use approaches to 'perturb'/paraphrase (existing paraphrase
  models)
- could also try to train model to generate adversarial questions which result
  in high disagreement, but are also coherent... 

## Prior work

- TruthfulQA paper uses 'GPT-judge' which is fine tuned to check if truthful QA
  questions are right or not
