# Chapter 2 · Linear Algebra

End-of-chapter exercises. Each has a definitions box, explanation, worked steps, and the answer.

---

## 2.1 · Custom operation $a \star b = ab + a + b$ on $\mathbb{R}\setminus\{-1\}$

!!! theory "Topics & Definitions"
    - **Group** — a set with an operation obeying 4 axioms: closure, associativity, identity, inverses.
    - **Abelian group** — a group whose operation is also commutative ($a\star b = b\star a$).
    - **Identity $e$** — the element with $a\star e = a$.
    - **Inverse** — the element that undoes $a$, returning $e$.

The key move is factoring: $a \star b = (a+1)(b+1) - 1$. So the operation behaves like ordinary multiplication shifted by $1$, which makes every axiom easy. It is closed (never gives $-1$), associative, has identity $0$, every element has an inverse, and it is commutative.

For part b, solve $3 \star x \star x = 4(x+1)^2 - 1 = 15$.

!!! answer "Answer"
    $(\mathbb{R}\setminus\{-1\},\ \star)$ is an **Abelian group**. Identity $e = 0$, inverse $a^{-1} = \dfrac{-a}{a+1}$.

    **2.1b:** $x = 1$ or $x = -3$.

---

## 2.2 · Integers mod $n$ under $\oplus$

!!! theory "Topics & Definitions"
    - **Congruence class $[a]$** — all integers with the same remainder as $a$ mod $n$.
    - **Modular addition** — $[a] \oplus [b] = [a+b]$, then reduce mod $n$.
    - **Prime condition** — $(\mathbb{Z}_n\setminus\{0\}, \otimes)$ is a group only when $n$ is prime.

$\mathbb{Z}_n = \{[0],[1],\dots,[n-1]\}$ with $[a]\oplus[b] = [a+b]$ reduced mod $n$. It is a group because ordinary integer addition already is, and the classes inherit that.

!!! answer "Answer"
    $(\mathbb{Z}_n, \oplus)$ is an **Abelian group**. Identity $[0]$, inverse of $[a]$ is $[n-a]$.

    $(\mathbb{Z}_n\setminus\{0\}, \otimes)$ is a group **iff $n$ is prime**.

---

## 2.3 · Upper-unitriangular $3\times 3$ matrices under multiplication

!!! theory "Topics & Definitions"
    - **Matrix group** — a set of matrices closed under multiplication satisfying the 4 axioms.
    - **Upper unitriangular** — $1$s on the diagonal, $0$s below, free entries above.
    - **Non-commutative** — $AB \neq BA$ in general, so a group can be non-Abelian.

$G$ is all matrices $\begin{bmatrix}1&x&z\\0&1&y\\0&0&1\end{bmatrix}$. Multiplying two keeps the shape (closed), multiplication is associative, the identity is in $G$, and inverses stay in $G$. But the $(1,3)$ entry of a product depends on order, so it is not Abelian.

!!! answer "Answer"
    $(G, \cdot)$ is a **group**, but **not Abelian**.

---

## 2.4 · Matrix products (check dimensions first!)

!!! theory "Topics & Definitions"
    - **Dimension rule** — $AB$ is defined only if $A$'s columns $=$ $B$'s rows: $(m\times n)(n\times p)\to(m\times p)$.
    - **Entry rule** — entry $(i,j)$ = row $i$ of $A$ dotted with column $j$ of $B$.
    - **Non-commutative** — compare b and c: same matrices swapped, different results.

Part **a** is a $3\times 2$ times a $3\times 3$: inner dimensions $2$ and $3$ do not match, so it is **undefined**.

!!! answer "Answer"
    **a)** undefined (dimension mismatch)

    **b)** $\begin{bmatrix}4&3&5\\10&9&11\\16&15&17\end{bmatrix}$
    &nbsp;&nbsp; **c)** $\begin{bmatrix}5&7&9\\11&13&15\\8&10&12\end{bmatrix}$

    **d)** $\begin{bmatrix}14&6\\-21&2\end{bmatrix}$
    &nbsp;&nbsp; **e)** $\begin{bmatrix}12&3&-3&-12\\-3&1&2&6\\6&5&1&0\\13&12&3&2\end{bmatrix}$

---

## 2.5 · Find all solutions of $A\mathbf{x} = \mathbf{b}$

!!! theory "Topics & Definitions"
    - **Gaussian elimination** — row operations to reach echelon form.
    - **Contradiction row** — $0 = \text{nonzero}$ means inconsistent, no solution.
    - **Free variable** — a column with no pivot, giving infinitely many solutions.

!!! answer "Answer"
    **2.5a:** no solution, $S = \varnothing$ (a contradiction row appears).

    **2.5b:** infinitely many solutions, two free parameters.

---

## 2.6 · Solving $A\mathbf{x} = \mathbf{b}$ with Gaussian elimination

!!! theory "Topics & Definitions"
    - **RREF** — pivots are $1$, alone in their column, stepping down-right.
    - **Pivot vs free column** — pivot columns give basic variables; no-pivot columns give free variables.
    - **General solution** — one particular solution plus the free-variable directions.

Reducing $[A\mid \mathbf{b}]$ to RREF puts pivots in columns $2, 4, 5$; columns $1, 3, 6$ are free.

!!! steps "RREF of $[A \mid \mathbf{b}]$"
    $$\left[\begin{array}{cccccc|c}
    0&1&0&0&0&1&1\\
    0&0&0&1&0&1&-2\\
    0&0&0&0&1&-1&1
    \end{array}\right]$$

    Pivots in columns $2, 4, 5 \Rightarrow x_2, x_4, x_5$ basic; $x_1, x_3, x_6$ free.

!!! answer "Answer"
    $$\mathbf{x} = \begin{pmatrix}0\\1\\0\\-2\\1\\0\end{pmatrix}
    + x_1\begin{pmatrix}1\\0\\0\\0\\0\\0\end{pmatrix}
    + x_3\begin{pmatrix}0\\0\\1\\0\\0\\0\end{pmatrix}
    + x_6\begin{pmatrix}0\\-1\\0\\-1\\1\\1\end{pmatrix},\quad x_1,x_3,x_6\in\mathbb{R}$$

---

## 2.7 · Solving $A\mathbf{x} = 12\mathbf{x}$

!!! theory "Topics & Definitions"
    - **Eigenvalue / eigenvector** — $A\mathbf{x} = \lambda\mathbf{x}$: a vector $A$ only scales, never rotates; $\lambda$ is the scale factor.
    - **Rearrangement** — $A\mathbf{x} = \lambda\mathbf{x} \Rightarrow (A - \lambda I)\mathbf{x} = 0$, a homogeneous system.
    - **Eigenspace** — all eigenvectors for a given $\lambda$ (a line/plane through the origin).
    - **Constraint** — an extra equation like $\sum x_i = 1$ picks one point on that line.

!!! steps "$(A - 12I)\mathbf{x} = 0$ elimination"
    $$\begin{bmatrix}-6&4&3\\6&-12&9\\0&8&-12\end{bmatrix}
    \longrightarrow
    \begin{bmatrix}-6&4&3\\0&-8&12\\0&0&0\end{bmatrix}$$

    Zero row $\Rightarrow x_3$ free. Then $x_2 = \tfrac32 x_3,\ x_1 = \tfrac32 x_3 \Rightarrow \mathbf{x} = t(3,3,2)$.
    The constraint $3t + 3t + 2t = 1$ gives $t = \tfrac18$.

!!! answer "Answer"
    $$\mathbf{x} = \left(\tfrac38,\ \tfrac38,\ \tfrac14\right)$$

---

## 2.8 · Inverses

!!! theory "Topics & Definitions"
    - **Inverse $A^{-1}$** — the matrix with $A\,A^{-1} = I$.
    - **Determinant** — a number measuring how much $A$ scales space.
    - **Invertible iff $\det \neq 0$** — $\det = 0$ means $A$ squashes a dimension, so no inverse.
    - **Gauss–Jordan** — reduce $[A\mid I]$ until the left is $I$; the right becomes $A^{-1}$.

**Part a.** $\det = 0$ (row 1 + row 3 = $2\times$ row 2), so no inverse.

!!! steps "$[A \mid I] \to [I \mid A^{-1}]$"
    $$\left[\begin{array}{cccc|cccc}
    1&0&1&0&1&0&0&0\\
    0&1&1&0&0&1&0&0\\
    1&1&0&1&0&0&1&0\\
    1&1&1&0&0&0&0&1
    \end{array}\right]
    \longrightarrow
    \left[\begin{array}{cccc|cccc}
    1&0&0&0&0&-1&0&1\\
    0&1&0&0&-1&0&0&1\\
    0&0&1&0&1&1&0&-1\\
    0&0&0&1&1&1&1&-2
    \end{array}\right]$$

!!! answer "Answer"
    **a)** not invertible ($\det = 0$).

    **b)** $A^{-1} = \begin{bmatrix}0&-1&0&1\\-1&0&0&1\\1&1&0&-1\\1&1&1&-2\end{bmatrix}$

---

## 2.9 · Which sets are subspaces of $\mathbb{R}^3$?

!!! theory "Topics & Definitions"
    - **Subspace** — a subset containing $\mathbf{0}$, closed under addition and scaling.
    - **The 3 tests** — contains $\mathbf{0}$; closed under $+$; closed under scalar $\times$.
    - **Span** — all linear combinations of given vectors; always a subspace.
    - **The 3 killers** — a square term, an integer-only condition, or $=$ a nonzero constant.

- **a.** A span of two vectors $\Rightarrow$ subspace.
- **b.** Has $\lambda^2$ (never negative); scaling $(1,-1,0)$ by $-1$ escapes $\Rightarrow$ not.
- **c.** A plane; through the origin only when $\gamma = 0$.
- **d.** Integer middle coordinate; scaling $(0,1,0)$ by $0.5$ escapes $\Rightarrow$ not.

!!! answer "Answer"
    **a)** subspace &nbsp;·&nbsp; **b)** not &nbsp;·&nbsp; **c)** subspace iff $\gamma = 0$ &nbsp;·&nbsp; **d)** not

---

## 2.10 · Linear independence

!!! theory "Topics & Definitions"
    - **Linearly independent** — the only combination giving $\mathbf{0}$ is all-zero coefficients.
    - **Linearly dependent** — some vector is a combination of the others.
    - **Method** — vectors as columns, row-reduce, count pivots.
    - **Rule** — pivot in every column $\Rightarrow$ independent; a missing column pivot $\Rightarrow$ dependent.

!!! steps "Vectors as columns, then reduce"
    $$\text{a)}\ \begin{bmatrix}2&1&3\\-1&1&-3\\3&-2&8\end{bmatrix}
    \longrightarrow
    \begin{bmatrix}2&1&3\\0&3&-3\\0&0&0\end{bmatrix}$$

    a) only 2 pivots, a zero row $\Rightarrow$ **dependent**. &nbsp; b) 3 pivots (rank 3) $\Rightarrow$ **independent**.

!!! answer "Answer"
    **a)** linearly dependent, with $\mathbf{x}_3 = 2\mathbf{x}_1 - \mathbf{x}_2$.

    **b)** linearly independent (rank $3$).

---

## 2.11 · Write $\mathbf{y}$ as a linear combination

!!! theory "Topics & Definitions"
    - **Linear combination** — $\lambda_1\mathbf{v}_1 + \lambda_2\mathbf{v}_2 + \lambda_3\mathbf{v}_3$: scale each vector, then add.
    - **Set-up** — build $[\mathbf{x}_1\ \mathbf{x}_2\ \mathbf{x}_3 \mid \mathbf{y}]$, same as solving a system.
    - **Method** — reduce to RREF; the coefficients appear in the final column.

!!! steps "$[\mathbf{x}_1\ \mathbf{x}_2\ \mathbf{x}_3 \mid \mathbf{y}] \to$ RREF"
    $$\left[\begin{array}{ccc|c}
    1&1&2&1\\1&2&-1&-2\\1&3&1&5
    \end{array}\right]
    \longrightarrow
    \left[\begin{array}{ccc|c}
    1&0&0&-6\\0&1&0&3\\0&0&1&2
    \end{array}\right]$$

    Check: $-6(1) + 3(1) + 2(2) = 1$, matching $\mathbf{y}$.

!!! answer "Answer"
    $$\mathbf{y} = -6\,\mathbf{x}_1 + 3\,\mathbf{x}_2 + 2\,\mathbf{x}_3$$

---

## 2.12 · Basis of $U_1 \cap U_2$

!!! steps "In progress"
    Set up the $4\times 6$ matrix $[\,\mathbf{u}_1\ \mathbf{u}_2\ \mathbf{u}_3 \mid -\mathbf{w}_1\ -\mathbf{w}_2\ -\mathbf{w}_3\,]$, reduce, and read the null space. Next step: $R_4 \to R_4 + \tfrac32 R_3$ gives $[\,0\,0\,0 \mid 0\ -1\ \tfrac72\,]$.

!!! answer "Answer"
    *To be completed.*
