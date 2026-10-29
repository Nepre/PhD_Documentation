# Research Direction

## Parts of a PhD dissertation

We're going to follow the example by Prof. Chris Clack, at least on this first round.

<http://www0.cs.ucl.ac.uk/staff/c.clack/phd.html>

### Abstract

### 1. Introduction

> Set the scene and *problem statement*. Introduce structure of thesis, state contributions (3-5).

#### Limitations \& Contributions 

| Limitation of existing systems | Provisional Contribution |
| -------- | -------- |
| Shallow ~1m deep | 3~4m deep |
| 1 layer | 3~4 Material Layer |
| Struggles with large amount of requests | Request spacing & large amount handling |
| Transient deformation | Persistent Deformation |


#### Visual example:


Example of the existing limitations: <https://www.youtube.com/watch?v=Y3rM49Z6gas>

![Holes on the ground (height comparison)](Images%5CHoles1.png)

![Holes on the ground (stamp showcase)](Images%5CHoles2.png)

The wholes on the ground are made via a stamp, so we can see the the pattern on the ground.
#### Expected challenges:

- Saving large textures (high memory cost) that cover the world at a reasonable pixel density.

- The more layers, the more memory cost.

- Handling large amount of requests require compute power.

#### Scope and out-of-scope

There are many options that can bring this system to a tipping point in terms of scale. 

We are going to focus on:
*In scope:*

- Open Worlds (\~1km2 )
- 3\~4 Material Layers
- 3\~4m Deep
- Deterministic

*Out-of-scope*

- Simulated

- Volume keeping

*In consideration*

- Multiplayer replication

### 2. Background

> Demonstrate wider appreciation (context). Provide *motivation*. The problem statement and the motivation state how you want the PhD to be judged - as engineering, scientific method, theory, philosophy, &c.

Context is a bit difficult to show, but the idea is to further study technologies I am already familiar with and I believe can provide better experience for users and developers.

Usually this technology is very bespoke to games, and not integrated whatsoever in commercial engines.

This will be an engineering PhD where a system will be created to solve these issues.

### 3. Related Work

> Survey and critical assessment. Relation to own work.

Literature Review. Check current systems and related technologies.

### 4-6. Analysis, design, implementation and interpretation of results

This is the main research plan for now.

2. Research Objective: Breakdown of goals and metrics. Come up with research plan.

3. Analysis, design and implementation:

   - Prototype & Benchmark

   - Data Structures, System & Pipeline

   - Optimizing & Scaling

     - Create performance targets

4. Expected Outcomes (Critical Assessment)

   - Comparison to closest rival

   - Further work remaining

   - Expansion possibilities

   - Engine integrations

5. Evaluation

   - Performance

   - Fidelity

   - Scalability

During the development testing is very necessary to make point 7. easier when we get there.

Create a testing framework that tests both functionality and collects system data.

### 7. Critical assessment of own work

> State hypothesis, and demonstrate precision, thoroughness, contribution, and comparison with closest rival.

A real-time multi-layer terrain deformation system for open worlds.

Review the systems developed:

- Create charts with how the performance has been improving and whether we've hit targets.

- Check functionality: does it accomplish all the targets?

- Compare to other existing systems.

### 8. Further Work

The idea is to finish all the targets that we have, but this will be the section where all the potential improvements and out-of-scope elements go.

### 9. Summary Conclusions

### Appendix

   - Data Structures, System & Pipeline 