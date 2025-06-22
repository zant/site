---
title: "Investigations in Computational Marxian economics"
date: 2025-06-22T00:49:56+02:00
---

this is an open WIP. i have to learn a bunch of game theory i have no idea about, so don't trust in any of the math yet lol

**Abstract**

I'm looking into computational methods on classical-Marxian economics. I also have some ideas as to use homotopy type theory [0] to model historical materialism:

> Marx argued that the economic base of a society—the "mode of production," which includes the forces of production (technology, labor) and the relations of production (class structures)—conditions the legal, political, and ideological "superstructure."

Why homotopy type theory? Well, if we have that:

> If A is a type in universe U*i and for every x : A, the type B(x) is in universe U_j, then the dependent function type (x : A) -> B(x) resides in the universe U*{max(i, j)}.

Then HoTT could allow us to model the "mode of production" (production forces, relations of production) and the "superstructure" as a dependent function type. I ended up with some approximation of a structure similar to a ([locally cartesian closed category](https://ncatlab.org/nlab/show/locally+cartesian+closed+category)) because at the end I'm trying to model dependent types, what homotopy type theory uses to model Universes.

> A locally cartesian closed category is a category C whose slice categories C / x are all cartesian closed. [1]

The univalence Axiom says there's an equivalence between equivalence and equality, which Cubical Type Theory constructs, this is just a property of a Martin-Löf dependent type theory. (i hope)

> Voevodsky’s way to achieve this is to start with a Martin-Löf type theory (MLTT), including identity types and type universes, and postulate a single axiom, named univalence. [3]

Now, taking in mind the relationship between a locally cartesian closed category and Martin-Löf dependent type theory[2].

> **Dependent type theory and locally cartesian closed categories**
> We discuss here how dependent type theory, is the syntax of which locally cartesian closed categories provide the semantics. For a dedicated discussion of this (and the subtle coherence issues involved) see also at categorical model of dependent types.
>
> Theorem 3.2. There are 2-functors [1]
>
> Cont, that forms a category of contexts of a Martin-Löf dependent type theory;
> Lang that forms the internal language of a locally cartesian closed category.
>
> that constitute an equivalence of 2-categories

> MLDependentTypeTheories ⟵Lang≃⟶Cont LocallyCartesianClosedCategories

> Definition 3.4. Given a dependent type theory T, its category of contexts Con(T) is the category whose
>
> - objects are the types of T;
> - morphisms f: A → B are the terms f of function type A → B.
>   Composition is given in the evident way.
>
> Proposition 3.5. Con(T) has finite limits and is a cartesian closed category.

So now we can better define our locally cartesian closed category:

> 1. Definition>
>    A locally cartesian closed category is a category C whose slice categories C / x are all cartesian closed.
>
> If a locally cartesian closed category C has a terminal object, then C is itself cartesian closed and in fact has all finite limits (because, cartesian products in C / x are pullbacks in C); often this requirement is included in the definition.
>
> Equivalently, a locally cartesian closed category C is a category with pullbacks (and a terminal object, if required) such that each base change functor f\* : C / y → C / x has a right adjoint Π_f, called the dependent product. (This equivalence is discussed in detail below.)
>
> In particular, such pullbacks preserve all colimits. Therefore, if a locally cartesian closed category has finite colimits, it is automatically a coherent category, and in fact a Heyting category.

And now with a little help of topos theory,

> The “fundamental theorem” of topos theory, in the terminology of McLarty 1992, asserts that for any topos 𝒯 and x ∈ 𝒯 any object, also the slice category 𝒯/x is a topos: the slice topos. [4]

We have the following:

> With all of these axioms included, homotopy type theory behaves like the internal language of an (∞,1)-topos, and conjecturally should admit actual models in any (∞,1)-topos. [5]

So we now model Universes as if they were toposes in a (∞,1)-topos, which has nice properties:

                  Paths(x, y) -------->   1
                   |                  | (x,y)
                   | (pullback)       |
                   ↓                  ↓
                   A ---------------> A × A
                         δ (diagonal)

So now we can even be satisfied with saying that using Cubical Agda, we're treating with a (∞,1)-topos, which is a homotopy type theory [6]:

> We prove the conjecture that any Grothendieck (∞, 1)-topos can
> be presented by a Quillen model category that interprets homotopy type theory
> with strict univalent universes. Thus, homotopy type theory can be used as a
> formal language for reasoning internally to (∞, 1)-toposes, just as higher-order
> logic is used for 1-toposes.

Or we can _conjecturally_ [5] say it's a cubical type theory:

> The Cartesian cubical model of cubical type theory and homotopy type theory is conjectured to be an (∞,1)-topos not equivalent to (∞,1)-groupoids. [6]

In any case, thinking of our different objects (Forces of Production ξ, Relations of Production Ψ, etc) as toposes in a (∞,1)-topos, will allow us to model Marxian economics in the following way in cubical [7] Agda (pseudocode):

```
variable
 𝓤 𝓥 : Universes

-- Forces of Production (technology, labour) is a type ξ, type in 𝓤
ξ : Type 𝓤
-- Relations of Production (class structures) is a type Ψ, type in 𝓤
Ψ : Type 𝓤

-- Mode of Production φ (forces of production, relations of production) is the
tensor product that takes (ξ x Ψ in 𝓤)
φ : Type 𝓤 := ξ × Ψ

-- seeing properties of paths in this context is fun 
apply0 : (Ξ : Type 𝓤) (p : I → Ξ) → Type Ξ
p Ξ p = p i0

path1 : {Ξ : Type 𝓤} (x : Ξ) → x ≡ x
path1 x = λ i → x

-- Superstructure ρ (social and political life)
-- dependent type family 𝓥 indexed by 𝓤 
-- (x : 𝓤) → 𝓥(x)
-- this is the type def, not sure about the structure yet
-- ρ is a dependent type family (function) that takes:
-- a mode of production Ξ in φ (Type 𝓤) and returns a superstructure in Type 𝓥
ρ : {Ξ : φ} (x : Ξ) → Type 𝓥

-- so different superstructures (e.g. socialist, communist, capitalist) 
-- could be indexed by different modes of production?
-- with relations of production Ψ that are not based on class structures?
```

The nice thing is that if we use a cubical system for example, to model this dependency types, we can leverage the univalence theorem to find equivalent (up to isomorphism) `ProductionMode`s different from that of capitalism, and with cubical we get this equivalence as a path in a space for free.

[0]: [Cubical methods in homotopy type theory and univalent foundations](https://www.cambridge.org/core/journals/mathematical-structures-in-computer-science/article/cubical-methods-in-homotopy-type-theory-and-univalent-foundations/ECB3FE6B4A0B19AED2D3A2D785C38AF9)

[1]: [locally cartesian closed category](https://ncatlab.org/nlab/show/locally+cartesian+closed+category)

[2]: [Dependent type theory and locally cartesian closed categories](https://ncatlab.org/nlab/show/relation+between+type+theory+and+category+theory#DependentTypeTheory)

[3]: [Introduction to Univalent Foundations of Mathematics with Agda](https://martinescardo.github.io/HoTT-UF-in-Agda-Lecture-Notes/HoTT-UF-Agda.html#universes)

[4]: [homotopy type theory](https://ncatlab.org/nlab/show/homotopy+type+theory#models_in_categories_and_toposes)

[5]: [Quillen model structure](https://groups.google.com/g/homotopytypetheory/c/RQkLWZ_83kQ/m/s6iazlFdBgAJ)

[5]: [All \(∞,1\)-toposes have strict univalent universes](https://arxiv.org/abs/1904.07004)

[6]: [cubical type theory](https://ncatlab.org/nlab/show/%28infinity%2C1%29-topos#cubical_type_theory)

[7]: [cubical github](https://github.com/agda/cubical)

Proposed literature:

- [Computational methods and classical-Marxian economics](https://onlinelibrary.wiley.com/doi/10.1111/joes.12459)
- [An Agent-Based Approach to Classical-Marxian Value Theory and Labor Mobility](https://jonathancogliano.com/wp-content/uploads/2018/10/Cogliano-Agent-Based-Approach-to-Value-Theory.pdf)
- [Prediction and Description in Marxian Value Theory](https://nsereview.org/index.php/NSER/article/view/122)
