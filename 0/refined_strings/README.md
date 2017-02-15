## Manifesto

Natural, written languages obviously do not permit just any string of letters to be a sensible word. They are more discerning in that regard. Similarly, first order logic is also quite choosy in identifying the "official" and "unofficial" strings of its syntax.

Unlike natural languages, however, which identify their "official" words in complicated and almost unsystematic fashions, first order logic takes a relatively simple but systematic approach to define its set of acceptable "words" &mdash; the method of inductive definition.

In the next two chapters, I will progressively use this method to construct the "words" of first order logic &mdash; **formulas**. Of course, that this method works and produces a valid set of strings must be assumed outright in the metatheory.


&nbsp;
> Before defining the set of formulas, one must first define one of its key constituents &mdash; the set of **terms**. Doing so requires an inductive definition as follows:


## Definition Terms:

**Terms**. $$\mathbf{Terms}$$ is the _smallest subset_ of $$\mathbf{AB}^\star$$ satisfying the following:
1. Every variable symbol and every constant symbol are in $$\mathbf{Terms}$$.
2. If $$^nf_i$$ is a function symbol (of arity $$n$$) and $$t_1,...,t_n$$ are any $$n$$ strings already in $$\mathbf{Terms}$$, then the string $$^nf_i(t_1,...,t_n)$$ is in $$\mathbf{Terms}$$.


## Notes

* Firstly, notice the stipulation that $$\mathbf{Terms}$$ be the _smallest set_ satisfying the conditions above. This ensures that terms are created solely by applying conditions 1 and 2 above (repeatedly if needed). Thus, for example, $$\mathbf{Terms}$$ cannot contain strings like $$\neg\exists$$ and $$\neg\neg\neg$$ which cannot be constructed by applying 1 and 2. For, if it did, then the smaller set $$\mathbf{Terms}\setminus\{\neg(\exists,v_3\neg\}$$ would satisfy 1 and 2, so that $$\mathbf{Terms}$$ would no longer be the smallest set satisfying them.

* Secondly, recall that particular first order theories might have no constants and/or no functions. Thus, the part of 1 about constants and the whole of 2 about functions are both provisional. They are only to be applied if the theory in question actually defines its own constants and functions. After all, $$^nf_i(t_1,...,t_n)$$ is not really a concrete string, to begin with, since the symbol $$^nf_i$$ is merely a stand-in.

* Finally, I show how this inductive definition works through an example. As always, I will use the case of the first order theory of natural numbers. As mentioned before, $$0$$ is a constant and $$S$$ is an unary function, in this theory. Thus, $$0$$ is an element of $$\mathbf{Terms}$$ by condition 1. Next, by condition 2, $$S(0)$$ is an element of the same. Then again by the same condition, so is $$S(S(0))$$, as is $$S(S(S(0))$$, etc.


&nbsp;
> I will now define the set of formulas by induction. As large formulas can get a bit unwieldy to write down, I also define some metatheoretical conventions that helps to alleviate some of this unwieldiness.


## Definition AF:

**Atomic Formulas**. $$\mathbf{AF}$$ is the smallest subset of $$\mathbf{AB}^\star$$ such that
1. For every pair of terms $$t,t'$$, the string $$=(t,t')$$ is in $$\mathbf{AF}$$. $$=(t,t')$$ is colloquially written as $$(t=t')$$ or even as $$t=t'$$.
2. For any $$n$$-ary predicate symbol $$^nP_i$$ and any $$n$$ terms $$t_1,...,t_n$$, the string $$^nP_i(t_1,...,t_n)$$ is in $$\mathbf{AF}$$.


## Definition WFF:

**Well-Formed Formulas**. $$\mathbf{WFF}$$ is the smallest subset of $$\mathbf{AB}^\star$$ such that
1. $$\mathbf{AF} \subseteq \mathbf{WFF}$$
2. If the strings $$\mathscr{A},\mathscr{B}$$ are already in $$\mathbf{WFF}$$, then the strings $$(\neg\mathscr{A})$$ and $$(\mathscr{A}|\mathscr{B})$$ are in there too.
3. If the string $$\mathscr{A}$$ is included and $$x$$ is any variable, then the string $$((\exists x)\mathscr{A})$$ is also included. In this case, one says that $$\mathscr{A}$$ is the **scope** of $$(\exists x)$$.


## Definition CA:

**Convenient Abbreviations**. For the sake of convenience in writing down large formulas and reasoning about them, one defines (in the metatheory) some shorthand notations and conventions:

* $$((\forall x)\mathscr{A})$$ abbreviates $$(\neg((\exists x)(\neg\mathscr{A})))$$.
* $$(\mathscr{A} \& \mathscr{B})$$ abbreviates $$(\neg((\neg\mathscr{A})|(\neg\mathscr{B}))$$.
* $$(\mathscr{A}\to\mathscr{B})$$ abbreviates $$((\neg\mathscr{A})|\mathscr{B})$$.
* $$(\mathscr{A}\leftrightarrow\mathscr{B})$$ abbreviates $$((\mathscr{A}\to\mathscr{B})\&(\mathscr{B}\to\mathscr{A}))$$.
* To minimize the use of brackets in the metatheory, one adopts certain priorities in parsing connectives: $$\forall,\exists,\neg$$ have the highest parse-priority; then, one has the following list of connectives in decreasing order of priority:
	* $$\&$$
	* $$|$$
	* $$\to$$
	* $$\leftrightarrow$$
* Also, within a formula that has a sequence of the same connective, one agrees to eliminate outermost brackets using the convention that similar connectives associate to the right. So for example, $$\mathscr{A}\to\mathscr{B}\to\mathscr{C}$$ is just sloppy notation for the formula $$(\mathscr{A}\to(\mathscr{B}\to\mathscr{C}))$$.