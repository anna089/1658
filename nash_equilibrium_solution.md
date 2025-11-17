# Solution: Pure Nash Equilibrium in Two-Player Zero-Sum Game

## Problem Statement

Consider a two-player zero-sum continuous-kernel game where:
- Player 1 chooses action **u₁ ∈ [0,1]**
- Player 2 chooses action **u₂ ∈ [0,1]**
- Cost function for Player 1:

$$J(u_1, u_2) = -\frac{1}{2}(u_2)^2 + 2(u_1)^2 + 2u_1 u_2 - \frac{7}{2}u_1 - \frac{5}{4}u_2$$

Since this is a **zero-sum game**:
- Player 1 wants to **minimize** J(u₁, u₂)
- Player 2 wants to **maximize** J(u₁, u₂)

## Solution Approach

A pure Nash equilibrium (u₁*, u₂*) exists if:
1. u₁* is the best response for Player 1 given u₂*
2. u₂* is the best response for Player 2 given u₁*

### Step 1: Find Player 1's Best Response Function

Player 1 minimizes J with respect to u₁. Taking the partial derivative:

$$\frac{\partial J}{\partial u_1} = 4u_1 + 2u_2 - \frac{7}{2}$$

**Second-order condition:**
$$\frac{\partial^2 J}{\partial u_1^2} = 4 > 0$$

Since the second derivative is positive, J is **convex** in u₁, confirming we have a minimum.

**First-order condition (unconstrained):**
Setting the first derivative to zero:

$$4u_1 + 2u_2 - \frac{7}{2} = 0$$

$$u_1 = \frac{7/2 - 2u_2}{4} = \frac{7}{8} - \frac{u_2}{2}$$

**Accounting for constraints u₁ ∈ [0,1]:**

$$u_1^*(u_2) = \begin{cases}
0 & \text{if } \frac{7}{8} - \frac{u_2}{2} < 0 \text{ (i.e., } u_2 > \frac{7}{4}) \\
\frac{7}{8} - \frac{u_2}{2} & \text{if } 0 \leq \frac{7}{8} - \frac{u_2}{2} \leq 1 \text{ (i.e., } -\frac{3}{4} \leq u_2 \leq \frac{7}{4}) \\
1 & \text{if } \frac{7}{8} - \frac{u_2}{2} > 1 \text{ (i.e., } u_2 < -\frac{3}{4})
\end{cases}$$

Since u₂ ∈ [0,1], we have:

$$u_1^*(u_2) = \frac{7}{8} - \frac{u_2}{2} \quad \forall u_2 \in [0,1]$$

### Step 2: Find Player 2's Best Response Function

Player 2 maximizes J with respect to u₂. Taking the partial derivative:

$$\frac{\partial J}{\partial u_2} = -u_2 + 2u_1 - \frac{5}{4}$$

**Second-order condition:**
$$\frac{\partial^2 J}{\partial u_2^2} = -1 < 0$$

Since the second derivative is negative, J is **concave** in u₂, confirming we have a maximum.

**First-order condition (unconstrained):**
Setting the first derivative to zero:

$$-u_2 + 2u_1 - \frac{5}{4} = 0$$

$$u_2 = 2u_1 - \frac{5}{4}$$

**Accounting for constraints u₂ ∈ [0,1]:**

$$u_2^*(u_1) = \begin{cases}
0 & \text{if } 2u_1 - \frac{5}{4} < 0 \text{ (i.e., } u_1 < \frac{5}{8}) \\
2u_1 - \frac{5}{4} & \text{if } 0 \leq 2u_1 - \frac{5}{4} \leq 1 \text{ (i.e., } \frac{5}{8} \leq u_1 \leq \frac{9}{8}) \\
1 & \text{if } 2u_1 - \frac{5}{4} > 1 \text{ (i.e., } u_1 > \frac{9}{8})
\end{cases}$$

Since u₁ ∈ [0,1], we need to check which case applies.

For u₁ ∈ [0, 5/8): u₂* = 0
For u₁ ∈ [5/8, 1]: u₂* = 2u₁ - 5/4

### Step 3: Find the Nash Equilibrium

A Nash equilibrium occurs where both best response functions are satisfied simultaneously.

**Case 1: Interior solution** (both u₁*, u₂* satisfy FOCs)

$$u_1 = \frac{7}{8} - \frac{u_2}{2}$$
$$u_2 = 2u_1 - \frac{5}{4}$$

Substituting the second equation into the first:

$$u_1 = \frac{7}{8} - \frac{1}{2}\left(2u_1 - \frac{5}{4}\right)$$

$$u_1 = \frac{7}{8} - u_1 + \frac{5}{8}$$

$$2u_1 = \frac{12}{8} = \frac{3}{2}$$

$$u_1^* = \frac{3}{4}$$

Then:
$$u_2^* = 2 \cdot \frac{3}{4} - \frac{5}{4} = \frac{6}{4} - \frac{5}{4} = \frac{1}{4}$$

**Verification that this is an interior solution:**
- u₁* = 3/4 ∈ [0,1] ✓
- u₂* = 1/4 ∈ [0,1] ✓
- For u₁* = 3/4: We need u₁ ≥ 5/8 for the interior solution of u₂. Since 3/4 = 6/8 > 5/8 ✓

### Step 4: Verify Nash Equilibrium Conditions

**Check Player 1's best response:**
Given u₂* = 1/4, Player 1's best response is:
$$u_1^* = \frac{7}{8} - \frac{1/4}{2} = \frac{7}{8} - \frac{1}{8} = \frac{6}{8} = \frac{3}{4}$$ ✓

**Check Player 2's best response:**
Given u₁* = 3/4, Player 2's best response is:
$$u_2^* = 2 \cdot \frac{3}{4} - \frac{5}{4} = \frac{1}{4}$$ ✓

Both conditions are satisfied!

### Step 5: Verify by Checking Deviations

**Can Player 1 improve by deviating?**

At (3/4, 1/4), the gradient with respect to u₁ is:
$$\frac{\partial J}{\partial u_1}\bigg|_{u_1=3/4, u_2=1/4} = 4 \cdot \frac{3}{4} + 2 \cdot \frac{1}{4} - \frac{7}{2} = 3 + \frac{1}{2} - \frac{7}{2} = 0$$

Since the gradient is zero and the second derivative is positive, this is indeed a minimum for Player 1. ✓

**Can Player 2 improve by deviating?**

At (3/4, 1/4), the gradient with respect to u₂ is:
$$\frac{\partial J}{\partial u_2}\bigg|_{u_1=3/4, u_2=1/4} = -\frac{1}{4} + 2 \cdot \frac{3}{4} - \frac{5}{4} = -\frac{1}{4} + \frac{6}{4} - \frac{5}{4} = 0$$

Since the gradient is zero and the second derivative is negative, this is indeed a maximum for Player 2. ✓

## Final Answer

**YES, this game has a pure Nash equilibrium:**

$$\boxed{(u_1^*, u_2^*) = \left(\frac{3}{4}, \frac{1}{4}\right)}$$

**At this equilibrium, the cost is:**

$$J\left(\frac{3}{4}, \frac{1}{4}\right) = -\frac{1}{2}\left(\frac{1}{4}\right)^2 + 2\left(\frac{3}{4}\right)^2 + 2 \cdot \frac{3}{4} \cdot \frac{1}{4} - \frac{7}{2} \cdot \frac{3}{4} - \frac{5}{4} \cdot \frac{1}{4}$$

$$= -\frac{1}{32} + 2 \cdot \frac{9}{16} + \frac{6}{16} - \frac{21}{8} - \frac{5}{16}$$

$$= -\frac{1}{32} + \frac{18}{16} + \frac{6}{16} - \frac{42}{16} - \frac{5}{16}$$

$$= -\frac{1}{32} + \frac{18 + 6 - 42 - 5}{16}$$

$$= -\frac{1}{32} - \frac{23}{16} = -\frac{1}{32} - \frac{46}{32} = -\frac{47}{32}$$

## Summary

The game has a unique pure Nash equilibrium at **(u₁*, u₂*) = (3/4, 1/4)** where:
- Player 1 cannot reduce the cost by unilaterally changing u₁
- Player 2 cannot increase the cost by unilaterally changing u₂
- Both players are playing their best responses to each other's strategies

