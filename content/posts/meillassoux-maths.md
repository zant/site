---
title: Meillassoux's Mathematics
date: 2021-10-06
---

## Contents

- [Introduction](#introduction)
- [Après la finitude](#après-la-finitude)
- [Set Theory](#set-theory) 
	- [Origins](#origins)
	- [ZF Set Theory](#zf-set-theory)
	- [Cardinality](#cardinality)
	- [Infinite sets](#infinite-sets)
- [Cantor's Theorem](#cantors-theorem)
- [What Meillassoux really meant](#what-meillassoux-really-meant)
	- [Cantor's Paradox](#cantors-paradox)
- [Conclusion](#conclusion)
- [Appendix A: Why is it called a paradox?](#appendix-a-why-is-it-called-a-paradox)

## Introduction

The following post will elaborate on the specificity and technical details in a mathematical argument made in Quentin Meillassoux's essay _Après la finitude_.

This post will provide the necessary background to follow all concepts embbedded in the mathematical references made by Meillassoux in his essay.

This post intends to be a guide over the mathematical references of the essay, as so, I'll heavily quote sentences to start referencing the mathematical details. All quotes are from the last section of the chapter "Hume's Problem".

**Disclaimer:** This post does not intend to be an exhaustive or even correct interpretation of the essay. I'm not a professional mathematician and please check all citations and resources linked.

## Après la finitude

_After Finitude: An Essay on the Necessity of Contingency_ is the name of the essay made by Quentin Meillassoux. The central subject of the essay is _the absolute_ and the relationship of philosophers with it.

As a rookie in Philosophy and this being one my first formal treatment, all I can say is that is a really interesting piece consisting of many moving parts, deep arguments and a good chunk of history of philosophy.

What's remarkable about this essay in particular, and what settles the topic of this post is that Meillassoux not only relies on logical arguments and syllogisms via natural language, but it also references and build on top of mathematical theories and theorem to support his argument and logical deductions.

## Set Theory

The main mathematical subject Meillassoux is relying on for supporting his argument is [Set Theory](https://en.wikipedia.org/wiki/Set_theory). Quoting the philosopher:

> In order to be as concise and as clear as possible about the
> issue of the transfinite, we can put things in the following way:
> one of the most remarkable aspects of the standard axiomatization
> of set-theory (known as 'ZF', for 'Zermelo-Fraenkel'),
> progressively elaborated during the first half of the twentieth
> century on the basis of Cantor's work, consists in its
> unencompassable pluralization of infinite quantities.

There's a lot to unpack in this first paragraph. But to understand what Meillassoux means about _"the standard axiomatization of set-theory"_ we first need to take a look at its origins, and what it means to have _an standard axiomatization_.

### Origins

Set Theory was first developed by the mathematician [George Cantor](https://en.wikipedia.org/wiki/Georg_Cantor) around the second half of the 19th century. This development was part of Cantor's study of the infinite.

Due to the utility of set theory as a tool to develop other subjects, it started to became more widespread. Naturally, as more mathematicians were catching up on it, some of them noticed that this first development, known as [Naive Set Theory](https://en.wikipedia.org/wiki/Naive_set_theory) had contradictions in it. 

This was mainly due to the fact of beign able to express sets with natural language, which leads to the most prominent example called Russell's Paradox [1], named after philosopher Bertrand Russel. This paradox can be expressed as follows:

> Consider the set of all sets that are not members of themselves

Should that set be within itself? If it does, then it's a member of itself, and cannot be within itself anymore. But if it doesn't, the set wouldn't be comprising _all_ sets, as the containing set will be missing.

This exposes the need of a more rigorous treatment of the theory, which will try to be circumvent this issues.

### ZF Set Theory

Introducing Zermelo-Fraenkel Set Theory, the first axiomatization of the subject. 

An axiomatization is the process of giving a theory a set of [axioms](https://en.wikipedia.org/wiki/Axiom). With axioms, we no longer rely on interpretations of a theory, but in initial assumptions that are grounded logically and will be used to follow new statements, such as [lemmas](https://en.wikipedia.org/wiki/Lemma_(mathematics)) and [theorems](https://en.wikipedia.org/wiki/Theorem).

With ZF Set theory, sets were no longer defined in terms of natural language, but in terms of properties in first-order languages, such as the one of logic, used to describe the properties of the set free of the ambiguities of natural language.

There are several axioms within this axiomatization, but the most relevant to us are the following:

- Axiom schema of specification: For every set A and every given property, there is a set containing exactly the elements of A that have that property. A property is given by a formula φ of the first-order language of set theory. This axiom makes not possible to define sets via natural language, but with a first-order language. The consistency of this language will assure consistency of the theory. [2]
- Axiom of regularity: Every non-empty set A contains an element that is disjoint from A. This axiom together with the axiom of pairing implies that no set is an element of itself [3]

We now see why Meillassoux is talking about _"the standard axiomatization"_, as this axiomatization is just one of other possible axiomatizations. This is also why Meillassoux goes and bewares the reader of the following:


> We are not claiming that the non-totalizing axiomatic is the
> only possible (i.e. thinkable) one.
>
> [..]
>
> But this at least must be accorded to us: we have at our
> disposal one axiomatic capable of providing us with the resources
> for thinking that the possible is untotalizable.


### Cardinality

A really important definition from Set Theory for our purposes is the one of [cardinality](https://en.wikipedia.org/wiki/Cardinality). 

Informally, cardinality can be thought of _the size_ of a set. Formally, the definition looks like the following:

> Cardinality is defined in terms of bijective functions. Two sets have the same cardinality if, and only if, there is a one-to-one correspondence (bijection) between the elements of the two sets. [4]

This formal definition will be useful to understand key concept in Set Theory and Cantor's results within it, which are leveraged by our philosopher.

The one thing we need to know about this definition, is the one of _bijection_.

A **Bijection** is a function between the elements of two sets, where each element of one set is paired with exactly one element of the other set [5]. Let's see an example.

Imagine you have two sets:
- Friends, that will be denoted by X 
- Bycicle, that will be denoted by Y.

Now let's defined a _function_ between them. This function will be f(x) and it'll be defined as follows:

If one of my friends has a bycicle, then the result of the function will be the bicycle that my friend has. Or stated formally:

For all x of the set X, then f(x) = bycicle(x), an element of Y.

Now, if this function were a bijection, this will mean that _i have as much friends as bycicles in the set **and** each of my friends has one and only one bycicle different from any other friend_

So, there's a 1:1 relationship between the set of bycicle and the set of friends I have. Naturally, it's impossible to have that many friends, and that none of them are owning the same bycicle, so in this case it we account for reality, we will really a non-[injective](https://en.wikipedia.org/wiki/Injective_function) non-[surjective](https://en.wikipedia.org/wiki/Surjective_function) function.


An **surjection** is simply the fact that _each bycicle is owned by at least one of my friends_, which will not be the case if I have friends without bycicles.

A **injection** means that, _none of my friends share the same bycicle_, or that there's a one-to-one relationship between my friends and bycicles. 

Why all of this was relevant you may ask now. Besides beign super fun, let's consider an escenario where this is crucial.

### Infinite sets

First we defined cardinality as "the size" of a set. With this definition, it will be easy to say if a set is bigger than other just by looking and counting the elements within it. If I have 3 friends and there are 100 million bycicles in the set of bycicles, then clearly the set of bycicles is bigger.

The catch is that we can also have _infinite sets_. They are perfectly possible even in the axiomatic set theory, some examples can be the set of natural numbers or the set of real numbers.

So, how do we say than an infinite set is bigger than other infinite set? We cannot count them, as we will never finish. 

The answer is that, we look at a _function_ or [relation](https://en.wikipedia.org/wiki/Relation_(mathematics)) between the two sets. If this relation is bijective, then we have the same cardinality, as stated above. 

Now, bijection gives us information about equality. How do we know which is bigger? Here, we look at surjection and injection. 

Remember in the case of our friends and bycicles. We will have a surjection if it was the case that every bycicle had at least one of my friends as an owner. This is clearly not the case as there are so many more bycicles than friends I have, and they cannot possibly have al of them. 

The relationship between the set of my friends and the set of bycicles if not a surjection. Having an injection just means that there are some friends with bycicles, but none of them with the same bycicle. We can generalize this:

> X has cardinality strictly less than the cardinality of Y, if there is an injective function from X to Y, but no function that is both injective and surjective (bijective) from X to Y. [6] This is denoted by card(X) < card(Y).

The cool thing about Set Theory is that there's no difference between finite sets and infinite sets. So we do not need to count anymore to know if a set is bigger than other, we can just look at the possible maps existing between them!

**Fun fact:** The _infinite_ set of the real numbers is bigger than the _infinite_ set of the natural numbers. [7]

## Cantor's Theorem

Let's go back to Meillassoux for a moment, and see how he starts to develop his arument:

> 'Cantor's theorem', as it is known, can be intuitively glossed as follows: take
> any set, count its elements, then compare this number to the
> number of possible groupings of these elements (by two, by three
> but there are also groupings 'by one', or 'by all', which is
> identical with the whole set).
>
> You will always obtain the same
> result: the set B of possible groupings (or parts) of a set A is
> always bigger than A - even if A is infinite.o

We se that our philosopher is talking about "all possible groupings" of a set. This is the informal definition of a mathematical object called the [Power Set](https://en.wikipedia.org/wiki/Power_set). The power set is defined as follows:

> In mathematics, the power set (or powerset) of a set S is the set of all subsets of S, including the empty set and S itself.

First, a subset A from B is just a set which has the _some_ elements of B. For example, A = {1} is a subset of B = {1, 2}. This is a "grouping" in meillassoux terms.

We denote the power set of a set by P(S) beign S a set, if we define S = {a, b, c} then,

P(s) = {{}, {a}, {b}, {c}, {a,b}, {a, c}, {b, c}, {a, b, c}}.

Now, we're ready for the formal statement of Cantor's theorem!

> Let f be a map (relation) from set A to its power set P(A). f: A -> P(A) is not surjective. As a consequence, card(A) < card(P(A)) holds for any set A.

The power set of any set has always bigger cardinality (is bigger) than the original set! Isn't that cool?

## What Meillassoux really meant

We see that, at the beginning of the argument relying on Cantor's theorem, Meillassoux is being really explicit and even provided an intuitive definition of Cantor's theorem. However, let's keep looking at the development of the argument.

> It is possible to
> construct an unlimited succession of infinite sets, each of which is
> of a quantity superior to that of the set whose parts it collects
> together. 

Here, we can clearly see that Meillassoux is talking about taking the power set of a set S, denoted by P(S). And iteratively taking a new power sets based on the previous one. We can define this procedure as:

1. Take the power set of S
2. Let S now be this power set
3. Repeat step 1

We can see this visually, starting at S = S.

1. P(S). Take the power set of S.
2. S = P(S). Let S now be this power set.
3. P(P(S)). Take the power set of S.
5. S = P(P(S)). Let S now be this power set
6. P(P(P(S))

This procedure, together with the fact that card(P(S)) > card(S). Means that, if we keep taking on power sets, we will always have bigger and bigger cardinality for each one of them. Each new one having bigger cardinality than the previous one.

Now, we get an interesting claim:

> But this series itself cannot be
> totalized, in other words, it cannot be collected together into some
> 'ultimate' quantity. 

Followed by equally interesting claims such as:

> Thus, the set T (for Totality) of all quantities cannot
> 'contain' the quantity obtained by the set of the parts of T. 
> 
> [..]
> 
> For this totality of
> the thinkable is itself logically inconceivable, since it gives rise to a
> contradiction. We will retain the following translation of Cantor's
> transfinite: the (quantifiable) totality of the thinkable is
> unthinkable.

We see that Meillassoux is referencing the fact that there does not exist a set T that can possibly comprise all iterations of a power set P(S). In other words, there does not exists a set T of all iterations of the power sets of a set. No set can possibly contain P(s), P(P(S)), P(P(P(S))) and so on.

This is great and all but, this is _an statement_ and we don't see any intuitive reference of a theorem, or even a mention of a theorem. However, this is clearly a mathematical conclusion, and in general, mathematicians are pretty skeptic about statements without anything that backes them. Oh I thought you were cool Meillassoux!

### Cantor's Paradox

Let's still be kind with our philosopher and try to provider mathematical statements that can back his arguments. 

Looking again at the work of Cantor, we can see that he has an interesting result which could provide a mathematical, and subsequently, correct argument to what Meillassoux marks as the "the totality of the thinkable is unthinkable".

This result is known as Cantor's Paradox. But don't be fooled by its name, the paradox does not comes from the theorem itself - which is correct and consistent - but from the consequences of it. For our purposes, let's focus on the theorem itself, and remember that a statement which is a theorem, is matematically and logically correct.

> **Theorem:** If S is any set then S cannot contain elements of all cardinalities. In fact, there is a strict upper bound on the cardinalities of the elements of S.

This seems promising. Let's focus only on the first part of this assertion. 

If we think of this assertion in Meillassoux terms, let's first remember about our iterative process, that generated P(S), P(P(S)) an so on. By Cantor's theorem, we know that card(P(S)) > P(P(S)). So each term of the iteration will have _a different cardinality_.

So, in this iteration we have are constantly creating different cardinalities, one bigger than the other. But this theorem says that "Any set S cannot contain elements of all cardinalities". So, as we're creating always new cardinalities, and there's not set containing _all_ cardinalities, meaning at least one cardinality will not be there, then, it's impossible to have a set comprising all power sets! Or "all possible groupings in sequence" in Meillassoux terms.

With this last theorem, can see that Meillassoux was indeed mathematically backed, and this theorem explicitely tells us what we needed. That's a save! We can now safely go to bed knowing that our philosopher was indeed taking all mathematical cares to give us his conclusions.

## Conclusion

In this post we saw the history of Set Theory. How it was developed and why they are more than one Set Theory. We also defined and intuitively understood concepts such as bijections, relations, cardinality, and power sets. Definitions that are key to understand the formal statement of Cantor's theorem.

We also had a curiosity about the missing of mathematical references in the last statements of Meillassoux mathematical argument. We were eskeptic of this and went ahead and find a theorem matching the conclusion made by the philosopher in strict (and correct) mathematical terms.

## Appendix A: Why is it called a paradox?

> Since the cardinal numbers are well-ordered by indexing with the ordinal numbers (see Cardinal number, formal definition), this also establishes that there is no greatest ordinal number; conversely, the latter statement implies Cantor's paradox. By applying this indexing to the Burali-Forti paradox we obtain another proof that the cardinal numbers are a proper class rather than a set, and (at least in ZFC or in von Neumann–Bernays–Gödel set theory) it follows from this that there is a bijection between the class of cardinals and the class of all sets. Since every set is a subset of this latter class, and every cardinality is the cardinality of a set (by definition!) this intuitively means that the "cardinality" of the collection of cardinals is greater than the cardinality of any set: it is more infinite than any true infinity. This is the paradoxical nature of Cantor's "paradox". [8]

[1]: https://en.wikipedia.org/wiki/Russell%27s_paradox 
[2]: https://en.wikipedia.org/wiki/Axiom_schema_of_specification
[3]: https://en.wikipedia.org/wiki/Axiom_of_regularity
[4]: https://en.wikipedia.org/wiki/Cardinal_number
[5]: https://en.wikipedia.org/wiki/Bijection
[6]: https://en.wikipedia.org/wiki/Cardinality#Comparing_sets
[7]: https://en.wikipedia.org/wiki/Cantor%27s_diagonal_argument#:~:text=In%20set%20theory%2C%20Cantor's%20diagonal,cannot%20be%20put%20into%20one%2D
[8]: https://en.wikipedia.org/wiki/Cantor%27s_paradox#Discussion_and_consequences