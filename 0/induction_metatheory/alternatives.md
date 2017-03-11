{% macro seq(x,n="n") %} {{ x }}_1,...,{{ x }}_{{n}} {% endmacro %}
{% macro seqf(f, x) %} {{ f }}({{ x }}_1),...,{{ f }}({{ x }}_n) {% endmacro %}
{% set I = "\\mathscr{I}" %}
{% set R = "\\mathscr{R}" %}
{% set clIR = "\\text{cl}(\\mathscr{I},\\mathscr{R})" %}
{% set IR = "\\mathscr{I},\\mathscr{R}" %}

> Here, I discuss some alternative ways of looking at induction. Depending on the context, these ways may be easier to work with than the basic way given earlier.


## Definition DerPar

**Derivations and Parses**. An $${{IR}}$$-derivation is a finite sequence of objects $${{seq("d")}}$$ where $$n$$ is a non-zero natural such that each $$d_i$$ is:
* either in $${{I}}$$
* or (inclusively) for some $$(r+1)$$-ary $$R$$ in $${{R}}$$, $$R(d_{j_1},...,d_{j_r}, d_i)$$ holds where $${{seq("j","r")}} < i$$.

One says that $$d_i$$ is derivable in $$i$$ steps. Note that, in the second alternative above, $$r$$ is a _non-zero_ natural; so, it is at least $$1$$.


{% set derIR = "\\text{der}(\\mathscr{I},\\mathscr{R})" %}

## Metatheorem ClDer

Let $${{derIR}}$$ be the set
$$
\{d : d\text{ is }\mathscr{I},\mathscr{R}\text{-derivable in some number of steps }n\}
$$ Then, $${{clIR}}\equiv{{derIR}}$$.

**Proof**: As per (informal) set theory, to show that two sets are equal, one shows that each is a subset of the other.

$$(\subseteq)$$ To show this direction of the subset relationship, do induction on $${{clIR}}$$:
1. $${{I}}\subseteq{{derIR}}$$, as for each $$d\in{{I}}$$, the $$1$$-step sequence &mdash; $$d$$ &mdash; is a derivation of itself.
2. Let $$R\in{{R}}$$ be an $$(r+1)$$-ary relation and suppose $$R({{seq('c','r')}},d)$$ holds. Suppose also, as our inductive hypothesis, that each $$c_i$$ is in $${{derIR}}$$ i.e. each has some $$n_i$$-step derivation
$$
{{seq('d^i','{n_i}')}} \quad\text{where }d^i_{n_i} \equiv c_i
$$
Concatenate all such derivations and append $$d$$ to the end
$$
{{seq('d^1','{n_1}')}},...,{{seq('d^i','{n_i}')}},...,{{seq('d^r','{n_r}')}},d
$$ This is still a derivation. For let $$o$$ be any object occurring in this sequence. If $$o$$ is not the final object $$d$$, then it must fall within one of the sequence's constituent derivations like so: $$d^j_1,...,o,...,d^j_{n_j}$$. As $${{seq('d^j','{n_j}')}}$$ is in fact a derivation, any object in it (and, thus, $$o$$) satisfies the conditions of [Definition DerPar](#definition-derpar). Otherwise, if $$o$$ is $$d$$, then it automatically satisfies the second condition in _Definition DerPar_ because $$R({{seq('c','r')}},d)$$ holds and each $$c_i$$ (i.e. $$d^i_{n_i}$$) occurs earlier in the sequence than $$d$$ does. Thus, in both cases, $$o$$ satisfies _Definition DerPar_, meaning the sequence in question is indeed a derivation of $$d$$. The latter is therefore derivable in as many steps as this sequence is long i.e. $$n_1+...+n_r+1$$ steps. So, $$d\in{{derIR}}$$, meaning $${{derIR}}$$ is closed under the arbitrary rule $$R$$, as desired.

$$(\supseteq)$$ To show the other direction, do induction on the number of steps $$n$$ required to derive any element $$d$$ of $${{derIR}}$$:
1. $$n$$ cannot be $$0$$ as each derivation of $$d$$ must contain at least one object &mdash; itself &mdash; in it. If $$n$$ is $$1$$, the derivation sequence of $$d$$ must be just $$d_1$$ where $$d_1 \equiv d$$. Now, by [Definition DerPar](#definition-derpar), $$d_1$$ either must be in $${{I}}$$ or there is an _at least_ $$2$$-ary relation $$R$$ such that $$R(d_{j_1},...,d_{j_r}, d_1)$$ holds where each $$j_i < 1$$. The second case is impossible since there are no $$d_{j_i}$$'s in the sequence $$d_1$$ such that $$j_i < 1$$. Hence, $$d\in{{I}}\subseteq{{clIR}}$$.
2. Now suppose for the inductive hypothesis (henceforth referred to as IH) that for all elements of $${{derIR}}$$ that can be derived within less than or equal to $$n$$ steps, it is the case that the element is in $${{clIR}}$$. Consider, now, some $$d$$ such that its derivation takes $$n+1$$ steps as such:
$$
{{seq('d')}},d_{n+1} \quad\text{where }d_{n+1} \equiv d
$$
If $$d$$ is in $${{I}}$$, one is done. Otherwise, there is a rule $$R$$ such that $$R(d_{j_1},...,d_{j_r}, d_{n+1})$$ holds, where each $$j_i < n+1$$ and each $$d_{j_i}$$ occurs in the derivation sequence above. Since each $$j_i < n+1$$, in fact, one has that $$j_i \leq n$$. Thus for each $$d_{j_i}$$, the sequence
$$
{{seq('d','{j_i}')}}
$$
is a derivation of it in less than or equal to $$n$$ steps. Hence, by the IH, each $$d_{j_i}$$ is in $${{clIR}}$$. But then, as $${{clIR}}$$ must be closed under every rule in $${{R}}$$, it must, in particular, be closed under $$R$$. Hence, $$d_{n+1} \equiv d \in {{clIR}}$$.