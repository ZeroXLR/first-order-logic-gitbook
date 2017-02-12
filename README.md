<div style="text-align:center">
	<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.
</div>

---


## Preamble

This is a compilation of notes that I accumulated while studying [_**Lectures in Logic and Set Theory. Volume I: Mathematical Logic**_](https://www.amazon.com/Lectures-Logic-Set-Theory-Mathematical/dp/0521753732). The core material of this GitBook is identical to that in the latter. However, there are additional proofs, more details in existing proofs and copious bug fixes.


## Preface

The formal study of logic, in the modern era, has humbler aims than what an ambitious logician might assume. It does not attempt, for instance, to found to all of Mathematics on a few, select group of axioms and rules. Why? Well, because:

1. It would be philosophically circular to do so. For, to construct and analyze formal logic, as this book does, one ends up needing a lot of informal math such as
	* **informal set theory**: ideas on forming unions, intersections, differences, power sets, products, etc; ideas on cardinality (for finite sets in the beginning and for countable and even uncountable sets later on)
	* **basic ideas about relations and functions**
	* **the natural numbers and associated ideas**: well-ordering property, induction, successor function, addition, subtraction, multiplication, division, divisibility, etc
	* **notions about finite strings of letters**
	* **inductive definitions and proofs**
2. One can show mathematically that any one particular system of logic cannot found all of mathematics **lest it be inconsistent**. This is the content of Gödel's Incompleteness Theorems. In short, such a system, if it is consistent,
	* either is not complicated enough to encode the natural numbers, in which case, the system does not provide a foundation for the naturals
	* or (in the case that it is complicated enough) contains a statement that is true but unprovable (i.e. unprovable in the system itself; it may be provable in a different system)

Instead, the study of formal logical systems is analogous to the study of any other mathematical system: it strives to discover properties of the system that cannot be surmised without an in-depth look.

The informal mathematical results, required to do the study itself, are simply taken for granted. One cannot prove these without circular reasoning. They form, what is called the **external theory** or the **metatheory**. On the other hand, the system being constructed and studied is called the **internal theory**.

This distinction is crucial because when I say statements like, "one has proved the well-ordering property of the naturals", what I really mean is, "the formal theory one is studying can derive the well-ordering property of the naturals using its own laws and axioms". Of course, there is no point in proving the aforementioned result in the metatheory as it already takes the result for granted to begin with.