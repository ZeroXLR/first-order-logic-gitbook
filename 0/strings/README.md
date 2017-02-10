# Definition
---

The first construction, using the alphabet $$\mathbf{AB}$$, is quite straightforward &mdash; simply glue together arbitrary numbers of arbitrary alphabet symbols and throw the glued objects into a set.

To be more precise, one needs a few short definitions:

* A **finite sequence** of length $$n$$, a natural number, is formed by literally writing down $$n$$ symbols from $$\mathbf{AB}$$ one after the other. One denotes this as $$\sigma_1...\sigma_n$$ where each $$\sigma_i \in \mathbf{AB}$$.
* More technically, one can define a finite sequence of length $$n$$ to be a function $$\sigma : \{1, ... , n\} \to \mathbf{AB}$$. In the case where $$n \equiv 0$$, one has the unique empty sequence $$\epsilon : \emptyset \to \mathbf{AB}$$, which is also called the **empty string of length** $$0$$.

Now, define the set of **strings over** $$\mathbf{AB}$$, denoted as $$\mathbf{AB}^\star$$, to be the set of all finite sequences over $$\mathbf{AB}$$. Examples of strings that are sensible are $$=(v_0,v_1)$$ and $$(\neg =(v_{101},v_{23}))$$. Examples of strings that are just random garbage are $$(()\neg\exists=$$ and $$v_{291}\neg\neg\neg$$.