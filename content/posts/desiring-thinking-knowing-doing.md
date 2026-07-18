---
title: "Desiring, Thinking, Knowing, Doing"
date: 2026-07-18T16:14:13-04:00
draft: false
---

_This article has been posted to my [Substack](https://cjauvin.substack.com/p/desiring-thinking-knowing-doing) also._

Consider these situations:

1. You want to write a novel

2. Someone asks you what is the capital of Norway

3. Someone asks you how you feel today

4. Someone is telling you that their program has a bug

Suppose that you would want to write a classic program (GOFAI-style), as an agent able to implement (perform) these four scenarios. How would it work?

The first scenario should implement a kind of “desire state”. That desire state should have some “target”, which could be something like: a world in which a beautiful new novel exists, or simply, a desire to produce an interesting sequence of words, by itself.

The second scenario should implement a kind of “recognition that a question is asked”, and should also involve a mechanism of “desire to answer it”, akin to 1. There should be also a notion that this is a question “about the real world”, which involves “objective knowledge”, and which also involves the question of “knowing it” (or not).

The third scenario should also recognize that a question is asked, but this time, that it is about some “internal state”, which is subtly different than the “external world”. There should be the implicit notion that this is not objective in the same sense as 2 (i.e. it’s a very different type of “target”). In this scenario, it doesn’t really make sense to “not know” the answer.

The fourth scenario also involves (implicitly) a question and an answer, but this time things imply a lot more “doing”: the program will need to act on the world, look at it, manipulate it, etc. in order to produce an “answer”, whose value will be defined in terms of how “successful” something will be, in the end.

Just consider how varied the different mechanisms involved in these scenarios are, and how difficult it is to simply begin to imagine, how they could be implemented in the substrate of a classic programming language (GOFAI-style). Now consider that all these things are implemented natively by a large language model, emerging as the by-product of its brutally simple objective: look at the big bunch of textual data, and “learn” from it what is the most likely way to continue a given sequence of symbols. This is an amazingly shocking scientific discovery, about what it means to “behave” in at least those four ways.
