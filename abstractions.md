# TODO

Recently I've seen discussion of how ...

This post is unfortunately unfocused, but there are two main aims:
- Abstracting/categorizing types of safe AI and why those types may fail.
- Making the case that we should be studying whether or not current approaches
  can result in deontological agents and how that scales with capabilities.

We'll make the following assumptions:
1. Highly capable and intelligent AIs which basically act like expected utility
   maximizers (aka Consequentialists) would kill us all if created with
   *current _*.
2. Societal and government competence and coordination aren't very high.

I am not certain that both of these assumptions are true and I can imagine
scenarios in which they wouldn't hold. However, I would be very surprised if
either claim was totally false and I think that they are useful assumptions for
reducing the safe AI search space. I make the case for why these are good
assumptions in the appendix to avoid clutter (because I'd guess most readers
already buy them). If you think that at least one of these hypothesises aren't
true, well maybe pick a different article to read.


<!-- Something something, criteria including discussion of pivotal act. -->

Now, lets try to see what a safe AI which could be used for pivotal act looks like.
What's a pivotal act you say? Some sort of action which is able to ensure unsafe AI isn't produced by someone else.
For example, maybe your safe AI conquers the world yielding a golden age under the new Yudkow-tocracy.

Given that we've said that expected utility maximization is a big no-no, what if we considered 
AIs which don't (intentionally) optimizer their environments at all?
Specifically we'll first consider AIs which possess no agency: tool AIs. 

## Tool AIs

By definition, tool AIs aren't mesa-optimizers, so inner alignment isn't a concern.
As such, they're in the same danger category as a nuclear bomb: they might kill
a bunch of people, buy you'll have to launch them at someone first.

The first question we need to ask is whether or not a tool AI can even exist?
Can something with no optimization ability or agency even be intelligent?
Well this comes down to definitions, so we need skip this questions in favor
of a different one: are the capabilities sufficient?

At this time, I'm not aware of any pivotal act which a tool AI could obviously
carry out. A tool AI could help speed up alignment research, but probably not
astronomically, so it doesn't really help us here. 
Perhaps there is some IDA type structure... (TODO)

The alignment tax seems high overall.

[tools want to be agents](https://www.gwern.net/Tool-AI)

Given the likely incompetence of such an AI to even be intelligent,
we'll try a different approach next: 
constructing an intelligent utility maximizer and restraining
its capabilities.


## Restrained AIs

For an example of a restrained AI, consider an AI which operates
as a long term goal achieving consequentialist in some sort of
constrained environment (e.g. theorem proving) without even
knowing about the real world. Or consider AIs (hopefully) made safer
by somehow removing their ability to model humans.
Both of these AI have had their capabilities handicapped to reduce danger.
Additionally, the classic 'boxed' AI is an example of this approach and the
typically proposed issues generalize to restrained AIs more generally.
The earlier examples are also 'boxed', just knowledge boxed
instead of isolated via some other mechanism.

Such AI could theoretically not be intent aligned and be highly
capable consequentialist agents while also being safe.
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
