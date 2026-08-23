# Interceptor Guidance and Control: A Gap Analysis

**How rigorously does the learning-based interceptor guidance literature validate its own results?**

Evidence base: **57 papers (2021-2026) read in full text**, plus 54 indexed journal papers held in reserve.

## Why this exists

Reading a research literature leaves you with an impression. Impressions are cheap and hard to argue with.

I wanted a number instead. So rather than summarising what the field claims, I scored every paper against thirteen dimensions of engineering realism, concrete checkable properties that determine whether a guidance law would survive contact with hardware. The result is a coverage matrix rather than a narrative, and it says something the narrative does not.

## The coverage matrix

| Dimension of engineering realism | Papers | Share |
| --- | --- | --- |
| Genuinely maneuvering target | 20 | 35% |
| Monte Carlo statistical validation | 18 | 32% |
| Estimator or measurement noise in the loop | 14 | 25% |
| Fully coupled 3D engagement | 10 | 18% |
| Seeker FOV enforced as a hard constraint | 7 | 12% |
| Input saturation embedded in synthesis, not clipped | 7 | 12% |
| Computation time measured on a real processor | 6 | 11% |
| Autopilot / actuator dynamics inside the stability proof | 3 | 5% |
| Flight test (all counter-drone, below 15 m/s) | 3 | 5% |
| Six-degree-of-freedom airframe simulation | 2 | 4% |
| Guarantee covering a learned component | 1 | 2% |
| Communication delay / packet loss modelled | 0 of 15 cooperative | 0% |
| Hardware-in-the-loop | 0 | 0% |

Read the bottom of that table rather than the top. **No paper in the corpus reports hardware-in-the-loop validation.** Two run 6-DOF simulation. Three include autopilot dynamics inside the stability proof they claim.

## Three structural findings

**1. Constraint-handling and estimation-aware papers are effectively disjoint communities.** Papers that take field-of-view and input saturation seriously assume perfect knowledge of the relative state. Papers that take estimation seriously impose no path constraints. Almost nobody works in the intersection, which is where the real problem lives.

**2. The cooperative subfield has a uniform blind spot.** Across all 15 cooperative-guidance papers: no communication imperfection modelled anywhere, and no look-angle bound enforced in any of them. A salvo coordination scheme that assumes a perfect network is solving a different problem from the one it names.

**3. Cross-paper comparison is currently impossible.** The validation ceiling is low and baselines are demonstrably handicapped. There is no shared benchmark, so reported improvements are not comparable between papers.

## Five evidenced gaps

**G1. Constrained guidance under estimated target state.** The novelty is the closed loop, not either half of it. The field-of-view constraint shapes the lead angle; the lead angle shapes the bearing-rate history; the bearing-rate history determines target-state observability; observability feeds back into the command. That is a dual-control problem hiding inside a constrained-guidance problem, and no paper in the corpus formulates it as one.

**G2. No validation or certification path for learned guidance.** Zero HIL, zero flight test, zero sim-to-real anywhere in the learning literature.

**G3. FOV constraints inside cooperative salvo guidance.** 0 of 15 papers.

**G4. Cooperative salvo against maneuvering targets over non-ideal communication.** The best-evidenced gap: 6 of the 15 cooperative papers name it as their own future work.

**G5. No shared benchmark, and handicapped baselines.**

## What I would do about it

**Paper 1.** Systematic review of learning-based interceptor guidance on a three-axis taxonomy: method class, problem class, validation maturity. The validation maturity ladder is the headline contribution.

**Paper 2.** Observability-Aware Field-of-View and Input Constrained Guidance Against a Maneuvering Target. Simulation only, planar, point-mass, minimum 1,000 Monte Carlo runs, three comparators.

## Method, and where it is weak

Papers were selected for full-text reading from a larger indexed set and scored against each dimension by direct inspection of the modelling assumptions, not the abstract. A paper counts as enforcing a constraint only if the constraint appears in the synthesis, not if it is applied afterwards by clipping.

Known weaknesses, stated plainly:

- The corpus skews open-access. 54 indexed journal papers remain unread, and that is this analysis's main limitation.
- - Scoring was done by one reader. There is no inter-rater reliability check.
  - - Absence of a dimension in a paper is recorded as absence, but some authors may treat it as out of scope rather than overlooked.
   
    - I would rather publish the matrix with these caveats attached than wait until it is unimpeachable. Anyone who disagrees with a specific score can check it against the paper.
   
    - ## Related
   
    - A companion systematic review, Deep Reinforcement Learning for Spacecraft Thermal Control, 61 primary studies, PRISMA-style protocol over 284 records, applies the same validation-maturity lens to a different field.
   
    - Hady Hesham | hadyheasham115@gmail.com | [github.com/HadyMekawi](https://github.com/HadyMekawi)
    - 
