## Definition:

**Closure**. A set $$S$$ is said to **closed** under an $$(n+1)$$-ary rule $$R$$ iff whenever $$a_1,...,a_n$$ are all in $$S$$, then every $$a_{n+1}$$ satisfying $$R(a_1,...,a_n,a_{n+1})$$ is in $$S$$.


## Definition IDS:

**Inductively Defined Set**. A set $$S$$ is defined by induction from a set of initial objects $$\mathscr{I}$$ and a set of rules $$\mathscr{R}$$ iff it is the smallest set such that:
1. $$\mathscr{I} \subseteq S$$
2. $$S$$ is closed under every rule in $$\mathscr{R}$$

One takes it for granted that a set $$S$$, defined as above, always exists in the metatheory. $$S$$ is called the **closure of $$\mathscr{I}$$ under $$\mathscr{R}$$**. As smallest sets are unique, one writes $$S$$ uniquely as $$\text{cl}(\mathscr{I},\mathscr{R})$$.


## Metatheorem PI:

**Proof by Induction**. _If for some set $$T$$, the following are true:_
* _$$\mathscr{I} \subseteq T$$_
* _$$T$$ is closed under every rule in $$\mathscr{R}$$_

_Then, $$\text{cl}(\mathscr{I},\mathscr{R}) \subseteq T$$._

This statement barely needs a proof and it is just a restatement of the fact that $$\text{cl}(\mathscr{I},\mathscr{R})$$ is the smallest set satisfying the bullet points above.

This metatheorem is often rephrased as follows: to prove that a property $$P(x)$$ holds for all $$x$$ in $$\text{cl}(\mathscr{I},\mathscr{R})$$,
* first prove that every member of $$\mathscr{I}$$ has the property
* and then show that the property propagates with every rule $$R$$ in $$\mathscr{R}$$ i.e. show that if $$P(x_1),...,P(x_n)$$ are true for objects $$x_1,...,x_n$$ and if $$R(x_1,...,x_n,y)$$ holds, then $$y$$ also has the property $$P$$ (that is, $$P(y)$$ holds).

To see that the above is a valid rephrasing of the metatheorem, let $$T$$ be the set of $$x$$ satisfying $$P(x)$$ ($$\{x:P(x)\}$$). Then, checking the two bullet points above amounts to checking 1 and 2 for $$T$$ in the metatheorem. Technically, one should be careful when writing set expressions like $$\{x:P(x)\}$$. One can easily fall prey to [Russell's Paradox](https://en.wikipedia.org/wiki/Russell's_paradox). For now, within the informal metatheory, I shall ignore such subtleties.