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