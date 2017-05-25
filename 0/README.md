## Manifesto

Using the metatheory mentioned [earlier](../README.md#preface), I will construct the syntax of first order logic in this chapter. Then, I will prove some metatheoretical properties of the syntax, while occasionally clarifying parts of the metatheory (namely, the salient, most frequently used parts).


&nbsp;
> Like natural, written languages, first order logic begins with an alphabet. Unlike natural, written languages, however, the alphabet of first order logic is not finite, as one sees below:


## Definition LS

**Logical Symbols**. The first group of symbols, comprising the alphabet, is the set of _logical symbols_; this set is common to all "flavors" of first order logic. It is, in turn, comprised of the following:

* **Variables**: $$\quad v_0 \quad v_1 \quad v_2 \quad v_3 \quad \ldots$$
	* In essence, I am setting aside a countably infinite number of symbols of the form $$v_i$$ for each natural number $$i$$.
	* It is important to note that the symbols $$0, 1, 2, \ldots$$ that appear in the list of variables _only serve to visually distinguish one variable from another_. Within the **internal theory** at least, they serve no other purpose. So, for example, the list &mdash; $$\quad v \quad v_| \quad v_{||} \quad v_{|||} \quad \ldots \quad$$ &mdash; could equally have been one's variables instead. However, within the **external theory** where knowledge about natural numbers is assumed, it is much easier to deal with numbers as indices than to deal with a bunch of vertical lines as indices.
	* In the metatheory, one often wants to _refer_ to a variable rather than to _write down_ an actual variable itself. Thus, one needs some **reference symbols** for this purpose: $$x, y, z, u, v, w$$. These can be used with subscripts or superscripts depending on the situation at hand.
* **Parentheses and the Separator**: $$\quad ( \quad ) \quad |$$
* **Boolean Connectives**: $$\quad \neg \quad \bigvee$$
* **The Existential Quantifier**: $$\quad \exists$$
* **The Equality Predicate**: $$\quad =$$

The last symbol may be a source of confusion because one needs an equality symbol in the metatheory too. Otherwise, how does one express the fact that two sets are equal in the metatheory? Of course, one can laboriously write down the English statement, "set A is equal to set B" each time, but, for convenience's sake, a shortcut symbol is needed. This is henceforth defined to be $$\equiv$$.


## Definition NLS

**Nonlogical Symbols**. The contents of the second group of symbols depend on the particular "flavor" of first order logic being studied. They always appear in at most three forms: **constants**, **function symbols** and **predicate symbols**:

* **Constants**: Since the particular make-up of this group depends on the particular theory being studied, one cannot obviously list the actual symbols comprising this set. Instead, one has to make do with a countable list of stand-in reference symbols &mdash; $$c_0 \quad c_1 \quad c_2 \quad \ldots$$.
	* While one cannot demonstrate actual symbols in the general case, one can at least demonstrate actual symbols in a particular case. Thus, for instance, $$0$$ is a constant symbol in the first order theory of natural numbers.

* **Function Symbols**: The stand-in symbols, in this case, have the following form: every pair of natural numbers $$n$$ and $$i$$ gives rise to one such symbol &mdash; $$^nf_i$$. Here, $$n$$ is a stand-in natural to indicate the number of inputs that this function symbol takes. In the metatheory, it is called the **arity** of the function symbol.
	* As a concrete example, $$S$$ is the successor function symbol in the first order theory of natural numbers. It has arity $$1$$. The notion of arity will become clearer when I define [terms](refined_strings/README.md#definition-terms) and [formulas](refined_strings/README.md#definition-wff).
* **Predicate Symbols**: Analogous to the situation above, every pair of natural numbers $$n$$ and $$i$$ gives rise to a (referential) predicate symbol &mdash; $$^nP_i$$.
	* Technically, the equality predicate, defined as a logical symbol, is a predicate symbol of arity $$2$$. Thus, a more accurate title for this section would be "Predicate Symbols without Equality".


## Remarks

There is an obvious but important metatheoretical property of each symbol defined above (actual or referential): each symbol is distinct from every other symbol. Thus, neither is any symbol _equal_ to any other (save itself) nor does any symbol _refer_ to any other. This **distinctness property** is used in proving _unique readability theorems_ later on.

Henceforth, the set of all symbols, defined above, is referred to as $$\mathbf{AB}$$. Of course, when one deals with specific "flavors" of first order logic, which may declare actual constants, functions and predicates, one must remember to replace the stand-in nonlogical symbols with those actual symbols.