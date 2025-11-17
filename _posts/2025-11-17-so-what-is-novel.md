---
layout: post
title: So Did You Come Up With A Novel Idea?
comments: true
excerpt: "We throw around the phrase **novel idea** a lot, especially in tech and research. But what is novelty really, and how do you even begin to measure it?"
---

# So Did You Come Up With A Novel Idea?

I think I have come across this wordplay quite a bit of late: this is a "novel idea" or "can AI create a novel thesis"? Two things come to mind when I hear this. First is the obsession we have with novel ideas, especially among founders and researchers. Second is: what is even a novel idea, how do you define it?

In 3, 2, 1... I dive down the second rabbit hole.

## So What Is Novelty?

The irony of trying to define this is that nothing is truly novel. If you think about how we conceive ideas, it is quite clear that all our ideas are inspired by some other source.

The best of breakthroughs, say Einstein's special relativity, definitely builds on ideas from Lorentz and Poincare's model of local time and local contraction; Maxwell's idea of finite speed of light; Riemann's mathematical framework for curved space, etc. But am I downplaying the actual breakthrough? For sure not. Even though local time as a concept existed, the idea that time and space are the same is still a jump. Discarding ether completely was a brave stance.

If you look at something that I was following when it happened, the now folklore paper *Attention Is All You Need*, I remember reading it back in the day and thinking, "Quite smart." Neither attention, self-attention, nor encoder decoders were novel ideas. Even using conv nets plus attention in place of RNNs was already a thing (RNNs had gotten the bad repute by then because of vanishing or exploding gradient problems). However, the paper unifying attention in all layers and multi-head attention felt like what really gave the results. ChatGPT tells me even ideas around multiple hops or memory slots existed before the paper came out.

Even if you look at some of the pioneering works in machine learning, a bunch of ideas were borrowed from thermodynamics, whether it is Boltzmann machines, energy based models and energy based learning, the equilibrium propagation paper, etc. So even things that seem novel could have their roots in very interesting and different sources.

That is where the **genius of a scientist lies, I think, in the ability to synthesise ideas or match patterns from the most orthogonal spaces.**

I think my conclusion from all this is that novelty is not a binary concept for sure. It is a spectrum.

## So How Do You Measure Novelty?

Like anything in physics that is a spectrum measurement, the usual trick in the book is to define the lowest and highest end points and then go about the business knowing these two are etched in stone. But that seems too sticky a definition, considering we do not know what the least was or will ever be, or what the highest was or will ever be.

The next best trick is to define it in terms of a fixed index (like specific gravity or refractive index), but that means you have to take a fundamental paper (or maybe papers in different sub fields) and compare them. The most pertinent challenge with this measurement is how fine grained you keep making the benchmark paper.

Do you have a benchmark paper for the whole of science, the whole of computer science, the whole of applied ML, the whole of language models, the whole of diffusion language models... you get the drift?

So I think the best way to do this is to compare among peers, a group that largely comprises mostly of peers who are addressing the same problem, or using the same methodology, or working on a similar application.

## Now Within This Group, What Is The Ranking Mechanism?

The idea here is that there are fundamental parts to a research idea (and I am going to focus specifically on research papers now) where there is a hierarchy of ideas.

If it is a methodology paper, then there is a core methodology, like inventing a new kind of neural network architecture. Or there is a slightly lower level of innovation in maybe an existing neural network architecture that uses something new, like residual connections.

You could keep going like this and define a hierarchy of novelty, whether it is at the level of architecture, training mechanism, training loss, or even dataset. If you are able to successfully define such a hierarchy, then suddenly a ranking mechanism looks more likely than otherwise.

A long blog, this one, but I think, borrowing from other ideas of measurement, we can now measure novelty. Quite the irony.
