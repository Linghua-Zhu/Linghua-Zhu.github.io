---
permalink: /research/today/
title: '<span class="qm-title qm-title--now">Today’s Qubits for Science</span>'
author_profile: true
---

<nav class="dirnav dirnav--now" aria-label="Research directions">
  <a href="/research/">← Research</a>
  <span class="dirnav__eyebrow">Now · noisy devices</span>
  <a class="dirnav__other" href="/research/tomorrow/">Science for Tomorrow’s Qubits →</a>
</nav>

Today's devices have a limited number of noisy qubits and no error correction. An algorithm has
to fit inside that budget and still produce a number that means something to a chemist. Every
result is checked against a classical method.

<div class="students students--1"><strong>For students.</strong> This side builds on the basics of quantum computing. You learn how molecular data and Hamiltonians are written into circuits, how variational algorithms are built and trained, what noise does to them, how error mitigation works, and why measurement often costs more than the gates. You also learn to compare a quantum result with a classical one fairly.</div>

<h2 id="encoding">Structured encoding for molecular learning</h2>

<figure>
  <img src="/images/hse.svg" alt="A molecule passes through one Hartree-Fock calculation. Principal minors of its density matrix, of size one, two and three, set the angles of single-, two- and three-qubit gate layers, followed by a trainable block.">
  <figcaption>One Hartree-Fock calculation written directly into the circuit. Layer k takes the
  k × k principal minors of the orthogonalized density matrix. The one-index layer, together
  with the diagonal of the Fock matrix, sets single-qubit rotations. The two-index layer sets
  two-qubit gates, and the three-index layer sets three-qubit gates. Only the final block is
  trainable.</figcaption>
</figure>

**Informed encoding of electronic structure.** Most quantum machine learning models load
molecular data through a feature map chosen for convenience. We write electronic structure into
the circuit instead. Each qubit stands for one valence atomic orbital, and the gate angles come
from a single Hartree-Fock calculation rather than from a fit. Replacing the three-index angles
with random or shuffled values, while the circuit stays fixed, makes the predictions clearly
worse. This is our evidence that the circuit reads physical content rather than absorbing
arbitrary parameters.

<h2 id="noise">Noise as a design variable</h2>

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

*APL Computational Physics 2, 030901 (2026).*
[arXiv](https://arxiv.org/abs/2601.13275) ·
[code](https://github.com/Linghua-Zhu/Quantum-Noise-QGNN)

<h2 id="adaptive">Adaptive algorithms and measurement cost</h2>

**ADAPT-VQE and ADAPT-QAOA.** These grow a circuit one operator at a time and let the problem
choose its own ansatz. I worked on both during my postdoctoral years at Virginia Tech. The
questions I still care about are the choice of reference state and an honest account of when
adaptivity earns its overhead and when a fixed ansatz would have done as well.

*Physical Review Research 4, 033029 (2022).*
[arXiv:2203.12757](https://arxiv.org/abs/2203.12757)

**Measurement cost and shot allocation.** Measurement, not gate count, is often what makes a
variational calculation impractical. We have worked on shot assignment driven by measured
variance, on reinforcement learning agents that adapt allocation during optimization, and on
step size selection for gradient-based optimization under finite shots.

*Journal of Chemical Theory and Computation 20, 2390 (2024). Chemical Physics Reviews 5,
041403 (2024). APL Computational Physics 1, 026110 (2025).*
[code](https://github.com/Linghua-Zhu/RL-Quantum-Measurement-Optimization)

<div class="directions directions--foot">
  <a class="direction direction--2" href="/research/tomorrow/">
    <p class="direction__eyebrow">Next · fault-tolerant machines</p>
    <p class="direction__title">Science for Tomorrow’s Qubits →</p>
    <p class="direction__text">The other direction. The science decides where error correction goes.</p>
  </a>
</div>
