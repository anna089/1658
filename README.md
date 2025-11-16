# Control Systems Exercises - MATLAB Solutions

This repository contains MATLAB solutions for Exercises 3.9, 3.10, and 3.11 from a control systems course.

## Files

1. **exercise_3_9.m** - Dynamical system analysis with exponential stability and domain of attraction
2. **exercise_3_10.m** - Adaptive control of pendulum with unknown mass parameter
3. **exercise_3_11.m** - Adaptive control of pendulum with both unknown mass and inertia parameters

## How to Run

### Option 1: Run in MATLAB Desktop Application
1. Open MATLAB
2. Navigate to this directory
3. Run each script by typing:
   ```matlab
   exercise_3_9
   exercise_3_10
   exercise_3_11
   ```

### Option 2: Run from Command Line (if MATLAB is in PATH)
```bash
matlab -batch "run('exercise_3_9.m')"
matlab -batch "run('exercise_3_10.m')"
matlab -batch "run('exercise_3_11.m')"
```

### Option 3: Run from Command Line (macOS with specific MATLAB version)
```bash
/Applications/MATLAB_R2024a.app/bin/matlab -batch "run('exercise_3_9.m')"
```
(Replace R2024a with your installed MATLAB version)

## Exercise Descriptions

### Exercise 3.9: Dynamical System Analysis
Analyzes a nonlinear dynamical system of the form ẋ = Ax + g(x) where:
- A is a Hurwitz matrix (stable)
- g(x) is locally Lipschitz with ||g(x)|| ≤ γ||x||²

**What the script does:**
1. Verifies that A is Hurwitz (eigenvalues have negative real parts)
2. Estimates the Lipschitz constant γ numerically
3. Estimates the domain of attraction using Lyapunov function level sets
4. Generates phase portrait using `streamslice` command
5. Simulates trajectories from multiple initial conditions
6. Analyzes conservativeness of the domain of attraction estimate

**Output:**
- Eigenvalues of A
- Estimated γ value
- Two subplots showing:
  - Phase portrait with streamlines and domain of attraction estimates
  - Simulated trajectories with Lyapunov level sets
- Analysis of how conservative the estimate is

### Exercise 3.10: Adaptive Control (Unknown Mass)
Implements an adaptive controller for a controlled pendulum with:
- Known moment of inertia parameter (mI)
- Unknown mass parameter (θ)

**System dynamics:**
```
ẋ₁ = x₂
ẋ₂ = -θ sin(x₁) + (1/mI²)u
```

**Control objective:** Stabilize the pendulum at inverted position (π, 0)

**What the script does:**
1. Implements adaptive control law: u(x₁, x₂, θ̂) = mI²(-c₁(x₁ - π) - c₂x₂ + θ̂ sin(x₁))
2. Uses adaptation law: θ̇̂ = x₂ sin(x₁)
3. Proves stability using Lyapunov function V = x̃ᵀPx̃ + ½(θ̂ - θ)²
4. Simulates system with multiple initial conditions
5. Plots trajectories, states, and parameter estimates

**Output:**
- Four subplots showing:
  - Phase portrait (x₁ vs x₂)
  - Position x₁(t) over time
  - Velocity x₂(t) over time
  - Parameter estimate θ̂(t) over time
- Analysis showing convergence to (π, 0)
- Discussion of why θ̂ may not converge to true θ

**Theoretical results verified:**
- (a) All trajectories are bounded
- (b) The line L = {(x₁, x₂, θ̂) : x₁ = π, x₂ = 0} is a set of equilibria
- (c) All trajectories approach L as t → ∞

### Exercise 3.11: Adaptive Control (Unknown Mass and Inertia)
Extends Exercise 3.10 to the case where both mass and inertia are unknown:
- Unknown parameter θ₁ (related to mass)
- Unknown parameter θ₂ (related to inertia, known to be positive)

**System dynamics:**
```
ẋ₁ = x₂
ẋ₂ = -θ₁ sin(x₁) + θ₂u
```

**What the script does:**
1. Implements adaptive control law: u = (1/θ̂₂)(c₁(x₁ - π) + c₂x₂ + θ̂₁ sin(x₁))
2. Uses adaptation laws:
   - θ̇̂₁ = -x₂ sin(x₁)
   - θ̇̂₂ = -x₂u
3. Uses Lyapunov function V = x̃ᵀPx̃ + ½(θ̂₁ - θ₁)² + ½(θ̂₂ - θ₂)²
4. Simulates with multiple initial conditions
5. Extensive plotting and analysis

**Output:**
- Nine subplots showing:
  - Phase portrait (x₁ vs x₂)
  - Position x₁(t) and velocity x₂(t) over time
  - Parameter estimates θ̂₁(t) and θ̂₂(t) over time
  - Control input u(t)
  - Lyapunov function V(t) (log scale)
  - Parameter trajectory in (θ̂₁, θ̂₂) space
  - State errors (log scale)
- Detailed numerical analysis of convergence
- Discussion of parameter convergence behavior

**Theoretical results verified:**
- (a) All trajectories are bounded (shown by non-increasing V(t))
- (b) L = {(x₁, x₂, θ̂₁, θ̂₂) : x₁ = π, x₂ = 0} is a set of equilibria
- (c) All trajectories approach L as t → ∞

## Key Observations

### Domain of Attraction Estimation (3.9)
- The estimate using Lyapunov level sets is conservative
- Actual domain of attraction may be larger than estimated
- Simulations confirm trajectories converge from points outside estimated domain

### Parameter Convergence (3.10 & 3.11)
- State variables (x₁, x₂) converge to desired equilibrium (π, 0)
- Parameter estimates (θ̂, θ̂₁, θ̂₂) do NOT necessarily converge to true values
- This is due to lack of persistent excitation
- Multiple parameter combinations can maintain equilibrium
- This is a fundamental limitation of adaptive control without sufficient excitation

## Requirements

- MATLAB R2018a or later (for ODE solvers and plotting functions)
- No additional toolboxes required (uses base MATLAB functions)

## Notes

- All scripts include detailed comments explaining the theory
- Figures are generated with high-quality settings for presentations
- Console output provides numerical analysis and verification of theoretical results
- Scripts are self-contained with no external dependencies

