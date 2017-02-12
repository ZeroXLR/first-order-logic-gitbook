Before defining the set of formulas, one must define one of its key constituents &mdash; the set of **terms**. Doing so requires an inductive definition as follows:

---


## Definition

$$\mathbf{Terms}$$ is the _smallest subset_ of $$\mathbf{AB}^\star$$ satisfying the following:
* Every **variable** symbol and every **constant** symbol are in $$\mathbf{Terms}$$.
* If $$^nf_i$$ is a *function* symbol (of arity $$n$$) and $$t_1,...,t_n$$ are any $$n$$ strings already in $$\mathbf{Terms}$$, then the string $$^nf_i(t_1,...,t_n)$$ is in $$\mathbf{Terms}$$.