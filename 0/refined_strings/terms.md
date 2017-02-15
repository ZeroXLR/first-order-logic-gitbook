Before defining the set of formulas, one must first define one of its key constituents &mdash; the set of **terms**. Doing so requires an inductive definition as follows:

---


## Definition:

**Terms**. $$\mathbf{Terms}$$ is the _smallest subset_ of $$\mathbf{AB}^\star$$ satisfying the following:
1. Every variable symbol and every constant symbol are in $$\mathbf{Terms}$$.
2. If $$^nf_i$$ is a function symbol (of arity $$n$$) and $$t_1,...,t_n$$ are any $$n$$ strings already in $$\mathbf{Terms}$$, then the string $$^nf_i(t_1,...,t_n)$$ is in $$\mathbf{Terms}$$.


## Notes

* Firstly, notice the stipulation that $$\mathbf{Terms}$$ be the _smallest set_ satisfying the conditions above. This ensures that terms are created solely by applying conditions 1 and 2 above (repeatedly if needed). Thus, for example, $$\mathbf{Terms}$$ cannot contain strings like $$\neg\exists$$ and $$\neg\neg\neg$$ which cannot be constructed by applying 1 and 2. For, if it did, then the smaller set $$\mathbf{Terms}\setminus\{\neg(\exists,v_3\neg\}$$ would satisfy 1 and 2, so that $$\mathbf{Terms}$$ would no longer be the smallest set satisfying them.

* Secondly, recall that particular first order theories might have no constants and/or no functions. Thus, the part of 1 about constants and the whole of 2 about functions are both provisional. They are only to be applied if the theory in question actually defines its own constants and functions. After all, $$^nf_i(t_1,...,t_n)$$ is not really a concrete string, to begin with, since the symbol $$^nf_i$$ is merely a stand-in.

* Finally, I show how this inductive definition works through an example. As always, I will use the case of the first order theory of natural numbers. As mentioned before, $$0$$ is a constant and $$S$$ is an unary function, in this theory. Thus, $$0$$ is an element of $$\mathbf{Terms}$$ by condition 1. Next, by condition 2, $$S(0)$$ is an element of the same. Then again by the same condition, so is $$S(S(0))$$, as is $$S(S(S(0))$$, etc.