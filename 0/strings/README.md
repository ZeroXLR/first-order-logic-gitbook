## Definition:

**Strings**. The first construction, using the alphabet $$\mathbf{AB}$$, is quite straightforward &mdash; simply glue together arbitrary numbers of arbitrary alphabet symbols and throw the glued objects into a set.

To be more precise, one needs a few short definitions:

* A **finite sequence** of length $$n$$, a natural number, is formed by literally writing down $$n$$ symbols from $$\mathbf{AB}$$ one after the other. One denotes this as $$\sigma_1...\sigma_n$$ where each $$\sigma_i \in \mathbf{AB}$$.
* More technically, one can define a finite sequence of length $$n$$ to be a function $$\sigma : \{1, ... , n\} \to \mathbf{AB}$$. In the case where $$n \equiv 0$$, one has the unique empty sequence $$\epsilon : \emptyset \to \mathbf{AB}$$, which is also called the **empty string of length** $$0$$.

Now, define the set of **strings over** $$\mathbf{AB}$$, denoted as $$\mathbf{AB}^\star$$, to be the set of all finite sequences over $$\mathbf{AB}$$. Examples of strings that are sensible are $$=(v_0,v_1)$$ and $$(\neg =(v_{101},v_{23}))$$. Examples of strings that are just random garbage are $$(()\neg\exists=$$ and $$v_{291}\neg\neg\neg$$.


## Definition StrEq:

**Equality**. The equality of two strings $$\sigma, \sigma'$$ is based on the equalities of their constituent symbols. Writing the constituents of $$\sigma$$ and $$\sigma'$$ as $$\sigma_i$$ and $$\sigma_i'$$ respectively and denoting the lengths of those strings as $$|\sigma|$$ and $$|\sigma'|$$ respectively, one defines string equality thus: $$\sigma_1...\sigma_{|\sigma|} \equiv \sigma_1'...\sigma_{|\sigma'|}'$$ iff $$|\sigma| \equiv |\sigma'|$$ and each $$\sigma_i \equiv \sigma_i'$$ as symbols.


## Definition StrCon:

**Concatenation**. The concatenation of two strings $$\sigma, \sigma'$$ is a string made by writing down every symbol of $$\sigma$$ followed by writing down every symbol of $$\sigma'$$.

As usual, one can get a more technical. The concatenation of strings $$\sigma, \sigma'$$ is the string, denoted by $$\sigma\sigma'$$, of length $$|\sigma|+|\sigma'|$$ such that:

* $$(\sigma\sigma')_i \equiv \sigma_i$$ for $$i$$ among the numbers in the range $$1, ... , |\sigma|$$
* $$(\sigma\sigma')_{i+|\sigma|} \equiv \sigma_i'$$ for $$i$$ among the numbers in the range $$1 , ... , |\sigma'|$$

Visually, $$\sigma\sigma' \equiv \sigma_1...\sigma_{|\sigma|}\sigma_1'...\sigma_{|\sigma'|}'$$.

Now, from this definition of concatenation, it is evident that the empty string behaves in the following way:
$$
\sigma\epsilon \equiv \epsilon\sigma \equiv \sigma
$$
For this behavior, the empty string is said to be the **identity of concatenation** in $$\mathbf{AB}^\star$$.


## Definition SubStr:

**Substrings**. Given two strings $$\sigma, \sigma'$$, one says that $$\sigma$$ is **substring** of $$\sigma'$$ iff there are strings $$\sigma_\text{left}, \sigma_\text{right}$$ such that $$
\sigma_\text{left}\sigma\sigma_\text{right} \equiv \sigma'
$$
If at least one of $$\sigma_\text{left}, \sigma_\text{right}$$ is not the empty string, then one says that $$\sigma$$ is a **proper substring** of $$\sigma'$$. If $$\sigma_\text{left} \equiv \epsilon$$, one calls $$\sigma$$ a **prefix** of $$\sigma'$$. Analogously, if $$\sigma_\text{right} \equiv \epsilon$$, one calls the former a **suffix** of the latter.

Now, I highlight an important property of alphabet symbols: no _nonempty_ string is a _proper substring_ of any symbol $$\varsigma$$ in $$\mathbf{AB}$$ (here, $$\varsigma$$ must be thought of as the unique string $$\sigma$$ of length $$1$$ where $$\sigma_1 \equiv \varsigma$$). This is the **atomicity property** of alphabet symbols. Like the distinctness property, it will be used in proving unique readability theorems. One can easily prove it via contradiction (unlike the distinctness property, which is assumed outright, atomicity can be proven with the definitions given thus far).


## Definition StrSOC:

**Symbol Occurrence Count**. An alphabet symbol $$\varsigma$$ is said to **occur** in a string $$\sigma$$ iff $$\varsigma$$, considered as a string, is a substring of $$\sigma$$.

One can go further and actually count the number of times a particular symbol occurs in a string. Firstly, for any two symbols $$\varsigma, \varsigma'$$, define
$$
\text{Count}_\varsigma(\varsigma) \equiv \begin{cases} 1 &\text{if } \varsigma \equiv \varsigma' \\ 0 &\text{otherwise} \end{cases}
$$
Now, extend $$\text{Count}$$ to take in any string $$\sigma$$ as input:
$$
\text{Count}_\varsigma(\sigma) \equiv \text{Count}_\varsigma(\sigma_1) + ... + \text{Count}_\varsigma(\sigma_{|\sigma|})
$$
One should verify with some examples and mini-proofs that this occurrence counting function behaves as expected. For instance, try and show that for any substring $$\sigma'$$ of $$\sigma$$, $$\text{Count}_\varsigma(\sigma') \le \text{Count}_\varsigma(\sigma)$$.


&nbsp;
> I now prove some basic properties of strings and their associated concepts. Since the proofs are easy and require simple expansions of definitions, I will sloppily leave out parts of the proofs which the readers can fill in themselves.


## Metatheorem SC:

**String Cancellation**. _If $$\sigma, \sigma', \sigma'' \in \mathbf{AB}^\star$$ are such that $$\sigma\sigma' \equiv \sigma\sigma''$$, then $$\sigma' \equiv \sigma''$$._

**Proof**:
1. If the hypothesis is true, then, by [Definition StrCon](#definition-strcon), $$|\sigma\sigma'| \equiv |\sigma\sigma''|$$ i.e. $$|\sigma| + |\sigma'| \equiv |\sigma| + |\sigma''|$$. So, $$|\sigma'| \equiv |\sigma''|$$.

2. Also, by [Definition StrEq](#definition-streq), $$(\sigma\sigma')_i \equiv (\sigma\sigma'')_i$$ for all $$i$$ among $$1,...,|\sigma\sigma'|$$ (or $$1,...,|\sigma\sigma''|$$ because of 1).

3. At the same time, again by [Definition StrCon](#definition-strcon), $$(\sigma\sigma')_{i+|\sigma'|} \equiv \sigma_i'$$ for $$i$$ among $$1,...,|\sigma'|$$. Similarly, $$(\sigma\sigma'')_{i+|\sigma''|} \equiv \sigma_i''$$ for $$i$$ among $$1,...,|\sigma''|$$.

Putting the results in 1, 2 and 3 together, one gets that
$$
\sigma_i' \equiv (\sigma\sigma')_{i+|\sigma'|} \equiv (\sigma\sigma'')_{i+|\sigma''|} \equiv \sigma_i''
$$ for $$i$$ among $$1,...,|\sigma'|$$ (or $$1,...,|\sigma''|$$).

You may notice that in the proof of this lemma, $$\sigma$$ was only used to make sure that the beginning parts of the strings $$\sigma\sigma'$$ and $$\sigma\sigma''$$ had the same length. So, in fact, a more general statement is true:

_If $$\sigma, \sigma', \sigma'', \sigma''' \in \mathbf{AB}^\star$$ are such that $$\sigma\sigma' \equiv \sigma''\sigma'''$$ and $$|\sigma| \equiv |\sigma''|$$, then $$\sigma \equiv \sigma''$$ and  $$\sigma' \equiv \sigma'''$$._

One final note: the two lemmas above cancel from the front i.e. they are prefix-cancellers. There is no reason why one couldn't equally cancel from the back and, in fact, proving the analogous suffix-versions of the lemmas is no harder.


## Metatheorem ASC:

**Associativity of String Concatenation**. _If $$\sigma, \sigma', \sigma''$$ are strings, then $$(\sigma\sigma')\sigma'' \equiv \sigma(\sigma'\sigma'')$$._

**Proof Sketch**: Firstly, [Definition StrCon](#definition-strcon) yields that
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