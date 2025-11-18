# Solution: Question 4 - Team Optimization and Nash Equilibrium

## Part (i): General Analysis

### Problem Statement

Consider the cost function $J : \mathbb{R}^2 \to \mathbb{R}$ defined by:

$$J(\mathbf{u}_1, \mathbf{u}_2) = \begin{bmatrix} \mathbf{u}_1 \\ \mathbf{u}_2 \end{bmatrix}^T Q \begin{bmatrix} \mathbf{u}_1 \\ \mathbf{u}_2 \end{bmatrix} + p^T \begin{bmatrix} \mathbf{u}_1 \\ \mathbf{u}_2 \end{bmatrix} + s$$

where:
- $Q$ is a $2 \times 2$ matrix
- $p$ is a $2 \times 1$ vector: $p = \begin{bmatrix} p_1 \\ p_2 \end{bmatrix}$
- $s$ is a scalar
- $J$ is **strictly convex** on $\mathbb{R}^2$

**Notation:**
- $\mathbf{u}_1$ and $\mathbf{u}_2$ are scalars (actions of Player 1 and Player 2)
- Let $\mathbf{u} = \begin{bmatrix} \mathbf{u}_1 \\ \mathbf{u}_2 \end{bmatrix}$

We can write:
$$J(\mathbf{u}) = \mathbf{u}^T Q \mathbf{u} + p^T \mathbf{u} + s$$

### A. Team Optimization Solution

In team optimization, both players cooperate to minimize the same cost function $J$.

**Objective:** Find $\mathbf{u}^{opt} = \begin{bmatrix} u_1^{opt} \\ u_2^{opt} \end{bmatrix}$ that minimizes $J$.

Since $J$ is strictly convex, it has a unique global minimum.

**First-order necessary condition:**
$$\nabla J(\mathbf{u}) = \mathbf{0}$$

**Computing the gradient:**
$$\nabla J(\mathbf{u}) = \nabla(\mathbf{u}^T Q \mathbf{u} + p^T \mathbf{u} + s)$$

For a quadratic form $\mathbf{u}^T Q \mathbf{u}$:
$$\nabla(\mathbf{u}^T Q \mathbf{u}) = (Q + Q^T)\mathbf{u}$$

Therefore:
$$\nabla J(\mathbf{u}) = (Q + Q^T)\mathbf{u} + p$$

Setting the gradient to zero:
$$(Q + Q^T)\mathbf{u}^{opt} + p = \mathbf{0}$$

$$\mathbf{u}^{opt} = -(Q + Q^T)^{-1}p$$

**Note:** Since $J$ is strictly convex, $(Q + Q^T)$ is positive definite, hence invertible.

### Team Optimization Solution:
$$\boxed{\mathbf{u}^{opt} = -(Q + Q^T)^{-1}p}$$

---

### B. Two-Player Game Analysis

Now consider a two-player game where:
- $J_1 = J_2 = J$ (both players have the same cost function)
- Each player minimizes their own cost

This is called a **potential game** or **common-interest game**.

#### Finding Best Response Functions

**Player 1's Best Response $\mathcal{R}_1(\mathbf{u}_2)$:**

Player 1 minimizes $J(\mathbf{u}_1, \mathbf{u}_2)$ with respect to $\mathbf{u}_1$, treating $\mathbf{u}_2$ as fixed.

Taking the partial derivative:
$$\frac{\partial J}{\partial \mathbf{u}_1} = \frac{\partial}{\partial \mathbf{u}_1}\left[\mathbf{u}^T Q \mathbf{u} + p^T \mathbf{u} + s\right]$$

Let $Q = \begin{bmatrix} q_{11} & q_{12} \\ q_{21} & q_{22} \end{bmatrix}$

Then:
$$\mathbf{u}^T Q \mathbf{u} = q_{11}u_1^2 + q_{12}u_1 u_2 + q_{21}u_1 u_2 + q_{22}u_2^2$$
$$= q_{11}u_1^2 + (q_{12} + q_{21})u_1 u_2 + q_{22}u_2^2$$

And:
$$p^T \mathbf{u} = p_1 u_1 + p_2 u_2$$

So:
$$\frac{\partial J}{\partial u_1} = 2q_{11}u_1 + (q_{12} + q_{21})u_2 + p_1$$

Setting to zero:
$$2q_{11}u_1 + (q_{12} + q_{21})u_2 + p_1 = 0$$

$$u_1 = -\frac{(q_{12} + q_{21})u_2 + p_1}{2q_{11}}$$

**Player 1's Best Response:**
$$\boxed{\mathcal{R}_1(u_2) = -\frac{(q_{12} + q_{21})u_2 + p_1}{2q_{11}}}$$

**Player 2's Best Response $\mathcal{R}_2(\mathbf{u}_1)$:**

By symmetry:
$$\frac{\partial J}{\partial u_2} = (q_{12} + q_{21})u_1 + 2q_{22}u_2 + p_2 = 0$$

$$u_2 = -\frac{(q_{12} + q_{21})u_1 + p_2}{2q_{22}}$$

**Player 2's Best Response:**
$$\boxed{\mathcal{R}_2(u_1) = -\frac{(q_{12} + q_{21})u_1 + p_2}{2q_{22}}}$$

---

### C. Proving Best Response Functions Have At Most One Common Point

A Nash equilibrium occurs where:
$$u_1^* = \mathcal{R}_1(u_2^*) \quad \text{and} \quad u_2^* = \mathcal{R}_2(u_1^*)$$

This is equivalent to:
$$\frac{\partial J}{\partial u_1}\bigg|_{(u_1^*, u_2^*)} = 0 \quad \text{and} \quad \frac{\partial J}{\partial u_2}\bigg|_{(u_1^*, u_2^*)} = 0$$

Which means:
$$\nabla J(\mathbf{u}^*) = \mathbf{0}$$

Since $J$ is **strictly convex**, the gradient equation $\nabla J(\mathbf{u}) = \mathbf{0}$ has **at most one solution**.

**Proof:** If there were two solutions $\mathbf{u}^{(1)}$ and $\mathbf{u}^{(2)}$ with $\mathbf{u}^{(1)} \neq \mathbf{u}^{(2)}$, both would be global minima of the strictly convex function $J$, which is impossible.

### Conclusion:
$$\boxed{\text{The best response functions } \mathcal{R}_1 \text{ and } \mathcal{R}_2 \text{ have at most one common point.}}$$

Since the functions are continuous and $J$ is strictly convex on all of $\mathbb{R}^2$, they have **exactly one** common point.

---

### D. Nash Equilibrium is Unique and Equals Team Optimization

The Nash equilibrium $\mathbf{u}^*$ satisfies:
$$\nabla J(\mathbf{u}^*) = \mathbf{0}$$

The team optimization solution $\mathbf{u}^{opt}$ satisfies:
$$\nabla J(\mathbf{u}^{opt}) = \mathbf{0}$$

Since $J$ is strictly convex, this equation has a unique solution.

Therefore:
$$\boxed{\mathbf{u}^* = \mathbf{u}^{opt} = -(Q + Q^T)^{-1}p}$$

**Key Insight:** When both players have identical cost functions that are strictly convex, the Nash equilibrium coincides with the team optimization solution. There is no conflict of interest!

---

## Part (ii): Specific Matrix Case

### Problem Statement

Consider the same setup with:
$$Q = \begin{bmatrix} 2 & 3 \\ 3 & 2 \end{bmatrix}$$

### A. Check if J Has the Same Properties

For $J$ to be strictly convex, we need $Q + Q^T$ to be **positive definite**.

**Compute $Q + Q^T$:**
$$Q + Q^T = \begin{bmatrix} 2 & 3 \\ 3 & 2 \end{bmatrix} + \begin{bmatrix} 2 & 3 \\ 3 & 2 \end{bmatrix} = \begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix}$$

**Check positive definiteness:**

Method 1: Check eigenvalues
The eigenvalues of $\begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix}$ are found from:
$$\det\begin{bmatrix} 4-\lambda & 6 \\ 6 & 4-\lambda \end{bmatrix} = 0$$
$$(4-\lambda)^2 - 36 = 0$$
$$16 - 8\lambda + \lambda^2 - 36 = 0$$
$$\lambda^2 - 8\lambda - 20 = 0$$
$$\lambda = \frac{8 \pm \sqrt{64 + 80}}{2} = \frac{8 \pm \sqrt{144}}{2} = \frac{8 \pm 12}{2}$$

$$\lambda_1 = 10, \quad \lambda_2 = -2$$

**Since $\lambda_2 = -2 < 0$, the matrix is NOT positive definite!**

Method 2: Check determinants (Sylvester's criterion)
- First leading principal minor: $4 > 0$ ✓
- Second leading principal minor: $\det\begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix} = 16 - 36 = -20 < 0$ ✗

### Answer:
$$\boxed{\text{NO, } J \text{ does NOT have the same properties as in (i)}}$$

$J$ is **NOT strictly convex** (in fact, it's indefinite - a saddle point function).

---

### B. Comment on Team Optimization Problem

Since $J$ is not convex, the team optimization problem may not have a unique global minimum. In fact:

1. **Critical point exists:** The gradient equation $(Q + Q^T)\mathbf{u} + p = \mathbf{0}$ still has a solution:
   $$\mathbf{u}_{crit} = -(Q + Q^T)^{-1}p = -\begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix}^{-1}p$$

   Note: $(Q + Q^T)$ is still invertible despite not being positive definite:
   $$\det(Q + Q^T) = -20 \neq 0$$

2. **Nature of critical point:** Since the Hessian $Q + Q^T$ has both positive and negative eigenvalues, the critical point is a **saddle point**, not a minimum.

3. **Implication:** The team optimization problem **does not have a minimum** on $\mathbb{R}^2$. The cost can go to $-\infty$ along certain directions.

**If there are constraints** (e.g., $\mathbf{u}_1, \mathbf{u}_2 \in [a, b]$), then a minimum would exist on the boundary of the feasible region.

---

### C. Nash Equilibrium in the Two-Player Game

Even though $J$ is not convex, we can still analyze the Nash equilibrium.

**Computing $(Q + Q^T)^{-1}$:**
$$Q + Q^T = \begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix}$$

$$(Q + Q^T)^{-1} = \frac{1}{-20}\begin{bmatrix} 4 & -6 \\ -6 & 4 \end{bmatrix} = \begin{bmatrix} -1/5 & 3/10 \\ 3/10 & -1/5 \end{bmatrix}$$

**Best Response Functions:**

From earlier, we have:
$$\mathcal{R}_1(u_2) = -\frac{6u_2 + p_1}{4} = -\frac{3u_2}{2} - \frac{p_1}{4}$$

$$\mathcal{R}_2(u_1) = -\frac{6u_1 + p_2}{4} = -\frac{3u_1}{2} - \frac{p_2}{4}$$

**Nash Equilibrium:**

Substituting the first into the second:
$$u_2^* = -\frac{3}{2}\left(-\frac{3u_2^*}{2} - \frac{p_1}{4}\right) - \frac{p_2}{4}$$
$$u_2^* = \frac{9u_2^*}{4} + \frac{3p_1}{8} - \frac{p_2}{4}$$
$$u_2^* - \frac{9u_2^*}{4} = \frac{3p_1}{8} - \frac{p_2}{4}$$
$$-\frac{5u_2^*}{4} = \frac{3p_1}{8} - \frac{2p_2}{8}$$
$$u_2^* = -\frac{4}{5} \cdot \frac{3p_1 - 2p_2}{8} = -\frac{3p_1 - 2p_2}{10}$$
$$u_2^* = \frac{-3p_1 + 2p_2}{10} = \frac{3p_2 - 6p_1}{20} = \frac{3p_2}{20} - \frac{3p_1}{10}$$

Wait, let me recalculate more carefully. We have:
$$(Q + Q^T)\mathbf{u}^* = -p$$

$$\begin{bmatrix} 4 & 6 \\ 6 & 4 \end{bmatrix}\begin{bmatrix} u_1^* \\ u_2^* \end{bmatrix} = -\begin{bmatrix} p_1 \\ p_2 \end{bmatrix}$$

$$\mathbf{u}^* = -\begin{bmatrix} -1/5 & 3/10 \\ 3/10 & -1/5 \end{bmatrix}\begin{bmatrix} p_1 \\ p_2 \end{bmatrix}$$

$$= \begin{bmatrix} p_1/5 - 3p_2/10 \\ -3p_1/10 + p_2/5 \end{bmatrix} = \begin{bmatrix} (2p_1 - 3p_2)/10 \\ (2p_2 - 3p_1)/10 \end{bmatrix}$$

**Uniqueness:**

The Nash equilibrium is found by solving:
$$(Q + Q^T)\mathbf{u} = -p$$

Since $(Q + Q^T)$ is invertible (det ≠ 0), this system has a **unique solution**.

### Answer:
$$\boxed{\text{YES, the NE solution is still UNIQUE}}$$

$$\mathbf{u}^* = -(Q + Q^T)^{-1}p = \frac{1}{10}\begin{bmatrix} 2p_1 - 3p_2 \\ 2p_2 - 3p_1 \end{bmatrix}$$

**Key Observation:** Uniqueness of the Nash equilibrium depends on $(Q + Q^T)$ being **invertible** (non-singular), NOT on it being positive definite. The positive definiteness ensures that:
1. The critical point is a minimum (relevant for team optimization)
2. The game is a potential game with a well-defined potential function

But for uniqueness of Nash equilibrium in this specific game structure, we only need invertibility.

---

## Summary

### Part (i):
- **Team optimization:** $\mathbf{u}^{opt} = -(Q + Q^T)^{-1}p$ (unique due to strict convexity)
- **Best responses:** Linear functions of opponent's action
- **Nash equilibrium:** Unique, coincides with team optimum
- **Key property:** Strict convexity ensures uniqueness and optimality

### Part (ii) with $Q = \begin{bmatrix} 2 & 3 \\ 3 & 2 \end{bmatrix}$:
- **Convexity:** NO, $J$ is not convex (saddle point)
- **Team optimization:** No minimum exists on $\mathbb{R}^2$ (cost unbounded below)
- **Nash equilibrium:** Still UNIQUE at $\mathbf{u}^* = -(Q + Q^T)^{-1}p$
- **Reason for uniqueness:** $(Q + Q^T)$ is invertible (though not positive definite)
- **Interpretation:** Even though the game doesn't have a "good" team solution, players still reach a unique equilibrium (a saddle point)

