Understanding Metric Spaces Through Distance Functions

A Real Analysis course project exploring how different distance functions on the plane **R²** define different metric spaces, and how the choice of metric changes the geometry and topology of the space.

**Guide:** Dr. G. D. Veerappa Gowda

**Team:**
- Anvi Patchigolla
- Prajnaa M
- Nitin Sailapathi
- Harshil Pansala
- Mohan Pritam K
- Srikar Nandagiri
- Aditya Gupta

---

## Overview

A metric space is a pair `(X, d)` where `X` is a non-empty set and `d : X × X → R` satisfies, for all `x, y, z ∈ X`:

1. **Non-negativity:** `d(x, y) ≥ 0`
2. **Identity of indiscernibles:** `d(x, y) = 0 ⇔ x = y`
3. **Symmetry:** `d(x, y) = d(y, x)`
4. **Triangle inequality:** `d(x, z) ≤ d(x, y) + d(y, z)`

This project defines three metrics on R², proves each one satisfies all four axioms, compares them through worked examples and unit-ball plots, and analyzes how each affects topological properties.

## The Three Metrics

| Metric | Name | Formula |
|--------|------|---------|
| `d₂` | Euclidean | `√((x₁ − y₁)² + (x₂ − y₂)²)` |
| `d₁` | Taxicab (Manhattan) | `\|x₁ − y₁\| + \|x₂ − y₂\|` |
| `d₀` | Discrete | `0` if `x = y`, otherwise `1` |

## Worked Example

Distance between `P = (1, 2)` and `Q = (4, 6)`:

| Metric | Distance |
|--------|----------|
| Euclidean (`d₂`) | 5 |
| Taxicab (`d₁`) | 7 |
| Discrete (`d₀`) | 1 |

## Unit Balls

The unit ball `{x : d(x, 0) ≤ 1}` looks different under each metric:

- **Euclidean:** a circle
- **Taxicab:** a diamond (a square rotated 45°)
- **Discrete:** a single point, `{0}`

## Topological Comparison

| Property | Euclidean | Taxicab | Discrete |
|----------|-----------|---------|----------|
| Open sets | Usual open sets | Same as Euclidean | Every subset is open |
| Connectedness | Connected and path-connected | Connected and path-connected | Totally disconnected (only single points are connected) |
| Convergence | Usual convergence | Same as Euclidean | Only eventually constant sequences converge |
| Compactness | Closed and bounded sets | Same as Euclidean | Exactly the finite sets |

**Key takeaway:** the Euclidean and taxicab metrics induce the **same topology**, while the discrete metric induces a much finer one.

## Real-Life Applications

The companion document (`Applications.pdf`) shows where "distance" appears outside pure mathematics:

- **Physical distance and navigation:** GPS, Google Maps, air vs. road vs. railway distance
- **Computer and data science:** k-nearest neighbors, image recognition, spam detection, using Euclidean, Manhattan, Minkowski, cosine, Hamming, Jaccard and other distances
- **Social networks:** degrees of separation and graph shortest paths
- **Internet and networks:** router hop counts and routing algorithms
- **Biology and medicine:** comparing DNA sequences, genetic similarity, medical images
- **Economics and finance:** similarity of price patterns, stock similarity, risk comparison
- **Recommendation systems:** Netflix and Spotify preference similarity

> A metric space is any situation where "distance" makes sense, even if it's not physical distance.

## Repository Contents

```
.
├── README.md                    # This file
├── Real_Analysis_Project.pdf    # Full report: definitions, proofs, examples, topology analysis
├── Applications.pdf             # Real-life applications of metric spaces
└── unit_balls.py                # Plotting code (see below)
```

## Running the Plotting Code

Requirements: Python 3, `numpy`, `matplotlib`.

```bash
pip install numpy matplotlib
python unit_balls.py
```

Save the following as `unit_balls.py`:

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(-1.5, 1.5, 400)
y = np.linspace(-1.5, 1.5, 400)
X, Y = np.meshgrid(x, y)

euclid = np.sqrt(X**2 + Y**2)
taxicab = np.abs(X) + np.abs(Y)

plt.figure(figsize=(15, 4))

plt.subplot(1, 3, 1)
plt.contour(X, Y, euclid, levels=[1])
plt.title("Unit Ball: Euclidean Metric")
plt.xlabel("x")
plt.ylabel("y")
plt.gca().set_aspect("equal")

plt.subplot(1, 3, 2)
plt.contour(X, Y, taxicab, levels=[1])
plt.title("Unit Ball: Taxicab Metric")
plt.xlabel("x")
plt.ylabel("y")
plt.gca().set_aspect("equal")

plt.subplot(1, 3, 3)
plt.scatter(0, 0, color="black")
plt.title("Unit Ball: Discrete Metric (only {0})")
plt.xlabel("x")
plt.ylabel("y")
plt.gca().set_aspect("equal")
plt.xlim(-1.5, 1.5)
plt.ylim(-1.5, 1.5)

plt.show()
```

## References

1. W. Rudin, *Principles of Mathematical Analysis*. McGraw-Hill, 1976.
2. R. Bartle and D. Sherbert, *Introduction to Real Analysis*. Wiley, 2011.
