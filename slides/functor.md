
### Recap: What's a Functor?

<aside class="notes" data-markdown>
- neues projekt
</aside>

<!-- .slide: data-background="img/background-green-16x9.png" -->

_The Functor class is used for types that can be mapped over. [...] – hackage.haskell.org_
<!-- .element: class="fragment" data-fragment-index="1" -->

```
class  Functor f  where
    fmap        :: (a -> b) -> f a -> f b
```
<!-- .element: class="fragment" data-fragment-index="2" -->

---
<!-- .slide: data-background="img/background-green-16x9.png" -->

```
> fmap (+3) (Just 2)
Just 5
```
<p><img class="simpleImage" src="img/fmap_just.png" title="fmap that shit" width="100%"></p>
<!-- .element: class="fragment" data-fragment-index="2" -->

```
instance  Functor Maybe  where
    fmap _ Nothing       = Nothing
    fmap f (Just a)      = Just (f a)
```
<!-- .element: class="fragment" data-fragment-index="3" -->

```
> fmap (+3) Nothing
Nothing
```
<!-- .element: class="fragment" data-fragment-index="4" -->
---
<!-- .slide: data-background="img/background-green-16x9.png" -->
### Exercises borrowed from haskellbook.com
<p><img class="simpleImage" src="img/haskellbook.png" title="a gorgeous book" width="50%"></p>
---
<!-- .slide: data-background="img/background-green-16x9.png" -->
### Determine if the following datatypes allow to have a Functor instance
---
<!-- .slide: data-background="img/background-green-16x9.png" -->

```
data Bool = False | True
```
```Nopes: kind *```
<!-- .element: class="fragment" data-fragment-index="2" -->
---

<!-- .slide: data-background="img/background-green-16x9.png" -->
```
data BoolAndSomethingElse a = False' a | True' a
```
```Yes: kind * → *```
<!-- .element: class="fragment" data-fragment-index="2" -->
---

<!-- .slide: data-background="img/background-green-16x9.png" -->

```
data BoolAndMaybeSomethingElse a = Falsish | Truish a
```

```Yes: kind * → *```
<!-- .element: class="fragment" data-fragment-index="2" -->
---

<!-- .slide: data-background="img/background-green-16x9.png" -->
```
newtype Muf = InF { outF :: f(Mu f) }
```
```Yes: kind * → *```
<!-- .element: class="fragment" data-fragment-index="2" -->
---

<!-- .slide: data-background="img/background-green-16x9.png" -->
```
import GHC.Arr

data D = D (Array Word Word) Int Int
```
```No: data D =…​ not a * → *```
<!-- .element: class="fragment" data-fragment-index="2" -->
---
<!-- .slide: data-background="img/background-green-16x9.png" -->
### Time for Haskell Codin'

### GOTO [goo.gl/E2ofCZ](http://goo.gl/E2ofCZ);
