---
permalink: /research/tomorrow/
title: '<span class="qm-title qm-title--next">Science for Tomorrow’s Qubits</span>'
author_profile: true
---

<nav class="dirnav dirnav--next" aria-label="Research directions">
  <a href="/research/">← Research</a>
  <span class="dirnav__eyebrow">Next · fault-tolerant machines</span>
  <a class="dirnav__other" href="/research/today/">Today’s Qubits for Science →</a>
</nav>

Fault-tolerant machines will spend most of their qubits and time on error correction. Standard
practice protects every operation equally. For a scientific question that is wasteful. A small
number of error channels move the quantity a chemist actually asked for, such as a reaction
barrier or a spectral gap, and most do not. Here the science decides where the protection goes.
This is the direction I expect to occupy most of my group's attention.

<figure class="bigpicture">
  <a href="/images/big-picture.png" title="Open at full size"><img src="/images/big-picture.png" alt="Six steps from a molecular Hamiltonian to predicted chemical properties: many-body Hamiltonian encoding, quantum circuit mapping, observable sensitivity analysis, application-aware error correction, error-mitigated or fault-tolerant execution, and prediction, joined by a co-design feedback loop."></a>
  <figcaption>The whole pipeline, from a molecular Hamiltonian to a predicted property. Encoding
  and circuit design (1, 2) are the work on <a href="/research/today/">today’s devices</a>.
  Sensitivity analysis and application-aware error correction (3, 4) are the work on this page.
  Execution (5) and prediction (6) are where the two meet, and the feedback loop runs the whole
  way round. Click to open at full size.</figcaption>
</figure>

<div class="students students--2"><strong>For students.</strong> This side starts from how quantum error correction works, with the repetition code and the surface code. You learn how a circuit is compiled for a fault-tolerant machine, how to estimate the qubits and the time a calculation needs, and how to set an error budget from what the answer is sensitive to.</div>

<h2 id="ses">Application-aware error correction</h2>

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

**AQRC.** The application-aware quantum resource compiler turns sensitivity into a protection
plan. It takes a molecular Hamiltonian, a state-preparation circuit and an accuracy target on an
observable. From the sensitivity of that observable to each type of Pauli error, on each logical
qubit and at each step, it chooses a code distance for each logical qubit and a synthesis
precision for each rotation. The output is a protection specification for downstream compilers
and resource estimators. The hardware model sits behind one interface, so the same analysis
runs for architectures with transversal gates. On the first test systems, LiH and an H4 chain at
chemical accuracy and a physical error rate of 10⁻³, the distances come out uniform. That is
what the framework should report when the sensitivity is spread out. Stating the accuracy target
on the energy still matters. For LiH it cuts the runtime estimated by the Azure Quantum Resource
Estimator by about 40 percent.

[code and research note](https://github.com/Linghua-Zhu/application-aware-quantum-resource-compiler)

<div class="directions directions--foot">
  <a class="direction direction--1" href="/research/today/">
    <p class="direction__eyebrow">Now · noisy devices</p>
    <p class="direction__title">Today’s Qubits for Science →</p>
    <p class="direction__text">The other direction. Algorithms built for the hardware we have.</p>
  </a>
</div>
