{% macro seq(x,n="n") %} {{ x }}_1,\ldots,{{ x }}_{{n}} {% endmacro %}
{% macro seqf(f, x) %} {{ f }}({{ x }}_1),\ldots,{{ f }}({{ x }}_n) {% endmacro %}


## Manifesto

Since induction plays a crucial role in logic, it is worth taking a more precise look at it. Thus, induction is one of the salient parts of the metatheory that I promised to refine and explore further.

One builds a set recursively or inductively out of two ingredients &mdash; a set of initial objects, prototypically denoted by $$\mathscr{I}$$, and a set of rules, prototypically denoted by $$\mathscr{R}$$. A member of $$\mathscr{R}$$ is an $$(n+1)$$-ary relation $$R$$ where $$n$$ is a non-zero natural number. One can visualize it as a possibly infinite table:

|   Input  |           $$\ldots$$          |   Input  |   Output    |
|:--------:|:-----------------------------:|:--------:|:-----------:|
|  $$a_1$$ |$$\ldots\quad a_i \quad\ldots$$|  $$a_n$$ | $$a_{n+1}$$ |
|$$\ldots$$|           $$\ldots$$          |$$\ldots$$| $$\ldots$$  |
|  $$b_1$$ |$$\ldots\quad b_i \quad\ldots$$|  $$b_n$$ | $$b_{n+1}$$ |
|$$\ldots$$|           $$\ldots$$          |$$\ldots$$| $$\ldots$$  |

To express the fact that $${{seq("a")}},a_{n+1}$$ is a row in the table, one uses the notations $$R({{seq("a")}},a_{n+1})$$ and $$({{seq("a")}},a_{n+1}) \in R$$ interchangeably.

Occasionally, one also uses the notation $$R({{seq("a")}}) \sim a_{n+1}$$ and, in that case, one says that $$R$$ yields an output of $$a_{n+1}$$ on input(s) $${{seq("a")}}$$. However, one must be careful since $$R$$ is a relation and may not be function. It could yield multiple outputs on the same input.


## Definition Closure

**Closure**. A set $$S$$ is said to **closed** under an $$(n+1)$$-ary rule $$R$$ iff whenever $${{seq("a")}}$$ are all in $$S$$, then every $$a_{n+1}$$ satisfying $$R({{seq("a")}},a_{n+1})$$ is in $$S$$.


{% set I = "\\mathscr{I}" %}
{% set R = "\\mathscr{R}" %}
{% set clIR = "\\text{cl}(\\mathscr{I},\\mathscr{R})" %}

## Definition IDS

**Inductively Defined Set**. A set $$S$$ is defined by induction from a set of initial objects $${{I}}$$ and a set of rules $${{R}}$$ iff it is the smallest set such that:
1. $${{I}} \subseteq S$$
2. $$S$$ is closed under every rule in $${{R}}$$

One takes for granted that a set $$S$$, as defined above, always exists in the metatheory. As smallest sets are unique, one writes $$S$$ uniquely as $${{clIR}}$$ and calls it the **closure of $$\mathscr{I}$$ under $$\mathscr{R}$$**.

The set of natural numbers, $$\mathbb{N}$$, can be seen as the closure of $${{I}}\equiv\{0\}$$ and $${{R}}\equiv\{\text{succ}\}$$ where $$\text{succ}$$ is the binary successor relation (for each natural $$n$$, it outputs $$n+1$$).


## Metatheorem PI

**Proof by Induction**. _If for some set $$T$$, the following are true:_
1. _$${{I}} \subseteq T$$_
2. _$$T$$ is closed under every rule in $${{R}}$$_

_Then, $${{clIR}} \subseteq T$$._

This statement barely needs a proof &mdash; it is just a restatement of the fact that $${{clIR}}$$ is the smallest set satisfying the bullet points above.

This metatheorem is often rephrased as follows: to prove that a property $$P(x)$$ holds for all $$x$$ in $${{clIR}}$$,
* first prove that every member of $$\mathscr{I}$$ has the property
* and then show that the property propagates with every rule $$R$$ in $$\mathscr{R}$$ i.e. show that if $${{seqf("P","x")}}$$ are true for objects $${{seq("x")}}$$ and if $$R({{seq("x")}},y)$$ holds, then $$y$$ also has the property $$P$$ (that is, $$P(y)$$ holds).

To see that the above is a valid rephrasing of the metatheorem, let $$T$$ be $$\{x:P(x)\}$$, the set of all $$x$$ satisfying $$P(x)$$. Then, checking the two bullet points above amounts to checking 1 and 2 for $$T$$ in the metatheorem. As side note, technically, one should be careful when writing set expressions like $$\{x:P(x)\}$$ for arbitrary $$P$$. One can easily fall prey to [Russell's Paradox](https://en.wikipedia.org/wiki/Russell's_paradox). For now, within the informal metatheory, it is simpler to ignore this subtlety. One can show, later on, that with some extra care, one can avoid this issue (though one ends up with clunkier notation as a result).

One final note: one often uses a stronger form of induction to prove properties about $$\mathbb{N}$$. The first step of this form of induction proceeds as expected: one shows that the property in question holds for $$0$$. However, for the second step, one uses a stronger inductive hypothesis &mdash; that the property holds for _all_ numbers less than $$n+1$$ (instead of just for $$n$$ alone) &mdash; only then does one proceed to show that the property holds for $$n+1$$ to complete the induction.


## Lemma IPE

**Inductive Proof Example**. I now give a simple example of how an inductive proof proceeds.

_For every $$x\in{{clIR}}$$, the following property is true:_

_if $$x\notin{{I}}$$, then there exists an $$(n+1)$$-ary relation $$R\in{{R}}$$ and $${{seq('a')}}\in{{clIR}}$$ such that $$R({{seq('a')}},x)$$ holds._

**Proof**: Every member $$x$$ of $${{I}}$$ trivially satisfies the property as, in their cases, the property's very hypothesis ($$x\notin{{I}}$$) is false.

Now suppose, for the inductive hypothesis, that the property holds for $${{seq('x')}}\in{{clIR}}$$ and that $$R({{seq('x')}},x)$$ holds for some $$(n+1)$$-ary $$R\in{{R}}$$. One now needs to show that the property holds for $$x$$ also. This is almost immediate from the inductive hypothesis; only the requirement that all the $$x_i$$ be in $${{clIR}}$$ is missing.

To that end, consider any one of the $$x_i$$'s. If it is in $${{I}}$$, then one is done. Otherwise, since it satisfies the property, there must be some $${{seq('a','r')}}\in{{clIR}}$$ and $$R_i\in{{R}}$$ such that $$R_i({{seq('a','r')}},x_i)$$ holds. But then, since $${{clIR}}$$ is obviously closed under every rule in $${{R}}$$, $$x_i\in{{clIR}}$$ as desired.