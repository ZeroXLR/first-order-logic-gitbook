<div style="text-align:center">
	<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
</div>


## Preamble

This is a compilation of notes that I accumulated while studying [_**Lectures in Logic and Set Theory. Volume I: Mathematical Logic**_](https://www.amazon.com/Lectures-Logic-Set-Theory-Mathematical/dp/0521753732). The core material of this GitBook is the same as that in the latter. However, there are additional proofs, more details in existing proofs and bug fixes.


## Preface

The formal study of logic has humbler aims than what a foundationalist might assume. It does not attempt, for instance, to give a foundation to all of Mathematics. Why? Well, because:

1. It would be philosophically circular to do so. For, to construct and analyze formal logic, as this book does, one ends up needing informal math such as
	* **informal set theory**: ideas on forming unions, intersections, differences, power sets, products, etc; ideas on cardinality (for finite sets in the beginning and for countable and even uncountable sets later on)
	* **basic ideas about relations and functions**
	* **properties of natural numbers** $$\{0, 1, 2, 3, ...\}$$: well-ordering property, inductive properties, etc.
	* **notions about finite strings of letters**
2. One can show mathematically that it any one particular system of logic cannot found all of mathematics **lest it be inconsistent**. This is the content of Gödel's Incompleteness Theorems. In short, such a system
	* either is not complicated enough to encode the natural numbers, in which case, the system does not provide a foundation for the naturals
	* or (in the case that it is complicated enough) contains a statement that is true but unprovable (that is, unprovable in the system itself; it may be provable in a different system, of course)

Instead, the study of formal logical systems is analogous to the study of any other mathematical objects: it strives to discover properties of the system that cannot be surmised without an in-depth look.

The informal mathematical results, required to do the study itself, are simply taken for granted. One cannot prove these without circular reasoning. They form, what we call the **external theory** or the **metatheory**. On the other hand, the system being constructed and studied is called the **internal theory**.

This distinction is crucial because when I say statements like, "we have proved the well-ordering property of the naturals", what I really mean is, "the formal theory we are studying can derive the well-ordering property of the naturals inside its own self". Of course, there is no point in proving the aforementioned result in the metatheory as it already takes that for granted.