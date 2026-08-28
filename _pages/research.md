---
permalink: /research/
title: "Research"
author_profile: true
---

My long-term goal is to design quantum computation from the structure of the problem it is
meant to solve. Structure, once written in, propagates. It tells you which parts of a circuit
carry physical meaning, which errors change the answer, and what a calculation should cost.
Building the encoding, the algorithm, the error correction, and the hardware in isolation
discards that information at every boundary.

The projects below sit at different layers of that stack. They are versions of the same
argument rather than separate lines of work.

## Application-Aware Error Correction

Quantum error correction treats every logical error as equally serious. For a scientific
question it is not. A small number of error channels move the quantity a chemist actually asked
for, such as a reaction barrier or a spectral gap, and most do not. This is the direction I
expect to occupy most of the group's attention at Mines.

<figure>
  <img src="/images/ses.svg" alt="A three-qubit circuit above a bar chart of the sensitivity of a target observable to the error on each gate, with two thresholds sorting the gates into tiers.">
  <figcaption>Sensitivity of a target observable to the error on each gate. Two thresholds sort
  the gates into tiers, from the ones that have to be protected to the ones that can be
  dropped.</figcaption>
</figure>

**Scientific error sensitivity.** We define the sensitivity of a target observable to the error
channels that act on it, and summarize how unevenly that sensitivity is distributed in a single
index. The index can be evaluated before any correction budget is committed. Where the
dependence is concentrated, uneven allocation wins. Where it is not, it does not, and the
framework should say so rather than oversell.

**Tiered allocation under a fixed budget.** Once sensitivity is known, correction strength and
measurement shots can be assigned in tiers instead of uniformly. We are working out how much
this buys on realistic chemistry targets, and where the crossover against uniform allocation
sits.

**Benchmarks.** A claim about allocation is only as good as the problems it is tested on. We
are assembling a set of scientific targets with trusted reference values, so that the same
allocation question can be asked across methods rather than tuned per paper.

## Structured Encoding for Molecular Learning

<figure>
  <img src="/images/hse.svg" alt="A molecule is passed through a mean-field calculation to give density and Fock matrices and a three-index cumulant tensor, which set the gate angles of a layered circuit.">
  <figcaption>A molecular Hamiltonian decomposed by body order and written directly into the
  circuit. One-body terms set single-qubit rotations, pair correlations set two-qubit gates, and
  three-body cumulants set the layer above. Only the final block is trainable.</figcaption>
</figure>

**Informed encoding of electronic structure.** Most quantum machine learning models load
molecular data through a feature map chosen for convenience. We write the many-body expansion
into the circuit instead. The gate angles come from cumulants rather than from a fit. Replacing
those angles with random numbers while holding the circuit fixed costs an order of magnitude in
accuracy, which is our evidence that the circuit reads physical content rather than absorbing
arbitrary parameters.

**Body order and the three-body window.** Decomposing the encoding by body order reveals a
window in which three-body terms help and outside which they do not. We want a predictive
account of where that window sits, rather than a report that it exists.

## Noise as a Design Variable

<figure style="max-width:480px;margin-left:auto;margin-right:auto;">
  <img src="/images/noise.svg" alt="Upper panel, performance change of trained models as depolarizing noise increases, split into a group that improves, a group that degrades, and a group that is indifferent. Lower panel, training and validation error against noise level.">
  <figcaption>The upper panel shows models trained on the same molecular data under increasing
  depolarizing noise. One group improves, a smaller group degrades, and about half are
  indifferent. The lower panel shows training and validation error against noise level. Training
  error rises throughout while validation error passes through a minimum, which is the signature
  of noise acting as a regularizer.</figcaption>
</figure>

**When noise improves learning.** Noise is normally treated as damage to be removed. In
training quantum models on molecular data we found that it is not uniformly harmful. Part of
the population converges better at moderate noise, and which part is decided before training
begins. Unstructured encodings make this easy to observe and very hard to predict, which is
part of why we moved toward structured ones.

**Analytic noise decay in structured circuits.** A structured encoding makes noise tractable.
Each layer has a known Pauli weight, so its decay rate under depolarizing noise is known in
advance rather than measured after the fact. We use this to derive thresholds on the noise
level below which the physical content of a layer survives.

## Adaptive Quantum Algorithms

**ADAPT-VQE and ADAPT-QAOA.** These grow a circuit one operator at a time and let the problem
choose its own ansatz. I worked on both during my postdoctoral years at Virginia Tech. The
questions I still care about are the choice of reference state and an honest account of when
adaptivity earns its overhead and when a fixed ansatz would have done as well.

**Measurement cost and shot allocation.** Measurement, not gate count, is often what makes a
variational calculation impractical. We have worked on shot assignment driven by measured
variance, on reinforcement learning agents that adapt allocation during optimization, and on
step size selection for gradient-based optimization under finite shots.
