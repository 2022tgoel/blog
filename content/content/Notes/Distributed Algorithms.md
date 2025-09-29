
Really neat idea:

Lemma: You can construct $k\Delta^3$ subsets $s_1, s_2 .. s_{\Delta^2 - 1}$ of the range $\{1 .. \Delta^2\}$ such that the $s_i \setminus \cup_{j \in A} s_j \neq \emptyset$ for any $i$ and $A$ with $|A| \leq \Delta$ 

Consider all of the polynomials $q(x) = ax^2 + bx + c$ on the field of mod $\Delta$. There are $\Delta^3$ such polynomials, since each of the coefficients can take up to $\Delta$ values. 

Additionally, you can also think of the polynomial in terms of the $\Delta^2$ points on the plane that it occupies: $(1, q(1)), (2, q(2)) .. (\Delta, q(\Delta - 1))$. Now the key observation here is that two distinct polynomials can only intersect in up to $2$ points. So you are only setminusing up to $2 \Delta$ elements. This is actually greater that the size of the set, but if you scale everything up by a factor of $3$ then it works. 