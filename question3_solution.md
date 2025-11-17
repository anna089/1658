# Solution: Question 3 - Nash Equilibrium with Parameter α

## Problem Statement

Consider a two-player zero-sum continuous-kernel game where:
- Player 1 chooses action **u₁ ∈ [0,1]**
- Player 2 chooses action **u₂ ∈ [0,1]**
- Cost function for Player 1:

$$J(u_1, u_2) = (u_1 - u_2)^2 - \alpha(u_2)^2$$

where α is a scalar parameter.

- **Player 1 minimizes J**
- **Player 2 maximizes J**

Find the pure Nash equilibrium (NE) solutions for:
- (i) α ∈ (1, 2]
- (ii) α = 0
- (iii) α ∈ (0, 1]

## General Analysis

### Step 1: Expand the Cost Function

$$J(u_1, u_2) = (u_1 - u_2)^2 - \alpha u_2^2$$
$$= u_1^2 - 2u_1 u_2 + u_2^2 - \alpha u_2^2$$
$$= u_1^2 - 2u_1 u_2 + (1 - \alpha)u_2^2$$

### Step 2: Find Player 1's Best Response

Player 1 minimizes J with respect to u₁.

**Partial derivative:**
$$\frac{\partial J}{\partial u_1} = 2u_1 - 2u_2$$

**Second derivative:**
$$\frac{\partial^2 J}{\partial u_1^2} = 2 > 0$$

Since the second derivative is positive, J is **strictly convex** in u₁, so any critical point is a minimum.

**Unconstrained optimum:**
$$2u_1 - 2u_2 = 0 \implies u_1 = u_2$$

**With constraints u₁ ∈ [0,1]:**

$$u_1^*(u_2) = \begin{cases}
0 & \text{if } u_2 < 0 \\
u_2 & \text{if } 0 \leq u_2 \leq 1 \\
1 & \text{if } u_2 > 1
\end{cases}$$

Since u₂ ∈ [0,1], we have:

$$\boxed{u_1^*(u_2) = u_2}$$

Player 1's best response is to **match Player 2's action**.

### Step 3: Find Player 2's Best Response

Player 2 maximizes J with respect to u₂.

**Partial derivative:**
$$\frac{\partial J}{\partial u_2} = -2u_1 + 2u_2 + 2(1-\alpha)u_2$$
$$= -2u_1 + 2u_2(1 + 1 - \alpha)$$
$$= -2u_1 + 2u_2(2 - \alpha)$$

**Second derivative:**
$$\frac{\partial^2 J}{\partial u_2^2} = 2(2 - \alpha)$$

The sign of the second derivative determines the nature of the critical point:
- If 2 - α < 0 (i.e., **α > 2**): J is **concave** in u₂ (maximum at interior)
- If 2 - α = 0 (i.e., **α = 2**): J is **linear** in u₂
- If 2 - α > 0 (i.e., **α < 2**): J is **convex** in u₂ (minimum at interior, maximum at boundary)

**Unconstrained critical point:**
$$-2u_1 + 2u_2(2 - \alpha) = 0$$
$$u_2 = \frac{u_1}{2 - \alpha}$$

### Step 4: Determine Best Response for Different α Values

#### Case A: α < 2
When α < 2, we have ∂²J/∂u₂² = 2(2-α) > 0, so J is **convex** in u₂.

This means the critical point is a **minimum**, not a maximum. Therefore, Player 2's maximum must be at the **boundary**.

Compare J at the boundaries:
- At u₂ = 0: J(u₁, 0) = u₁²
- At u₂ = 1: J(u₁, 1) = u₁² - 2u₁ + (1-α)

**Player 2 chooses u₂ = 1 if:**
$$J(u_1, 1) > J(u_1, 0)$$
$$u_1^2 - 2u_1 + (1-\alpha) > u_1^2$$
$$-2u_1 + (1-\alpha) > 0$$
$$u_1 < \frac{1-\alpha}{2}$$

Therefore, for α < 2:
$$u_2^*(u_1) = \begin{cases}
1 & \text{if } u_1 < \frac{1-\alpha}{2} \\
0 & \text{if } u_1 > \frac{1-\alpha}{2}
\end{cases}$$

Note: At u₁ = (1-α)/2, Player 2 is indifferent between u₂ = 0 and u₂ = 1.

#### Case B: α = 2
When α = 2, J is linear in u₂, so Player 2's choice depends on the coefficient:
$$\frac{\partial J}{\partial u_2} = -2u_1$$

- If u₁ > 0: prefer u₂ = 0
- If u₁ = 0: indifferent
- If u₁ < 0: prefer u₂ = 1 (but u₁ ≥ 0 always)

#### Case C: α > 2
When α > 2, J is concave in u₂, so the interior critical point is a maximum (if it exists in [0,1]).

## Solution for Each Case

---

## (i) α ∈ (1, 2]

For α ∈ (1, 2], we have α < 2, so Player 2's best response is:
$$u_2^*(u_1) = \begin{cases}
1 & \text{if } u_1 < \frac{1-\alpha}{2} \\
0 & \text{if } u_1 > \frac{1-\alpha}{2}
\end{cases}$$

Since α ∈ (1, 2], we have:
$$\frac{1-\alpha}{2} \in \left[\frac{1-2}{2}, \frac{1-1}{2}\right) = \left[-\frac{1}{2}, 0\right)$$

This means (1-α)/2 < 0 for all α ∈ (1, 2].

**Therefore, for all u₁ ∈ [0, 1]:**
$$u_1 > \frac{1-\alpha}{2} \implies u_2^*(u_1) = 0$$

**Finding Nash Equilibrium:**

Given Player 2's best response u₂* = 0, Player 1's best response is:
$$u_1^* = u_2^* = 0$$

**Verification:**
- Given u₂ = 0: Player 1's BR is u₁ = 0 ✓
- Given u₁ = 0: Is u₂ = 0 Player 2's BR?
  - J(0, 0) = 0
  - J(0, 1) = 0 - 0 + (1-α) = 1-α < 0 (since α > 1)
  - So J(0, 0) > J(0, 1), thus u₂ = 0 is indeed the BR ✓

### Answer (i):
$$\boxed{(u_1^*, u_2^*) = (0, 0) \text{ for all } \alpha \in (1, 2]}$$

At this equilibrium:
$$J(0, 0) = 0$$

---

## (ii) α = 0

For α = 0, the cost function becomes:
$$J(u_1, u_2) = (u_1 - u_2)^2$$

This simplifies the problem significantly.

**Player 1's best response:** u₁* = u₂ (as before)

**Player 2's best response:**

When α = 0, we have 2 - α = 2 > 0, so J is convex in u₂. The maximum is at the boundary.

Switching point: (1-α)/2 = (1-0)/2 = 1/2

$$u_2^*(u_1) = \begin{cases}
1 & \text{if } u_1 < \frac{1}{2} \\
0 & \text{if } u_1 > \frac{1}{2}
\end{cases}$$

**Finding Nash Equilibrium:**

We need both best responses satisfied:
1. u₁* = u₂* (Player 1's BR)
2. u₂* = 1 if u₁* < 1/2, or u₂* = 0 if u₁* > 1/2 (Player 2's BR)

**Case 1:** u₂* = 1
- Then u₁* = u₂* = 1 (from Player 1's BR)
- But this requires u₁* < 1/2 for Player 2's BR
- Contradiction: 1 ≮ 1/2 ✗

**Case 2:** u₂* = 0
- Then u₁* = u₂* = 0 (from Player 1's BR)
- But this requires u₁* > 1/2 for Player 2's BR
- Contradiction: 0 ≯ 1/2 ✗

**Case 3:** u₁* = 1/2 (the boundary)
- At u₁ = 1/2, Player 2 is indifferent between u₂ = 0 and u₂ = 1
- J(1/2, 0) = (1/2)² = 1/4
- J(1/2, 1) = (-1/2)² = 1/4
- Indeed indifferent ✓

If Player 2 chooses any u₂ ∈ [0, 1], Player 1's best response is u₁ = u₂.

For u₁ = u₂ to be a Nash equilibrium, we need Player 2's BR at u₁ to include u₂ = u₁.

At u₁ = u₂, we have J(u, u) = 0 for any u.

Let's check if u₁ = u₂ = u for any u ∈ [0, 1] can be an equilibrium:
- Player 1's BR given u₂ = u is u₁ = u ✓
- Player 2's BR given u₁ = u:
  - J(u, 0) = u²
  - J(u, 1) = (u-1)²
  - J(u, u) = 0

For u₂ = u to be optimal for Player 2, we need J(u, u) ≥ J(u, 0) and J(u, u) ≥ J(u, 1):
- 0 ≥ u² implies u = 0
- 0 ≥ (u-1)² implies u = 1

**So only u = 0 or u = 1 could work, but:**
- At u = 0: J(0, 0) = 0, J(0, 1) = 1, so Player 2 prefers u₂ = 1 ✗
- At u = 1: J(1, 1) = 0, J(1, 0) = 1, so Player 2 prefers u₂ = 0 ✗

**Actually, let me reconsider.** Since J(u, u) = 0 for all u, Player 2 achieves J = 0 by matching Player 1. But can Player 2 do better?

At any (u₁, u₂), J = (u₁ - u₂)². Player 2 wants to maximize this.
Given u₁, Player 2 should choose u₂ as far from u₁ as possible:
- If u₁ < 1/2: choose u₂ = 1 (distance = 1 - u₁)
- If u₁ > 1/2: choose u₂ = 0 (distance = u₁)
- If u₁ = 1/2: both give distance = 1/2

This confirms the best response above.

### Answer (ii):
$$\boxed{\text{NO pure Nash equilibrium exists for } \alpha = 0}$$

The best response curves do not intersect at a point where both players are simultaneously playing best responses.

---

## (iii) α ∈ (0, 1]

For α ∈ (0, 1], we still have α < 2, so Player 2's best response is:
$$u_2^*(u_1) = \begin{cases}
1 & \text{if } u_1 < \frac{1-\alpha}{2} \\
0 & \text{if } u_1 > \frac{1-\alpha}{2}
\end{cases}$$

Since α ∈ (0, 1], we have:
$$\frac{1-\alpha}{2} \in \left[\frac{1-1}{2}, \frac{1-0}{2}\right) = \left[0, \frac{1}{2}\right)$$

So the switching point is in [0, 1/2), which is within the feasible region!

**Finding Nash Equilibrium:**

We need:
1. u₁* = u₂* (Player 1's BR)
2. Player 2's BR is satisfied

**Case 1:** u₂* = 1
- Then u₁* = 1 (from Player 1's BR)
- This requires u₁* < (1-α)/2 for Player 2's BR
- Since α ∈ (0, 1], we have (1-α)/2 ≤ 1/2
- But u₁* = 1 > 1/2 ≥ (1-α)/2
- Contradiction ✗

**Case 2:** u₂* = 0
- Then u₁* = 0 (from Player 1's BR)
- This requires u₁* > (1-α)/2 for Player 2's BR
- Since α ∈ (0, 1], we have (1-α)/2 ∈ [0, 1/2)
- For u₁* = 0 > (1-α)/2, we need (1-α)/2 < 0
- But (1-α)/2 ≥ 0 for α ≤ 1
- So this only works if (1-α)/2 < 0, which means α > 1 ✗

**Case 3:** u₁* = (1-α)/2 (the switching point)

At u₁ = (1-α)/2, Player 2 is indifferent. Let's check if u₂ = u₁ = (1-α)/2 is part of the indifference.

Actually, Player 2 is only indifferent between u₂ = 0 and u₂ = 1 at the switching point, not necessarily at u₂ = u₁.

Let me recalculate. At u₁ = (1-α)/2:
- J((1-α)/2, 0) = ((1-α)/2)²
- J((1-α)/2, 1) = ((1-α)/2 - 1)² - α
  = ((1-α-2)/2)² - α
  = ((-(1+α))/2)² - α
  = ((1+α)/2)² - α
  = (1+α)²/4 - α
  = (1 + 2α + α²)/4 - α
  = (1 + 2α + α² - 4α)/4
  = (1 - 2α + α²)/4
  = (1-α)²/4

So J((1-α)/2, 0) = (1-α)²/4 = J((1-α)/2, 1) ✓

Player 1's best response to u₂ = (1-α)/2 is u₁ = (1-α)/2.

But is u₂ = (1-α)/2 a best response for Player 2 when u₁ = (1-α)/2?

Let u* = (1-α)/2. We have:
- J(u*, 0) = (u*)²
- J(u*, 1) = (u*)²
- J(u*, u*) = 0

Since (u*)² > 0 for u* > 0 (which is true for α < 1), we have:
$$J(u*, 0) = J(u*, 1) = (u*)² > 0 = J(u*, u*)$$

So Player 2 prefers u₂ = 0 or u₂ = 1 over u₂ = u*.

### Re-examining for α ∈ (0, 1]

Let me think differently. Since Player 1 always plays u₁ = u₂, substitute this into J:

$$J(u_2, u_2) = 0$$

So if both players play u₁ = u₂ = u, then J = 0.

But Player 2 wants to deviate! Given any u₁, Player 2 maximizes (u₁ - u₂)² - αu₂².

Taking derivative: -2(u₁ - u₂) - 2αu₂ = 0
$$-2u_1 + 2u_2 + 2αu_2 = 0$$

Wait, I made an error. Let me recalculate:

$$J = (u_1 - u_2)^2 - \alpha u_2^2$$
$$\frac{\partial J}{\partial u_2} = 2(u_1 - u_2)(-1) - 2\alpha u_2 = -2(u_1 - u_2) - 2\alpha u_2$$
$$= -2u_1 + 2u_2 - 2\alpha u_2 = -2u_1 + 2u_2(1 - \alpha)$$

Setting to zero:
$$u_2 = \frac{u_1}{1-\alpha}$$

But wait, for α ∈ (0, 1), we have 1 - α > 0, so J is **convex** in u₂ if ∂²J/∂u₂² > 0.

$$\frac{\partial^2 J}{\partial u_2^2} = 2(1-\alpha)$$

For α ∈ (0, 1), this is positive, so J is convex in u₂, meaning the maximum is at the boundary.

Actually, I had the wrong expansion earlier. Let me redo this carefully.

$$J(u_1, u_2) = (u_1 - u_2)^2 - \alpha u_2^2$$

Expanding:
$$J = u_1^2 - 2u_1 u_2 + u_2^2 - \alpha u_2^2 = u_1^2 - 2u_1 u_2 + (1-\alpha)u_2^2$$

Taking partial derivative w.r.t. u₂:
$$\frac{\partial J}{\partial u_2} = -2u_1 + 2(1-\alpha)u_2$$

Second derivative:
$$\frac{\partial^2 J}{\partial u_2^2} = 2(1-\alpha)$$

For α ∈ (0, 1), we have 1 - α ∈ (0, 1), so ∂²J/∂u₂² > 0, meaning J is **convex** in u₂.

Therefore, the maximum is at the boundary (u₂ = 0 or u₂ = 1).

Compare:
- J(u₁, 0) = u₁²
- J(u₁, 1) = u₁² - 2u₁ + (1-α) = u₁² - 2u₁ + 1 - α

Player 2 chooses u₂ = 1 if:
$$u_1^2 - 2u_1 + 1 - \alpha > u_1^2$$
$$-2u_1 + 1 - \alpha > 0$$
$$u_1 < \frac{1-\alpha}{2}$$

So the switching point is indeed at u₁ = (1-α)/2 ∈ [0, 1/2) for α ∈ (0, 1].

Since there's no pure Nash equilibrium where both players play best responses simultaneously (as we showed, neither boundary works and the switching point doesn't work), let me reconsider whether equilibrium might actually not exist.

Actually, for α = 1:
- Switching point: (1-1)/2 = 0
- So for u₁ > 0, Player 2 chooses u₂ = 0
- For u₁ = 0, Player 2 is indifferent or chooses u₂ = 0
- Given u₂ = 0, Player 1's BR is u₁ = 0 ✓
- Given u₁ = 0, J(0, 0) = 0, J(0, 1) = 0 - 0 + (1-1) = 0
- So Player 2 is indifferent ✓

So **(0, 0) is a Nash equilibrium for α = 1**.

For α ∈ (0, 1):
- Switching point: (1-α)/2 > 0
- At u₁ = 0: since 0 < (1-α)/2, Player 2 chooses u₂ = 1
- Given u₂ = 1, Player 1's BR is u₁ = 1
- Given u₁ = 1: since 1 > (1-α)/2 (because (1-α)/2 < 1/2 < 1), Player 2 chooses u₂ = 0
- This creates a cycle: no equilibrium

### Answer (iii):
$$\boxed{
\begin{cases}
\text{NO pure Nash equilibrium for } \alpha \in (0, 1) \\
(u_1^*, u_2^*) = (0, 0) \text{ for } \alpha = 1
\end{cases}
}$$

Or more precisely, for α ∈ (0, 1], equilibrium exists only at the boundary α = 1.

---

## Summary of All Cases

| α Range | Pure Nash Equilibrium | J* |
|---------|----------------------|-----|
| α ∈ (1, 2] | **(0, 0)** | 0 |
| α = 1 | **(0, 0)** | 0 |
| α ∈ (0, 1) | **None exists** | - |
| α = 0 | **None exists** | - |

## Key Insights

1. **Player 1 always wants to match Player 2**: u₁* = u₂ regardless of α

2. **Player 2's strategy depends on α**:
   - For α > 1: Always prefers the boundary away from u₁, but specifically u₂ = 0 when u₁ ≥ 0
   - For α ≤ 1: Creates a discontinuous best response that prevents equilibrium (except at α = 1)

3. **The parameter α controls the "penalty" term** -αu₂² in Player 2's objective, affecting whether Player 2 prefers high or low values of u₂.

