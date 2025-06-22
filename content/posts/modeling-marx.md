---
title: "Investigations in Computational Marxian economics"
date: 2025-06-22T00:49:56+02:00
---

This is an open WIP.

_Abstract_

I'm looking into computational methods on classical-Marxian economics. I also have some ideas as to use homotopy type theory to model historical materialism:

> Marx argued that the economic base of a society—the "mode of production," which includes the forces of production (technology, labor) and the relations of production (class structures)—conditions the legal, political, and ideological "superstructure."

Why homotopy type theory? Well, if we have that:

> If A is a type in universe U*i and for every x : A, the type B(x) is in universe U_j, then the dependent function type (x : A) -> B(x) resides in the universe U*{max(i, j)}.

Then HoTT could allow us to model the "mode of production" and the "relations of production" as a dependent type. In pseudo cubical-Agda:

```
variable
 𝓤 𝓥 𝓦 : Universe -- 𝓤 𝓥 𝓦 are Universes in HoTT

ProductionRelations : 𝓤 -- ProductionRelations belongs to 𝓤
ProductionMode : 𝓥 -- ProductionMode belongs to 𝓥
Superstructure : 𝓦 -- Superstructure belongs to 𝓦

ξ : ProductionForces -- ξ belongs to ProductionRelations (technology, labour)
Ψ : ProductionMode -- Ψ belongs to ProductionMode (class structures)
φ : ξ x Ψ -- Dot product
ρ : Superstructure (social and political life)

(x : ρ) -> φ(x)
```

The nice thing is that if we use a cubical system for example, to model this dependency types, we can leverage the univalence theorem to find equivalent (up to isomorphism) `ProductionMode`s different from that of capitalism, to then model this equivalence as a path in a space.

References:

- [Computational methods and classical-Marxian economics](https://onlinelibrary.wiley.com/doi/10.1111/joes.12459)
- [An Agent-Based Approach to Classical-Marxian Value Theory and Labor Mobility](https://jonathancogliano.com/wp-content/uploads/2018/10/Cogliano-Agent-Based-Approach-to-Value-Theory.pdf)
- [Prediction and Description in Marxian Value Theory](https://nsereview.org/index.php/NSER/article/view/122)
