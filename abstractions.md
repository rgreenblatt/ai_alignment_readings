# TODO

The [Late 2021 MIRI conversions](https://www.lesswrong.com/s/n945eovrA3oDueqtq)
include discussion on why various approaches to alignment might fail
if my understanding of the views of Eliezer Yudkowsky (EY) on intelligence and
current AI research are broadly correct. (Please note that this post... something
something kowtow to epistemic humility).
Note that this post is intended to be readable without spending hours reading
those conversations. 

In fact, I'd hope that this post would help clarify and
distill some of that discussion (something like this, maybe also read before reading discussion?)

While I've seen all of these approaches to alignment discussed elsewhere,
I haven't seen a crisp delineation of these ideas and why they might fall
apart. Specifically, we'll be discussing tool AIs, restricted AIs, and deontological AIs
and how constructing _sufficiently useful_ and safe versions of these
AIs depends on currently unknown (and highly contested!) properties of
the space of intelligence itself and current machine learning (ML) 
(compare to oracle/genie/sovereign: these ideas fall apart in a similar way (TODO: maybe this parenthetical isn't useful?)).
(TODO: note how these are caricatures/continuous/could be combined)
As such, I make the case that we should be trying to learn more about these _spooky properties_.

My understanding is that EY thinks that these _spooky properties_ imply that
you can't get _sufficiently useful_, safe, and super intelligent AIs with these
approaches and current ML without some currently unknown *magic*.
This post will mostly abstract over views on _spooky properties_, timelines, and weak to moderate views
of societal coordination: when
differences become relevant, we'll mention them (make this better/describe what
we will actually do). 

<!-- This post is unfortunately unfocused, but there are two main aims: -->
<!-- - Abstracting/categorizing types of safe AI and why those types may fail. -->
<!-- - Making the case that we should be studying whether or not current approaches -->
<!--   can result in deontological agents and how that scales with capabilities. -->


But abstracting over everything results in a mess, so we'll make the following
assumptions:
1. Highly capable and strongly superintelligent AIs which basically act like
   expected utility maximizers (aka Consequentialists) would kill us all if
   created with approaches reasonably similar to current ML.
2. Societal and government competence and coordination aren't very high.

I am not certain that both of these assumptions are true and I can imagine
scenarios in which they wouldn't hold. However, I would be very surprised if
either claim was totally false and I think that they are useful assumptions for
reducing the safe AI search space. I make the case for why these are good
assumptions in the appendix to avoid clutter (because I'd guess most readers
mostly already buy them). If you strongly disagree with either of these
assumptions, well, maybe pick a different post to read.

Now what is this _sufficiently useful_ criteria we are using to judge AIs?
Well, depending on views, either sufficiently small alignment tax so society
can collectively enforce via governance or sufficiently small capabilities
penalty such that an actor could use this AI to accomplish a 'pivotal act'.
The term _sufficiently useful_ probably has some unhelpful associations,
so we will taboo this and instead use the Japanese word for
useful: _Tsukaeru_. 
<!-- While we're at it, we'll pull this word into the hellscape which is the English -->
<!-- grammatical system to make writing more convenient (TOO much I think?) -->

<!-- Something something, criteria including discussion of pivotal act. -->

Now, first lets try to see what a safe AI which could be used for pivotal act looks like.
What's a pivotal act you say? Some sort of action which is able to ensure unsafe AI isn't produced by someone else.
For example, maybe your safe AI conquers the world yielding a golden age under the new Yudkow-tocracy.

(TODO: expand/clarify/consolidate this. how much background do we want? can link to pauls
views on alignment tax/governance, not sure what to link to on pivotal act
framing. Need to mention Yudkow-tocracy somewhere!)

Now we're ready to motivate the approaches to safety discussed earlier. We've
said that acting like an expected utility maximizer is a big no-no, so what if
we considered AIs which don't (intentionally) optimize their environments at
all? Specifically we'll first consider AIs which possess no agency: tool AIs. 

## Tool AIs

One behavioral property that tool AIs have is that they don't optimize.
Well, what do we mean by this precisely? Does a hammer optimize the position
of a nail?
Using the definition of optimization purposed [here](https://www.lesswrong.com/posts/znfkdCoHMANwqc2WE/the-ground-of-optimization-1),
we'll say that a tool AI can be _used_ for optimization, but doesn't
perform the optimization itself. The key distinction is in robustness
to perturbations in the goals of the wielder. The optimization performed
using a tool AI optimizes toward goals which can change
greatly as the goals of the wielder change. This is a general property
of friendly AI, though its worth noting that we would really like
using the AI to optimize toward toward ... As such, Tool AIs can't be friendly,
merely safe.

<!-- something here about how using a tool AI might not further your goal? -->

<!-- As such, tool AIs are in the same danger category as a nuclear bomb: they might -->
<!-- kill a bunch of people, but you'll have to launch them first. -->


The next question we need to ask is whether or not a tool AI can even exist and be _Tsukaeru_?
Can something with no optimization ability or agency even be intelligent?
Well this comes down to definitions, so we'll taboo intelligence and simply discuss
capabilities.

<!-- Ok so maybe below is obvious and a waste of time? -->

How could we train a tool AI to do useful things? We could train to imitate or
predict instead of optimizing for outcomes. Perhaps apply some iterative
amplification or similar and boom, you've got an tool AI which do useful
things.

Did you catch it?

The error in the above reasoning? Take a second and think through what's
wrong before peeking.

:::spoiler
 
Just because an AI is trained to imitate or predict doesn't mean it's a tool AI!

For instance, consider an AI trained to predict the action a human would take.
If this AI was really good, it behaves exactly like a human. At this point, the
AI would be optimizing its environment because humans optimize their
environments.

<!-- In fact, it seems reasonably likely that such AI produced by -->
<!-- techniques similar to current ML would _intend_ to optimize its environment. -->
<!-- The behavior of acting exactly like a human might end up being represented -->
<!-- as simply understanding the goals, irrationalities, and beliefs of the human -->
<!-- and optimizing based on them. -->

Something, something Q function.

For an even more absurd case, consider training an AI to predict
the outputs of some other AI which optimizes for an some objective.
Clearly this new AI would also optimize for the same objective.
In fact, my understanding of distillation would indicates that if both of these
AIs are trained using something like current ML, the internal reasoning of the
new AI would likely end up being similar to that of the original AI!

:::

So, there isn't an obvious way to train a tool AI. In fact, we don't even
have a way to train an AI and evaluate its agency which seems deep property,

something something ontological dread, something something.
something something generalization, something something.
While some training approaches could result in reduced agency...
Something, something, we don't know.
Something something, agency in generalization?
So something imply must be agentic, but non-agentic could be carried out by agent.

At this time, I'm not aware of any pivotal act which a tool AI could obviously
carry out. A tool AI could help speed up alignment research, but probably not
astronomically, so it doesn't really help us here. 
Perhaps there is some IDA type structure... (TODO)

The alignment tax seems high overall.

[tools want to be agents](https://www.gwern.net/Tool-AI)

Given the likely incompetence of such an AI we'll try a different approach
next: constructing an intelligent utility maximizer and restraining its
capabilities.


## Restrained AIs

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
