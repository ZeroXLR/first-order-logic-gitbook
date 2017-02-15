# Manifesto
---

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