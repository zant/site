---
title: "Abstract Algebra from scratch in Haskell"
date: 2022-09-17T00:49:56+02:00
draft: true
---

While learning Haskell is impossible not to notice the use of mathy objects like `Monoids` and `Semigroups` within `GHC.Base`. Then you get to learn that surprisingly, lists (`[]`) are `Monoids`! And then you start having curiosity about, what about really mathy objects, and how can they be represented via typeclasses and Haskell?

Well, that at least happened to me - and this post is going through the construction and definition of the cyclic group `z2` and its way on algebraic structures up to being a well behaved Group. Let's get started!

Because we want to user proper names but we don't want to prefix things with `My` for god's
so let's make sure we're can use our functions in qualified form:

{{< highlight haskell >}}
module Lib where
{{< / highlight >}}

We start by defining the z2 cyclic group:

{{< highlight haskell >}}
data Z2 =
    E |
    A deriving (Show)
{{< / highlight >}}

After that, we define a semigroup as we cannot start with a magma. This is because a magma is only (M, •) i.
e. a set and a binary operation. However, in order to define a Haskell typeclass we need _some_ restriction
in the constructor. 

Now, as Haskell is right associative already, we only need to specify that the typeclass needs a function
of two arguments (binary operation) that returns a value of the same type (closure).

{{< highlight haskell >}}
class Semigroup a where
    (<>) :: a -> (a -> a)
{{< / highlight >}}

The encoding of the multiplication table will be done by the `dot` function. This was the tricky part
to construct from zero.

{{< highlight haskell >}}
dot :: Z2 -> Z2 -> Z2
dot E A = A
dot A E = A
dot E E = E
dot A A = E
{{< / highlight >}}

We can see that it accurately reflects its multiplication table:

![](/img/z2_table.png)

We can now finally instantiate our Semigroup class with Z2 and specifying the binary associative operation!
In this case will be dot, which we previously defined to encode our times table.

{{< highlight haskell >}}
instance Lib.Semigroup Z2 where
    (<>) = dot
{{< / highlight >}}

If we do a quick test, we can see that our function is indeed associative:

{{< highlight haskell >}}
main = do
    putStrLn $ "Semigroup (assosiacivity) - (A <> A) <> E = " ++ show
        ((A Lib.<> A) Lib.<> E)
    putStrLn $ "Semigroup (assosiacivity) - A <> (A <> E) = " ++ show
        (A Lib.<> (A Lib.<> E))
{{< / highlight >}}

This will output:

{{< highlight plaintext >}}
Semigroup (assosiacivity) - (A <> A) <> E = E
Semigroup (assosiacivity) - A <> (A <> E) = E
{{< / highlight >}}

Nice, we're associative :)

Okay, let's do something more fun now. We now that adding an identity element to a `Semigroup`
will mean having a `Monoid`. Let's leverage Haskell's typeclasses power and inherit `Semigroup`
with its associative operation, and add an identity element.

{{< highlight haskell >}}
class Lib.Semigroup a => Monoid a where
    mempty :: a
{{< / highlight >}}

Pretty, cool. Let's now instantiate `z2` with it.

{{< highlight haskell >}}
-- E is our identity element, so this is straight forward
instance Lib.Monoid Z2 where
    mempty = E
{{< / highlight >}}

A quick sanity check:


{{< highlight haskell >}}
main = do
    putStrLn $ "Monoid (+identity element) - A <> E) = " ++ show
        (A Lib.<> Lib.mempty)
    putStrLn $ "Monoid (+identity element) - E <> E) = " ++ show
        (E Lib.<> Lib.mempty)
{{< / highlight >}}

And output:

{{< highlight plaintext >}}
Monoid (semigroup w identity element) - A <> E) = A
Monoid (semigroup w identity element) - E <> E) = E
{{< / highlight >}}

Great, `Monoids` are cool. Let's finally move to `Group`s now! 

We follow the same approach and inherit, instantiate and print some of our properties. 

For this one we will need to add an `invert` function to `Monoid` so we have invertibility.

This will be defined by having an `invert` function such that:

{{< highlight plaintext >}}
a <> invert a == mempty
invert a <> a == mempty
{{< / highlight >}}

Let's define it!

{{< highlight haskell >}}
class Lib.Monoid a => Group a where
    invert :: a -> a

-- because the only way to get mempty in z2 is by 
-- doting and element by itself
-- our invert function is dot by the identity element
instance Lib.Group Z2 where
    invert = dot Lib.mempty

-- print print
main = do
    putStrLn $ "Group (monoid + inverse) - invert A <> A) = " ++ show
        (invert A Lib.<> A)
    putStrLn $ "Group (monoid + inverse) - A <> invert A) = " ++ show
        (A Lib.<> invert A)
    putStrLn $ "Group (monoid + inverse) - invert E <> E) = " ++ show
        (invert E Lib.<> E)
    putStrLn $ "Group (monoid + inverse) - E <> invert E) = " ++ show
        (E Lib.<> invert E)
{{< / highlight >}}

Output:

{{< highlight plaintext >}}
Group (monoid + inverse) - invert A <> A) = E
Group (monoid + inverse) - A <> invert A) = E
Group (monoid + inverse) - invert E <> E) = E
Group (monoid + inverse) - E <> invert E) = E
{{< / highlight >}}

Great no? We have created our own small ADT for z_2, defined `Semigroup`, `Monoid` and `Group` typeclasses
and instantiated our `z_2` ADT to make use of the methods within this typeclasses so we make it both
explicitly and fun to experiment with our small little cyclic group.