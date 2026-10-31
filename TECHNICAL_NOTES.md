# Technical notes

## Version baseline

| Package | Supported range | Tested with |
|---|---|---|
| qiskit | 2.0.x | 2.0.3 |
| qiskit-aer | 0.17.x | 0.17.1, 0.17.2 |
| qiskit-ibm-runtime | 0.40.x | 0.40.1 |
| qiskit-qasm3-import | 0.6.x | 0.6.0 |

The original material records end-to-end execution on this stack. Stored lecture outputs come from
that earlier run. The difficulty revision described below changes lesson navigation and question text;
it does not represent a new end-to-end execution of all lecture and exercise cells.

## Version-sensitive decisions

- Circuits run with the Qiskit Runtime `SamplerV2` and `EstimatorV2` primitives on `AerSimulator`,
  or on `AerSimulator.from_backend(FakeXxx())` when a device model is needed.
- `StatevectorSampler` / `StatevectorEstimator` are not used in the lecture code, exercises or questions
  (notebook 05 mentions once that such reference primitives exist).
- Fake backends are used only as device models (targets, coupling maps, layouts, gate maps) and in the one
  example where a Runtime primitive rejects a non-ISA circuit in local testing mode (`IBMInputValueError`).
- Runtime features added after qiskit-ibm-runtime 0.40 (the Executor primitive, the 0.48 deprecations,
  the client-side Sampler/Estimator of 0.50) are excluded.
- Circuit-library circuits use the function forms; the class forms are pending deprecation in Qiskit 2.0.
- The REST example sends `IBM-API-Version: 2024-01-01`, the value qiskit-ibm-runtime 0.40.1 sends.
- Each notebook ends with versioned API references (Qiskit 2.0, qiskit-ibm-runtime 0.40).

## Difficulty and curriculum revision

Both mocks retain 68 questions and the section allocation 11/7/12/10/8/8/7/5. A emphasizes foundations;
B is a second standard set with short application questions. These are editorial difficulty choices,
not a measured equivalence to IBM's live exam. The advice to require 80% on both mocks has been removed.

A has 25 revised question stems and B has 40. Multi-select items decreased from 10 to 7 in A and from
13 to 4 in B; the revised multi-select questions all ask for two answers. Unchanged applied questions
retain some moderate challenge. The displayed 47/68 threshold is a practice reference, not a prediction
that a learner will pass the live exam.

The revision replaces many exact timeout/default-value questions, internal representation details,
and compound multidimensional shape puzzles with core workflows. Basic broadcasting, DD, twirling,
resilience levels, ZNE, OpenQASM and REST remain in scope. Question numbering, answer-entry cells,
embedded scoring keys, solution stems, answer tables and explanations are kept in sync.

All eight lessons were compared with the official study guide's 21 objectives. No whole objective
needed to be removed or added. The main issue was priority: custom implementations and API edge cases
appeared alongside first-pass work. Lessons now mark 42 coding exercises as core and 15 as optional,
with visible skip/resume links and `study-core` / `study-optional` cell tags. Twenty of the 175 review
questions are marked as deeper practice. Optional is a learning order, not a guarantee of exam exclusion.
The lecture code, existing outputs and figures are preserved.

### Public examples inspected

The revision uses public examples to compare question length, topic selection and one-task-at-a-time
structure. Replacement wording and explanations are original; no question bank is imported. Community
answers are not treated as authoritative when they conflict with the pinned IBM APIs.

- [Quantum Tokyo: execution questions](https://github.com/quantum-tokyo/qiskit-certification-prep/blob/98fbb42a19cd54bd4439dfdcf0efb2f56cbdb393/src/sec4_run-quantum-circuit.ipynb),
  [Sampler/Estimator](https://github.com/quantum-tokyo/qiskit-certification-prep/blob/98fbb42a19cd54bd4439dfdcf0efb2f56cbdb393/src/sec5-6_sampler-estimator.ipynb), and
  [results](https://github.com/quantum-tokyo/qiskit-certification-prep/blob/98fbb42a19cd54bd4439dfdcf0efb2f56cbdb393/src/sec7_retrieve-and-analyze.ipynb)
  (Apache-2.0): concise mode selection, primitive options, and result retrieval questions.
- [QAMP 2025 Practice Test 1](https://github.com/kibrahim757/qiskit_2x_certification_exam_tutorial/blob/acd983ab59c7dc6d56174769a5a3d696fe06bc4f/Test_Samples/Practice_Test_1.ipynb):
  comparisons of gates, circuit composition, visualization choice and parameter use. Some examples
  contain ambiguous choices or older API assumptions; their answer keys were not copied.
- [Muhammad Faryad's practice exam](https://github.com/muf148/qiskit-practice-exam/blob/main/index.html)
  (CC0-1.0): inspected the question bank's short workflow and result-reading formats. Its stated
  Qiskit 2.5 / Runtime 0.48 baseline differs from this repository's baseline.
- IBM's public C1000-179 sample and study guide, reached from the [official certification page](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400),
  remain the primary coverage/style references. The sample itself cautions that its score does not
  predict performance on the complete exam.

### Validation scope

The revision checks notebook schemas and Python syntax, question numbering, answer/solution agreement,
section counts, attachment references and internal navigation. Scoring is exercised for blank and
perfect attempts, the 46/47 pass boundary, answer normalization, and partial multi-select answers.
Selected new code-dependent questions are executed on Qiskit 2.0.3, Aer 0.17.2 and Runtime 0.40.1.
Hardware-service facts use the cited IBM documentation rather than live paid QPU jobs. This is not a
claim that every retained question or all 57 exercise solutions were re-executed during this revision.

## References

- [Official certification page](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400)
- [Qiskit SDK 2.0 API](https://quantum.cloud.ibm.com/docs/api/qiskit/2.0)
- [qiskit-ibm-runtime 0.40 API](https://quantum.cloud.ibm.com/docs/api/qiskit-ibm-runtime/0.40)
- [Local testing mode](https://quantum.cloud.ibm.com/docs/guides/local-testing-mode)
- [Qiskit Aer `AerSimulator`](https://qiskit.github.io/qiskit-aer/stubs/qiskit_aer.AerSimulator.html)
