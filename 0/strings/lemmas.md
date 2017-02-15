I now prove some basic properties of strings and their associated concepts. Since the proofs are easy and require simple expansions of definitions, I will sloppily leave out parts of the proofs which the readers can fill in themselves.

---


## Metatheorem SC:

**String Cancellation**. _If $$\sigma, \sigma', \sigma'' \in \mathbf{AB}^\star$$ are such that $$\sigma\sigma' \equiv \sigma\sigma''$$, then $$\sigma' \equiv \sigma''$$._

**Proof**:
1. If the hypothesis is true, then, by [Definition StrCon](concepts.md#definition-strcon), $$|\sigma\sigma'| \equiv |\sigma\sigma''|$$ i.e. $$|\sigma| + |\sigma'| \equiv |\sigma| + |\sigma''|$$. So, $$|\sigma'| \equiv |\sigma''|$$.

2. Also, by [Definition StrEq](concepts.md#definition-streq), $$(\sigma\sigma')_i \equiv (\sigma\sigma'')_i$$ for all $$i$$ among $$1,...,|\sigma\sigma'|$$ (or $$1,...,|\sigma\sigma''|$$ because of 1).

3. At the same time, again by [Definition StrCon](concepts.md#definition-strcon), $$(\sigma\sigma')_{i+|\sigma'|} \equiv \sigma_i'$$ for $$i$$ among $$1,...,|\sigma'|$$. Similarly, $$(\sigma\sigma'')_{i+|\sigma''|} \equiv \sigma_i''$$ for $$i$$ among $$1,...,|\sigma''|$$.

Putting the results in 1, 2 and 3 together, one gets that
$$
\sigma_i' \equiv (\sigma\sigma')_{i+|\sigma'|} \equiv (\sigma\sigma'')_{i+|\sigma''|} \equiv \sigma_i''
$$ for $$i$$ among $$1,...,|\sigma'|$$ (or $$1,...,|\sigma''|$$).

You may notice that in the proof of this lemma, $$\sigma$$ was only used to make sure that the beginning parts of the strings $$\sigma\sigma'$$ and $$\sigma\sigma''$$ had the same length. So, in fact, a more general statement is true:

_If $$\sigma, \sigma', \sigma'', \sigma''' \in \mathbf{AB}^\star$$ are such that $$\sigma\sigma' \equiv \sigma''\sigma'''$$ and $$|\sigma| \equiv |\sigma''|$$, then $$\sigma \equiv \sigma''$$ and  $$\sigma' \equiv \sigma'''$$._

One final note: the two lemmas above cancel from the front i.e. they are prefix-cancellers. There is no reason why one couldn't equally cancel from the back and, in fact, proving the analogous suffix-versions of the lemmas is no harder.


## Metatheorem ASC:

**Associativity of String Concatenation**. _If $$\sigma, \sigma', \sigma''$$ are strings, then $$(\sigma\sigma')\sigma'' \equiv \sigma(\sigma'\sigma'')$$._

**Proof Sketch**: Firstly, [Definition StrCon](concepts.md#definition-strcon) yields that
$$
\begin{aligned}
|(\sigma\sigma')\sigma''| &\equiv |\sigma\sigma'| + |\sigma''| \\ &\equiv (|\sigma| + |\sigma'|) + |\sigma''| \\ &\equiv |\sigma| + (|\sigma'| + |\sigma''|) \\ &\equiv |\sigma| + |\sigma'\sigma''| \equiv |\sigma(\sigma'\sigma'')|
\end{aligned}
$$

Next, by the same definition, for $$i$$ among $$1,...,|\sigma\sigma'|$$, $$((\sigma\sigma')\sigma'')_i \equiv (\sigma\sigma')_i$$. In particular, for $$i$$ among $$1,...,|\sigma|$$, $$(\sigma\sigma')_i \equiv \sigma_i$$ so that $$((\sigma\sigma')\sigma'')_i \equiv \sigma_i$$ in that range. On the other end, one gets directly that in the range $$1,...,|\sigma|$$, $$(\sigma(\sigma'\sigma''))_i \equiv \sigma_i$$.

Putting the two results together, one gets that within
$$1,...,|\sigma|$$,
$$
((\sigma\sigma')\sigma'')_i \equiv \sigma_i \equiv (\sigma(\sigma'\sigma''))_i
$$

I will not show the remaining parts of the proof but the gist should be clear: one needs to consider, by expanding definitions, what values $$((\sigma\sigma')\sigma'')_i$$ and $$(\sigma(\sigma'\sigma''))_i$$ take in different ranges and equate them using those values within each range; eventually, one will have equated them over the entire range $$1,...,|(\sigma\sigma')\sigma''|$$ (or $$1,...,|\sigma(\sigma'\sigma'')|$$).

Because of the associativity of string concatenation, one can use the single notation &mdash; $$\sigma\sigma'\sigma''$$ &mdash; to refer to both $$(\sigma\sigma')\sigma''$$ and $$\sigma(\sigma'\sigma'')$$.


## Metatheorem LL:

**Levi's Lemma**. _Given strings $$\sigma_\text{left}, \sigma_\text{right}, \sigma_\text{left}', \sigma_\text{right}'$$, if $$\sigma_\text{left}\sigma_\text{right} \equiv \sigma_\text{left}'\sigma_\text{right}'$$, then there exists a string $$\sigma_\text{mid}$$ such that:_
1. _either $$\sigma_\text{left}\sigma_\text{mid} \equiv \sigma_\text{left}'$$ and $$\sigma_\text{right} \equiv \sigma_\text{mid}\sigma_\text{right}'$$_
2. _or $$\sigma_\text{left}'\sigma_\text{mid} \equiv \sigma_\text{left}$$ and $$\sigma_\text{right}' \equiv \sigma_\text{mid}\sigma_\text{right}$$_
3. _or $$\sigma_\text{left} \equiv \sigma_\text{left}'$$ and $$\sigma_\text{right} \equiv \sigma_\text{right}'$$_

**Proof Sketch**:
1. If $$|\sigma_\text{left}| < |\sigma_\text{left}'|$$, define $$\sigma_\text{mid} \equiv (\sigma_\text{left}')_{|\sigma_\text{left}|+1}...(\sigma_\text{left}')_{|\sigma_\text{left}'|}$$.
2. Else if $$|\sigma_\text{left}'| < |\sigma_\text{left}|$$, define $$\sigma_\text{mid} \equiv (\sigma_\text{left})_{|\sigma_\text{left}'|+1}...(\sigma_\text{left})_{|\sigma_\text{left}|}$$.
3. Otherwise, $$|\sigma_\text{left}'| \equiv |\sigma_\text{left}|$$ and, in this case, Levi's Lemma is the same as the generalized string cancellation mentioned earlier.

In each case, showing that the particular definition of $$\sigma_\text{mid}$$ works is a straightforward exercise in expanding out relevant definitions.

Also, note that the definitions of $$\sigma_\text{mid}$$ in cases 1 and 2 are well-defined because the condition, at the start of each case, guarantees that the starting subscript is never more than the ending subscript.