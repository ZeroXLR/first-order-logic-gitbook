## Manifesto

Since induction plays a crucial role in logic, it is worth taking a more precise look at it. Thus, induction is one of the salient parts of the metatheory that I promised to refine and explore further.

One builds a set recursively or inductively out of two ingredients &mdash; a set of initial objects, prototypically denoted by $$\mathscr{I}$$, and a set of rules, prototypically denoted by $$\mathscr{R}$$. A member of $$\mathscr{R}$$ is an $$(n+1)$$-ary relation $$R$$ where $$n$$ is a non-zero natural number. One can visualize this relation as a possibly infinite table:

| $$\textbf{in}_1\qquad ... \qquad\textbf{in}_n$$ | $$\textbf{out}$$ |
|:-----------------------------------------------:|:----------------:|
| $$a_1\qquad ... \qquad a_n$$                    | $$a_{n+1}$$      |
|             ...                                 |    ...           |
| $$b_1\qquad ... \qquad b_n$$                    | $$b_{n+1}$$      |
|             ...                                 |    ...           |

To express the fact that $$a_1,...,a_n,a_{n+1}$$ is a row in the table, one uses the notation $$R(a_1,...,a_n,a_{n+1})$$ and $$(a_1,...,a_n,a_{n+1}) \in R$$ interchangeably.

Occasionally, one also uses the notation $$R(a_1,...,a_n) \sim a_{n+1}$$ and, in that case, one says that $$R$$ yields an output of $$a_{n+1}$$ on input(s) $$a_1,...,a_n$$. However, one must be careful since $$R$$ is a relation and not a function. It may have multiple outputs for the same input.


## Definition Closure:

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

To see that the above is a valid rephrasing of the metatheorem, let $$T$$ be $$\{x:P(x)\}$$, the set of $$x$$ satisfying $$P(x)$$. Then, checking the two bullet points above amounts to checking 1 and 2 for $$T$$ in the metatheorem. Technically, one should be careful when writing set expressions like $$\{x:P(x)\}$$. One can easily fall prey to [Russell's Paradox](https://en.wikipedia.org/wiki/Russell's_paradox). For now, within the informal metatheory, I shall ignore such subtleties.