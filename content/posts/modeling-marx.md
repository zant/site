---
title: "Investigations in Computational Marxian economics"
date: 2025-06-22T00:49:56+02:00
---

This is an open WIP.

**Abstract**

I'm looking into computational methods on classical-Marxian economics. I also have some ideas as to use homotopy type theory [0] to model historical materialism:

> Marx argued that the economic base of a society—the "mode of production," which includes the forces of production (technology, labor) and the relations of production (class structures)—conditions the legal, political, and ideological "superstructure."

Why homotopy type theory? Well, if we have that:

> If A is a type in universe U*i and for every x : A, the type B(x) is in universe U_j, then the dependent function type (x : A) -> B(x) resides in the universe U*{max(i, j)}.

Then HoTT could allow us to model the "mode of production" (production forces, relations of production) and the "superstructure" as a dependent function type. In pseudo cubical-Agda:

```
variable
 𝓤 𝓥 𝓦 𝓣 : Universe -- 𝓤 𝓥 𝓦 𝓣 are Universes in HoTT

ξ : 𝓤 -- ξ is the forces of production (technology, labour), in 𝓤
Ψ : 𝓥 -- Ψ are the relations of production (class structures), in 𝓥, not sure if they belong to the same universe with the forces of production, but having a cartesian product could be fun
φ : ξ x Ψ : 𝓤 x 𝓥 -- φ is the mode of production, the cartesian product (tensor product) the set of all (forces of production, relations of production), this product could be thought of as tensor product in a cartesian closed category?
ρ : 𝓣 -- ρ is the superstructure (social and political life), in 𝓣

(x : φ) -> ρ(x) -- so different superstructures (e.g. socialist, communist, capitalist) could be indexed by different modes of production? with relations of production Ψ that are not based on class structures?
```

The nice thing is that if we use a cubical system for example, to model this dependency types, we can leverage the univalence theorem to find equivalent (up to isomorphism) `ProductionMode`s different from that of capitalism, to then model this equivalence as a path in a space.

[0]: [Cubical methods in homotopy type theory and univalent foundations](https://www.cambridge.org/core/journals/mathematical-structures-in-computer-science/article/cubical-methods-in-homotopy-type-theory-and-univalent-foundations/ECB3FE6B4A0B19AED2D3A2D785C38AF9)

Proposed literature:

- [Computational methods and classical-Marxian economics](https://onlinelibrary.wiley.com/doi/10.1111/joes.12459)
- [An Agent-Based Approach to Classical-Marxian Value Theory and Labor Mobility](https://jonathancogliano.com/wp-content/uploads/2018/10/Cogliano-Agent-Based-Approach-to-Value-Theory.pdf)
- [Prediction and Description in Marxian Value Theory](https://nsereview.org/index.php/NSER/article/view/122)
