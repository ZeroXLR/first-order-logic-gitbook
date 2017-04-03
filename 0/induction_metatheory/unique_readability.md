{% macro seq(x,n="n") %} {{ x }}_1,...,{{ x }}_{{n}} {% endmacro %}
{% macro seqf(f, x) %} {{ f }}({{ x }}_1),...,{{ f }}({{ x }}_n) {% endmacro %}
{% set I = "\\mathscr{I}" %}
{% set R = "\\mathscr{R}" %}
{% set clIR = "\\text{cl}(\\mathscr{I},\\mathscr{R})" %}
{% set IR = "\\mathscr{I},\\mathscr{R}" %}


## Definition IPA

**Immediate Predecessors and Ambiguity**. Suppose $$x\in{{clIR}}$$ and it is the case that for some $$R\in{{R}}$$ and $${{seq('d','r')}}\in{{clIR}}$$, $$R({{seq('d','r')}},d)$$ holds. Then, $${{seq('d','r')}}$$ are called the **immediate R-predecessors** of $$d$$ or just i.p. for short if $$R$$ is understood.

A pair $${{IR}}$$ is called **ambiguous** iff there is some $$d\in{{clIR}}$$ that satisfies at least one of the following:
1. it has two distinct _lists_ (i.e. _ordered_ sets/sequences) of immediate $$R$$-predecessors for some $$R\in{{R}}$$
2. it has both immediate $$R$$-predecessors and immediate $$R'$$-predecessors where $$R$$ and $$R'$$ are not names for the same rule/table
3. it is a member of $${{I}}$$; yet it has immediate predecessors for some rule

If $${{IR}}$$ is not ambiguous, it is unsurprisingly called **unambiguous**.

**Example**. The pair $${{I}}\equiv\{00,0\}$$ and $${{R}}\equiv\{\text{glue}\}$$, where $$\text{glue}(x,y,z)$$ holds iff $$z \equiv xy$$ ($$xy$$ is just the concatenation of the strings/symbols $$x$$ and $$y$$), is ambiguous. For example, $$0000$$ has three i.p. lists: $$(00,00)$$, $$(0,000)$$ and $$(000,0)$$. Moreover, $$00\in{{I}}$$; yet, it has the i.p. list $$(0,0)$$.

Ambiguity is quite inconvenient when defining _functions_ (not relations) inductively on $${{clIR}}$$. For instance, consider the following inductive definition of a supposed "function" $$f$$ on our pair above:
* If $$x\in{{I}}$$, $$f(x)\equiv\mathbf{T}$$.
* If $$f(x)\equiv f(y)\equiv\mathbf{T}$$, then $$f(xy)\equiv\mathbf{F}$$; otherwise, $$f(xy)\equiv\mathbf{T}$$.

Ambiguity makes this definition troublesome. For instance, because $$0\in{{I}}$$, by definition $$f(0)\equiv\mathbf{T}$$. So, according to the previous sentence, $$f(00)\equiv\mathbf{F}$$. However, note that $$00\in{{I}}$$ also. So, in fact, $$f(00)\equiv\mathbf{T}$$ also. Thus, $$f$$ is not really a function as claimed, as it outputs two distinct things on the same input.


&nbsp;
> I now show that the [Terms](../refined_strings/README.md#definition-terms) and [Formulas](../refined_strings/README.md#definition-wff), defined earlier are, in fact, _unambiguous_. Later on, this will imply that one can define inductive functions on these inductive sets. But, first, one needs a series of lemmas to show all this: