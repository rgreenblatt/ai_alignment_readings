# TODO

_(TODO: we vs I?)_

The [Late 2021 MIRI conversions](https://www.lesswrong.com/s/n945eovrA3oDueqtq)
include discussion on why various approaches to alignment might fail.
One [shared frame](https://www.lesswrong.com/posts/GkxxfdCukyGuyKXQQ/shared-frames-are-capital-investments-in-coordination)
which wasn't immediately present in the discussion was a clean delineation of
possible approaches to alignment and what they require.
We claim that alignment techniques can be useful understood as *utility based*,
deontological, or capability restriction (or a mixture of these) and we'll be going through the challenges
associated with constructing _sufficiently useful_ and safe AI using these approaches. 
_(TODO: Not a fan of this wording, also fix utility based)_
Note that this post is intended to be readable without spending hours reading
those conversations. 
In fact, I'd hope that this post would be useful to read before reading these discussions
as it should help clarify and abstract. _(TODO: Not a fan of this wording)_

_(TODO: frame epistemic context for piece)_

Now what is this _sufficiently useful_ criteria we are using to judge AIs?
The alignment tax must be sufficiently small on the capability dimensions we care about. _(TODO: link to something on alignment tax)_
And what is sufficiently small?
Well, I don't think we currently have a good understanding of this, but 2
typical models are: _(TODO more epistemic humility)_

1. Small enough that alignment can be enforced via governance without to much
   incentive for defection. This framing is probably more relevant in slow
   takeoff.
2. Small enough that an actor could use a lead in AI capabilities to accomplish
   a [pivotal act](https://arbital.com/p/pivotal/) safely before unaligned AIs _(TODO: this article isn't very focused, better one?)_
   are constructed. Note that under this framing, the 'capability dimensions we care about'
   are the ones which can be used to cause a pivotal act. If the alignment penalty makes all pivotal acts
   impossible, then that technique is (approximately) worthless.
   This framing is more relevant in fast takeoff and the acceptable levels of alignment tax could
   depend on how far ahead the actor attempting to cause a pivotal act is. _(TODO: revise/cleanup language)_

For the remainder of this post, we'll abstract over this distinction in views,
referencing different perspectives as necessarily.

<!-- Now, first lets try to see what a safe AI which could be used for pivotal act looks like. -->
<!-- What's a pivotal act you say? Some sort of action which is able to ensure unsafe AI isn't produced by someone else. -->
<!-- For example, maybe your safe AI conquers the world yielding a golden age under the new Yudkow-tocracy. -->

<!-- (TODO: expand/clarify/consolidate this. how much background do we want? can link to pauls -->
<!-- views on alignment tax/governance, not sure what to link to on pivotal act -->
<!-- framing. Need to mention Yudkow-tocracy somewhere!) -->


<!-- The term _sufficiently useful_ probably has some unhelpful associations, -->
<!-- so we will taboo this and instead use the Japanese word for -->
<!-- useful: _Tsukaeru_. --> 
<!-- While we're at it, we'll pull this word into the hellscape which is the English -->
<!-- grammatical system to make writing more convenient (TOO much I think?) -->

<!-- Something something, criteria including discussion of pivotal act. -->


<!-- The first question is what objective we are aligning for... --> 
<!-- We'll abstract over ... -->

<!-- While I've seen all of these approaches to alignment discussed elsewhere, -->
<!-- I haven't seen a crisp delineation of these ideas and why they might fall -->
<!-- apart. Specifically, we'll be discussing deontological AIs and restricted AIs. -->
<!-- and how constructing _sufficiently useful_ and safe versions of these -->
<!-- AIs depends on currently unknown (and highly contested!) properties of -->
<!-- the space of intelligence itself and current machine learning (ML) --> 
<!-- (compare to oracle/genie/sovereign: these ideas fall apart in a similar way (TODO: maybe this parenthetical isn't useful?)). -->
<!-- (TODO: note how these are caricatures/continuous/could be combined) -->
<!-- As such, I make the case that we should be trying to learn more about these _spooky properties_. -->

<!-- My understanding is that EY thinks that these _spooky properties_ imply that -->
<!-- you can't get _sufficiently useful_, safe, and super intelligent AIs with these -->
<!-- approaches and current ML without some currently unknown *magic*. -->
<!-- This post will mostly abstract over views on _spooky properties_, timelines, and weak to moderate views -->
<!-- of societal coordination: when -->
<!-- differences become relevant, we'll mention them (make this better/describe what -->
<!-- we will actually do). --> 

<!-- This post is unfortunately unfocused, but there are two main aims: -->
<!-- - Abstracting/categorizing types of safe AI and why those types may fail. -->
<!-- - Making the case that we should be studying whether or not current approaches -->
<!--   can result in deontological agents and how that scales with capabilities. -->


But abstracting over everything results in a mess, so we'll make the following
assumptions:
1. Unrestricted and superintelligent AGIs which basically act like
   long-term expected utility maximizers (aka Consequentialists) would kill us
   all and destroy most of the value of the future if created with approaches
   reasonably similar to current ML. This is due to Goodhart's law and an
   inability to perfectly align utility functions (if we could even state one).
2. Societal and government competence and coordination aren't very high.

I make the case for why these are good assumptions in the appendix to avoid
clutter (because I'd guess most readers at least roughly already buy them). If
you strongly disagree with either of these assumptions, well, maybe pick a
different post to read (after making sure your aware of the arguments in the
appendix).

## Utility based approaches

Given that we assume that long-term expected utility maximizers would kill us
all, what utility based approaches are left? Well, expected utility maximizers
which don't care about the
long run of course! These are typically described as myopic agents.
Unfortunately, we currently [don't know how to construct myopic
agents](https://www.lesswrong.com/posts/LCLBnmwdxkkz5fNvH/open-problems-with-myopia),
simply training agents with myopic reward is insufficient.
The issues here broadly come to inner alignment. 
We don't have solid approaches for inspecting the cognition of deep agents.
Or a decent understanding of
what agent cognition will result from a specific training process.
And it's unclear if techniques will generalize to higher intelligence regimes.
These issues are a theme for this entire post. My current
view is that this is the difficult crux of alignment and we'll
present only one (dangerous) way to proceed without resolving these issues.
<!-- The TLDR on this 'difficult crux of alignment' is: can we inspect the cognition -->
<!-- of agents meaningfully or predict the cognition which will result from --> 
_(TODO: maybe this should be moved earlier?)_
_TODO: revise this as we keep writing_


Even though long-term expected utility maximizers would kill us all, there's
still value in the ability to produce agents with utility functions reasonably
close to the desired one. This would greatly increase the applicability of
deontological and restriction based approaches as discussed below.

## Deontological approaches


_(TODO: maybe define/link deontology)_

### Tool AIs are purely deontological AIs

We've covered expected utility maximization, so let's now consider AIs which
don't care about optimizing their environments at all. Specifically we'll
first consider AIs which reduced agency: tool AIs. _(TODO:
Contested if this even is a real thing, maybe mention here, possibly in footnote)_ You may have
noticed this appears in the deontological approaches section.  That's because I
claim that tool AIs (as typically described) are just _purely deontological_
AIs. 
[Agency is mostly just a set of capabilities coupled with
(long-term) consequentialism](https://www.lesswrong.com/s/mzgtmmTKKn5MuCzFJ/p/bz5GdmCWj8o48726N).
If wish to remove agency while keeping capabilities, we must remove consequentialism
yielding a deontological AI. It may also be possible to reduce agency by removing some
capabilities (such as self-modeling), this will be discussed in the section on
restriction based approaches.
Tool AIs are an extreme version of a deontological approach as they are _purely deontological_,
but they serve as a good exhibit of the weaknesses and safety advantages of deontological AIs
as well as the challenges in constructing them.

_(TODO: maybe footnote here explaining that purely deontological AIs basically
always have the features which are current associated with the words 'tool AIs'.
However, there is exception of very strange deontological principles like wanting
to imitate a consequentialist etc... Maybe also description of
tool vs process based task vs purely deontological and how uses of these terms has differed?
Maybe put this footnote below where we discuss purely deontological AIs
which basically act like agents?
In general, I'm worried about these words being confused given
how I first expand the notion of tools and then contract the notion of actually achievable purely deontological
AIs)


### Purely Deontological AI, what is it good for

_(TODO, ok maybe use actual title that references that this section is about safety properties...)_

Given that different people use the term 'tool AI' in somewhat different ways,
I will stick with the verbose _purely deontological_ AI from here on.


Note that _purely deontological_ AIs can be capable of modeling consequences, but they don't
_care_ about the consequences of their actions. _footnote, this is a likely  difference from how Eliezer was using the tool AI/non-agentic AI
as he stated , so planners actually can
be tool AI, but only they **don't care about the consequences of their plans and instead care about something else**_
These means that _purely deontological_ AIs can appear very agentic. For instance, consider
a _purely deontological_ AI which just cares about imitating the actions of 
a human. For a more absurd
example, consider an AI which only cares about imitating what its actions would
be if it here a expected value maximizer. For a competent imitator, this
the *same* as being an expected value maximizer.
So wait! Why have we bothered with defining this class of AIs if it practically
includes expected value maximizers anyway!?
Well, this come down to why the intentions of AIs matter at all.
Intentions determine behavior when out of distribution for intelligent and capable agents.
For example, consider 
[some empirical observations of objective robustness failures](https://www.lesswrong.com/posts/iJDmL7HJtN5CYKReM/empirical-observations-of-objective-robustness-failures)
in which agents 'care' about a correlated feature and then purse that feature when out of distribution instead of the reward
from the original environment.
There are also more arcane considerations like deceptive alignment which can
leverage slight distributional differences into unsafety failures _footnote, even if test inputs are within the training distribution (somehow),
unless training is arbitrarily long there can still be safety concerns due to probabilistic treacherous turns_

So there can be purely deontological AIs which act like consequentialist agents
in their training environments, but we generally expect them to act less like consequentialist
agents on out of distribution inputs. In general, I would be Very Surprised
if a highly capable, purely deontological AI killed us all in a bid for power without having been
trained explicitly to do so. It is isn't agency which scares us: it's generalizing agency.

In summary, purely deontological AIs are not existentially dangerous _by
default_. They're in the same danger category as a nuclear
bomb: they might kill a bunch of people, but you'll have to launch them first.

<!-- Maybe more here? -->
<!-- Maybe discuss optimization like below? -->


<!-- One behavioral property that tool AIs have is that they don't (intentionally) optimize. -->
<!-- Well, what do we mean by this precisely? Does a hammer optimize the position -->
<!-- of a nail? -->
<!-- Using the definition of optimization purposed [here](https://www.lesswrong.com/posts/znfkdCoHMANwqc2WE/the-ground-of-optimization-1), -->
<!-- we'll say that a tool AI can be _used_ for optimization, but doesn't -->
<!-- perform the optimization itself. The key distinction is that -->
<!-- the target which a tool AI and wielder optimize toward often changes as you -->
<!-- perturb the goals of the yielder. _(TODO: something about how the tool AI itself isn't the thing which corrects for perturbations, otherwise, it's a consequentialist)_ --> 
<!-- This is a general property of friendly AI, --> 
<!-- <!-1- though it's worth noting that we -1-> -->
<!-- <!-1- would really like the direction of change to be toward the goals of the -1-> -->
<!-- <!-1- wielder, -1-> --> 
<!-- the distinction... -->
<!-- <!-1- TODO There should be something more here... -1-> -->

### Constructing sufficiently useful purely deontological AIs

The next question we need to ask is how a _sufficiently useful_ purely
deontological AI can be constructed.

How could we train a purely deontological AI to do useful things? We could
train to imitate or predict instead of optimizing for outcomes. Perhaps apply
some iterative amplification or similar and boom, you've got an tool AI which
do useful things.

Did you catch it?

The error in the above reasoning? Take a second and think through what's
wrong before peeking.

:::spoiler
 
Just because an AI is trained to imitate or predict doesn't mean it's
guaranteed to be a purely deontological AI!

For instance, consider an AI trained to imitate a another AI which is
a competent expected utility maximizer. It seems quite plausible
that this imitator would itself just become an expected
utility maximizer! 

More generally, inner alignment is not guaranteed by all training procedures.
<!-- If this AI was really good at this task, it seems --> 
<!-- would behave exactly like a human. -->
<!-- At this point, the AI would be optimizing its environment because humans -->
<!-- optimize their environments. -->

<!-- In the RL context, a [Q -->
<!-- function](https://spinningup.openai.com/en/latest/spinningup/rl_intro2.html) is -->
<!-- _just_ a prediction function! _footnote, note that it isn't trained purely as prediction function, but the optimal Q function is -->
<!-- a predictor._ -->  
<!-- But add argmax action selection and you have a full agent. -->

:::

To be clear, I don't think this is a common misconception among people working
on or thinking about alignment. However, it does seem like a potential trap, so
I thought I would try to push readers away from the trap strongly.

So, there isn't an obvious way to train a purely deontological AI. In fact, we
don't even know how to check how if an AI cares about consequences
or deontological rules.
We're back to difficult crux of alignment discussed earlier.

That said, there are obvious ways to train deep neural networks which ensure that
they will be purely deontological. For instance, consider training
a (randomly initialized) model to output the value 1. 
Clearly such an model isn't going to be a consequentialist or intelligent
(unless you think the inductive biases of SGD are *actually* Magic).
But, if the task in question might involve modeling consequences,
the question of how to use current machine learning approaches 
to produce intelligent, non-consequentialist agents is considerably tricker.

In the superintelligent, highly capable regime, what sorts of training and
objectives might produce purely deontological agents (as opposed to agents
which are at least partially consequentialists)? Well, we're clearly deep into
speculation land, because we don't even know how to produce a superintelligent,
highly capable AI (I wouldn't tell you if I knew _TODO: change to footnote?_).
However, I would be Very Surprised if training agents based on the consequences
of their actions (outcomes) in even modestly complex environments with
something resembling modern machine learning (e.g. reinforcement learning)
resulted in purely deontological AIs outside of edge cases or the application
of some not currently known technique.
I'd also make a similar claim about AIs
trained to imitate another expected utility maximizer AI. Note that constructing plans
also falls into the category of outcome based training (assuming you care about
whether or not those plans work!). Also be careful not to over generalize my
statement: I'm just saying that you wouldn't get _purely_ deontological agents,
not that you couldn't get _partially_ deontological agents which we will
discuss later. So, this leaves the tasks which are classically associated with
tool AIs such as prediction. We'll refer to these tasks as _process based_ as opposed
to _outcome based_. _(TODO: better name than process based, maybe a standard name)_
So would process based tasks actually result in purely deontological AIs? I will hold
off on speculating here, though I think the answer to this
question would be useful.
My understanding is that in [this
conversation](https://www.lesswrong.com/s/n945eovrA3oDueqtq/p/7im8at9PmhbT4JHsW)
EY says that he thinks that current machine learning
techniques couldn't even produce an intelligent and purely deontological model.
There's also some speculation in 
[this post on safety in predictive learning](https://www.lesswrong.com/posts/ey7jACdF4j6GrQLrG/thoughts-on-safety-in-predictive-learning).

Now let's suppose that process based tasks do in fact result in purely deontological
agents and consider if such agents can be _sufficiently useful_.

I'm not currently aware of any pivotal act which can be achieved using a
process based task AI. A process based task AI could possibly help speed up
alignment research, but probably not astronomically, so that isn't sufficient
for a pivotal act.

_(TODO: add predication widget thing here for existence of such an act.)_


If purely deontological AI via process based tasks is the main approach to alignment enforced by governance, the
benefits of defection seem large as [tools want to be agents](https://www.gwern.net/Tool-AI).

So overall, my belief is that trying to solve alignment for current ML via
using purely deontological AIs is very unlikely to succeed.

### Partially Deontological AI, what is it good for

Given the weakness of purely deontological AIs, perhaps we can tolerate some
level of consequentialism, but instill some deontological properties.
Such as...

Now just explain why hard...


A deontologically corrigible or obedient agent might have
incoherent preferences, but there's a problem we run into even
before that: how the hell do we instill deontological preferences?

For any environment which rewards deontological methods, there
exists an agent which simply models that reward as part of its
utility functions and achieves full marks.
Without knowing more about the learning process or inspecting the agent
we can't hope to do better.

So maybe if you setup your Very Clever corrigibility encouraged environment
and train to convergence you get a super intelligent, modestly aligned,
and corrigible agent. But maybe not. And we have no good physics
or even chemistry style models for understanding the eventual intentions
of super intelligent AI produced via such a process.




## Restrained AIs

Deontology is hard and consequentialism kills us all. Is there another way?

Now we're ready to motivate the approaches to safety discussed earlier. We've
said that acting like an expected utility maximizer is a big no-no, so what if
we considered AIs which don't (intentionally) optimize their environments at
all? Specifically we'll first consider AIs which possess no agency: tool AIs. 


<!-- Given the likely incompetence of such an AI we'll try a different approach -->
<!-- next: constructing an intelligent utility maximizer and restraining its -->
<!-- capabilities. -->


For an example of a restrained AI, consider an AI which operates
as a long term goal achieving consequentialist in some sort of
constrained environment (e.g. theorem proving) without even
knowing about the real world. Or consider AIs (hopefully) made safer
by somehow removing their ability to model humans or another part of the world.
Both of these AI have had their capabilities handicapped to reduce danger.
Additionally, the classic 'boxed' AI is an example of this approach and the
typically proposed issues generalize to restrained AIs more generally.


<!-- The earlier examples are also 'boxed' in some sense, they are boxed -->
<!-- by knowledge knowledge instead of physical isolation. -->

Such an AI could theoretically not be intent aligned and be a highly
capable consequentialist agent while also being safe.
Or could they?
The classic boxed AI which is aware of the external world will manipulate
and fight for unsafe freedom.
Similarly, the knowledge boxed AI will fight for missing knowledge. Perhaps you
think you can get around this by simply making the AI not even able to consider
the knowledge you wish to keep away. Alas, this seems difficult to do
without devastating the capabilities of the AI. An AI with
no knowledge of the world can't contribute to pivotal events (something, something
alignment tax TODO).

(TODO: give things needed for restrained AIs to work after going through
misconceptions)

Ok, so restraints and tools both seem likely to fail. What if
instead of redacting capabilities or intelligence, we simply made
them act less like expected utility maximizers?

## Deontological agents

A deontologically corrigible or obedient agent might have
incoherent preferences, but there's a problem we run into even
before that: how the hell do we instill deontological preferences?

For any environment which rewards deontological methods, there
exists an agent which simply models that reward as part of its
utility functions and achieves full marks.
Without knowing more about the learning process or inspecting the agent
we can't hope to do better.

So maybe if you setup your Very Clever corrigibility encouraged environment
and train to convergence you get a super intelligent, modestly aligned,
and corrigible agent. But maybe not. And we have no good physics
or even chemistry style models for understanding the eventual intentions
of super intelligent AI produced via such a process.
