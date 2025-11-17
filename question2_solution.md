# Solution: Question 2 - Pure Nash Equilibrium in Cubic Game

## Problem Statement

Consider a two-player zero-sum continuous-kernel game where:
- Player 1 chooses action **u₁ ∈ [0,1]**
- Player 2 chooses action **u₂ ∈ [0,1]**
- Cost function for Player 1:

$$J(u_1, u_2) = (u_1)^3 - 3u_1 u_2 + (u_2)^3$$

**Hint:** J is strictly convex in u₁, and for any given u₁, the maximum value of J with respect to u₂ is attained at either u₂ = 0 or u₂ = 1.

Since this is a **zero-sum game**:
- Player 1 wants to **minimize** J(u₁, u₂)
- Player 2 wants to **maximize** J(u₁, u₂)

## Solution Approach

### Step 1: Analyze Player 2's Best Response

Player 2 maximizes J with respect to u₂. Let's find the partial derivative:

$$\frac{\partial J}{\partial u_2} = -3u_1 + 3(u_2)^2 = 3(u_2^2 - u_1)$$

**Second-order condition:**
$$\frac{\partial^2 J}{\partial u_2^2} = 6u_2$$

This is positive for u₂ > 0, negative for u₂ < 0, and zero at u₂ = 0.

**Critical points (unconstrained):**
Setting the first derivative to zero:

$$3(u_2^2 - u_1) = 0$$
$$u_2 = \pm\sqrt{u_1}$$

Since u₂ ∈ [0,1], only u₂ = √u₁ is feasible (when u₁ ∈ [0,1]).

However, we need to check if this is a maximum or minimum. Since ∂²J/∂u₂² = 6u₂ = 6√u₁ > 0 for u₁ > 0, the critical point is a **local minimum**, not a maximum!

**This confirms the hint:** The maximum must be at the boundary (u₂ = 0 or u₂ = 1).

Let's compare J at both boundaries:

- At u₂ = 0: J(u₁, 0) = u₁³
- At u₂ = 1: J(u₁, 1) = u₁³ - 3u₁ + 1

**Player 2's best response:**

Player 2 chooses u₂ = 1 if J(u₁, 1) > J(u₁, 0), i.e., if:

$$u_1^3 - 3u_1 + 1 > u_1^3$$
$$-3u_1 + 1 > 0$$
$$u_1 < \frac{1}{3}$$

Therefore:
$$u_2^*(u_1) = \begin{cases}
1 & \text{if } u_1 < \frac{1}{3} \\
0 & \text{if } u_1 > \frac{1}{3}
\end{cases}$$

**At u₁ = 1/3:** J(1/3, 0) = (1/3)³ = 1/27 and J(1/3, 1) = 1/27 - 1 + 1 = 1/27, so both are equally good.

### Step 2: Analyze Player 1's Best Response

Player 1 minimizes J with respect to u₁. Let's find the partial derivative:

$$\frac{\partial J}{\partial u_1} = 3u_1^2 - 3u_2 = 3(u_1^2 - u_2)$$

**Second-order condition:**
$$\frac{\partial^2 J}{\partial u_1^2} = 6u_1 \geq 0$$

This confirms that J is convex in u₁ (as stated in the hint).

**Critical points (unconstrained):**
Setting the first derivative to zero:

$$3(u_1^2 - u_2) = 0$$
$$u_1 = \sqrt{u_2}$$

Since J is convex in u₁, this critical point is a minimum (when it exists in [0,1]).

**Player 1's best response:**

For u₂ ∈ [0,1], we have u₁ = √u₂ ∈ [0,1], so:

$$u_1^*(u_2) = \sqrt{u_2}$$

We should verify this is indeed the minimum by checking boundaries:
- At u₁ = 0: ∂J/∂u₁|_{u₁=0} = -3u₂ ≤ 0 (for u₂ ≥ 0), so moving away from 0 decreases J
- At u₁ = 1: ∂J/∂u₁|_{u₁=1} = 3(1 - u₂)
  - If u₂ < 1, this is positive, so we should move left
  - If u₂ > 1 (not possible), this would be negative

So the best response is:
$$u_1^*(u_2) = \begin{cases}
0 & \text{if } u_2 = 0 \\
\sqrt{u_2} & \text{if } 0 < u_2 \leq 1
\end{cases}$$

### Step 3: Find Nash Equilibria

A Nash equilibrium occurs where both best responses are satisfied simultaneously.

**Case 1: u₂* = 1**

This occurs when u₁ < 1/3 (from Player 2's BR).

Given u₂ = 1, Player 1's best response is:
$$u_1^* = \sqrt{1} = 1$$

But this contradicts u₁ < 1/3. So **no equilibrium** with u₂* = 1.

**Case 2: u₂* = 0**

This occurs when u₁ > 1/3 (from Player 2's BR).

Given u₂ = 0, Player 1's best response is:
$$u_1^* = \sqrt{0} = 0$$

But this contradicts u₁ > 1/3. So **no equilibrium** with u₂* = 0.

**Case 3: u₁* = 1/3 (the boundary case)**

At u₁ = 1/3, Player 2 is indifferent between u₂ = 0 and u₂ = 1.

Let's check if u₁ = 1/3 is Player 1's best response to any u₂:

$$u_1^*(u_2) = \sqrt{u_2} = \frac{1}{3}$$
$$u_2 = \frac{1}{9}$$

So if u₂ = 1/9, then Player 1's best response is u₁ = 1/3.

**Now check Player 2's best response to u₁ = 1/3:**

Compare:
- J(1/3, 0) = (1/3)³ = 1/27 ≈ 0.037
- J(1/3, 1/9) = (1/3)³ - 3(1/3)(1/9) + (1/9)³ = 1/27 - 1/9 + 1/729
  = 27/729 - 81/729 + 1/729 = -53/729 ≈ -0.073
- J(1/3, 1) = (1/3)³ - 3(1/3) + 1 = 1/27 - 1 + 1 = 1/27 ≈ 0.037

Player 2 wants to maximize J. The maximum is at u₂ = 0 or u₂ = 1 (both give 1/27), not at u₂ = 1/9.

This confirms that **u₂ = 1/9 is NOT a best response** for Player 2 when u₁ = 1/3.

### Step 4: Check for Mixed Strategy Insight

Since we found no pure Nash equilibrium, let's verify more carefully by examining the discontinuity in Player 2's best response.

Player 2's best response jumps from 1 to 0 at u₁ = 1/3. This discontinuity, combined with Player 1's continuous best response curve u₁ = √u₂, means they never intersect at a point where both players are playing best responses.

Let me create a more systematic analysis:

**For a Nash equilibrium (u₁*, u₂*) to exist:**

1. If u₂* > 0, then u₁* = √u₂* (Player 1's interior BR)
2. If u₁* < 1/3, then u₂* = 1 (Player 2's BR)
3. If u₁* > 1/3, then u₂* = 0 (Player 2's BR)

**Checking consistency:**

- If u₂* = 1: Then u₁* = 1, but Player 2's BR requires u₁* < 1/3. **Contradiction!**
- If u₂* = 0: Then u₁* = 0, but Player 2's BR requires u₁* > 1/3. **Contradiction!**
- If u₂* ∈ (0,1): Then u₁* = √u₂* must equal 1/3 (the switching point)
  - This gives u₂* = 1/9
  - But at u₁ = 1/3, Player 2 prefers u₂ = 0 or 1 over u₂ = 1/9. **Contradiction!**

## Final Answer

**NO, this game does NOT have a pure Nash equilibrium.**

### Explanation:

1. **Player 2's best response is discontinuous** at u₁ = 1/3, jumping from u₂ = 1 (for u₁ < 1/3) to u₂ = 0 (for u₁ > 1/3).

2. **Player 1's best response is continuous**: u₁ = √u₂, which is a smooth curve from (0,0) to (1,1).

3. **These two best response functions never intersect** at a point where both players simultaneously play best responses:
   - When u₂ = 1 (Player 2's BR for small u₁), Player 1 wants u₁ = 1, but then Player 2 wants u₂ = 0.
   - When u₂ = 0 (Player 2's BR for large u₁), Player 1 wants u₁ = 0, but then Player 2 wants u₂ = 1.
   - The discontinuity in Player 2's strategy prevents the intersection.

4. **The game would require a mixed strategy equilibrium** instead of a pure strategy equilibrium.

### Graphical Interpretation:

- Player 1's BR curve: u₁ = √u₂ is a smooth parabola
- Player 2's BR correspondence:
  - u₂ = 1 for u₁ ∈ [0, 1/3)
  - u₂ ∈ [0,1] for u₁ = 1/3 (indifferent)
  - u₂ = 0 for u₁ ∈ (1/3, 1]

These curves do not intersect at a fixed point, confirming no pure Nash equilibrium exists.

## Summary

The discontinuous nature of Player 2's best response function, caused by the cubic structure of the cost function, prevents the existence of a pure strategy Nash equilibrium. The game would require mixed strategies for an equilibrium to exist.

