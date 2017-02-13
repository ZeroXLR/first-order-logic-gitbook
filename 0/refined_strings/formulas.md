I will now define the set of formulas by induction. As large formulas can get a bit unwieldy to write down, I also define some metatheoretical conventions that helps to alleviate some of this unwieldiness.

---


## Definition (Atomic Formulas)

$$\mathbf{AF}$$ is the smallest subset of $$\mathbf{AB}^\star$$ such that
1. For every pair of terms $$t,t'$$, the string $$=(t,t')$$ is in $$\mathbf{AF}$$. $$=(t,t')$$ is colloquially written as $$(t=t')$$ or even as $$t=t'$$.
2. For any $$n$$-ary predicate symbol $$^nP_i$$ and any $$n$$ terms $$t_1,...,t_n$$, the string $$^nP_i(t_1,...,t_n)$$ is in $$\mathbf{AF}$$.


## Definition (Well-Formed Formulas)

$$\mathbf{WFF}$$ is the smallest subset of $$\mathbf{AB}^\star$$ such that
1. $$\mathbf{AF} \subseteq \mathbf{WFF}$$
2. If the strings $$\mathscr{A},\mathscr{B}$$ are already in $$\mathbf{WFF}$$, then the strings $$(\neg\mathscr{A})$$ and $$(\mathscr{A}|\mathscr{B})$$ are in there too.
3. If the string $$\mathscr{A}$$ is included and $$x$$ is any variable, then the string $$((\exists x)\mathscr{A})$$ is also included. In this case, one says that $$\mathscr{A}$$ is the **scope** of $$(\exists x)$$.


## Convenient Abbreviations

For the sake of convenience in writing down large formulas and reasoning about them, one defines (in the metatheory) some shorthand notations and conventions:

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