# Qiskit v2.X Developer Certification Prep (C1000-179)

Lecture, practice and mock-exam notebooks for the IBM exam
[C1000-179: Fundamentals of Quantum Computing Using Qiskit v2.X Developer](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400)
(credential: IBM Certified Quantum Computation using Qiskit v2.X Developer – Associate).

The notebooks were written for the Qiskit Advocate KR certification study group. They combine the
group's study notebooks and the QAMP 2025 certification tutorial into one English set that follows the
official objectives and section weights.

## Exam at a glance

68 questions · 90 minutes · pass mark 47 correct (69%) · single-answer and multi-select questions ·
Pearson VUE (test center or online).

| # | Section | Weight | ≈ Questions |
|---|---|---|---|
| 1 | Perform quantum operations | 16% | 11 |
| 2 | Visualize quantum circuits, measurements, and states | 11% | 7 |
| 3 | Create quantum circuits | 18% | 12 |
| 4 | Run quantum circuits | 15% | 10 |
| 5 | Use the sampler primitive | 12% | 8 |
| 6 | Use the estimator primitive | 12% | 8 |
| 7 | Retrieve and analyze the results of quantum circuits | 10% | 7 |
| 8 | Operate with OpenQASM | 6% | 4 |

## Contents

| Notebook | What it covers |
|---|---|
| [01_Perform_Quantum_Operations](01_Perform_Quantum_Operations.ipynb) | Pauli operators, `SparsePauliOp`, `Operator`, gates and phases, circuit mechanics, feature maps |
| [02_Visualize_Circuits_Measurements_States](02_Visualize_Circuits_Measurements_States.ipynb) | `draw()` options, histograms, Bloch / Q-sphere / city / Hinton / Pauli-vector plots, backend plots |
| [03_Create_Quantum_Circuits](03_Create_Quantum_Circuits.ipynb) | Registers and measurement, parameterized circuits, dynamic circuits (`if_test`, `switch`, loops), transpilation |
| [04_Run_Quantum_Circuits](04_Run_Quantum_Circuits.ipynb) | Job / batch / session modes, `QiskitRuntimeService`, ISA circuits, PUBs and broadcasting |
| [05_Use_the_Sampler_Primitive](05_Use_the_Sampler_Primitive.ipynb) | `SamplerV2` PUBs, shots, options (dynamical decoupling, twirling), `BitArray`, do-it-yourself readout mitigation |
| [06_Use_the_Estimator_Primitive](06_Use_the_Estimator_Primitive.ipynb) | `EstimatorV2` PUBs, precision and shots, resilience levels, TREX / ZNE / PEA / PEC, manual ZNE |
| [07_Retrieve_and_Analyze_Results](07_Retrieve_and_Analyze_Results.ipynb) | Job status and monitoring, `service.job()` / `service.jobs()`, sessions, saving results, analysis |
| [08_Operate_with_OpenQASM](08_Operate_with_OpenQASM.ipynb) | OpenQASM 3 structure and types, semantics, `qasm2` / `qasm3` interop, Runtime REST API |
| [09_Final_Check_Mock_Exam_A](09_Final_Check_Mock_Exam_A.ipynb) | Full 68-question mock exam, standard level |
| [10_Final_Check_Mock_Exam_B](10_Final_Check_Mock_Exam_B.ipynb) | Full 68-question mock exam, harder (more code reading and multi-select) |
| [solutions/09_Final_Check_Mock_Exam_A_Solutions](solutions/09_Final_Check_Mock_Exam_A_Solutions.ipynb) | Answer key and explanation for every Mock Exam A question |
| [solutions/10_Final_Check_Mock_Exam_B_Solutions](solutions/10_Final_Check_Mock_Exam_B_Solutions.ipynb) | Answer key and explanation for every Mock Exam B question |

Notebooks 01–08 have lecture parts with runnable examples, 7–8 coding exercises each (with check cells),
and 18–24 exam-style questions each; the answer or solution is folded directly under each item (click
Show answer / Show solution). Notebooks 09–10 are practice exams without answers: questions are shuffled
across sections by the official weights, like the real exam, you record your answers in order, and a
scoring cell grades the attempt at the end. Answers and explanations for the two exams are in the
[solutions](solutions/) folder.

## How to use

1. Work through 01–08 in order. Run the cells top to bottom; in each practice cell replace the `None` /
   `# TODO` parts and run the check cell below it.
2. Take Mock Exam A under exam conditions. Run the Start cell, then answer in order: under each
   question, type your choice in its answer cell (for example `answer(12, "B")`) and run it. When you
   finish, run the scoring cell. It reports the score per section, unanswered questions, and the correct
   letter for each question you missed.
3. Read the explanations in `solutions/09_Final_Check_Mock_Exam_A_Solutions.ipynb`, review the section
   notebooks it points to, then take Mock Exam B and review it the same way.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

On Windows PowerShell, activate the environment with `.venv\Scripts\Activate.ps1`.

Everything runs locally without an IBM Quantum account. Circuits are executed with the Qiskit Runtime
`SamplerV2` / `EstimatorV2` primitives on `AerSimulator` (or `AerSimulator.from_backend(FakeXxx())` when
a device model is needed). Cells that need real hardware or the REST API are guarded and run only when
you add credentials. The gate-map and circuit-layout plots in notebook 02 need the Graphviz system
package (`brew install graphviz` / `apt install graphviz` / `conda install graphviz`).

## Environment

The material is pinned to the exam-era API and is not meant to track the latest Qiskit release.

| Package | Supported range | Tested with |
|---|---|---|
| qiskit | 2.0.x | 2.0.3 |
| qiskit-aer | 0.17.x | 0.17.1, 0.17.2 |
| qiskit-ibm-runtime | 0.40.x | 0.40.1 |
| qiskit-qasm3-import | 0.6.x | 0.6.0 |

Circuit-library circuits use the function forms (`zz_feature_map`, `real_amplitudes`, `efficient_su2`,
`n_local`, `QFTGate`). The class forms (`ZZFeatureMap`, `RealAmplitudes`, …) are pending deprecation in
Qiskit 2.0 and deprecated from 2.1. Each notebook ends with links to the versioned Qiskit 2.0 and
qiskit-ibm-runtime 0.40 API pages. See [TECHNICAL_NOTES.md](TECHNICAL_NOTES.md) for version-sensitive decisions.

## Official resources

- [Exam page, study guide and sample test (C9008400 / C1000-179)](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400)
- [IBM Quantum blog: the Qiskit v2.X developer certification](https://www.ibm.com/quantum/blog/qiskit-v2x-developer-certification)
- [Qiskit video: preparing for the certification](https://www.youtube.com/watch?v=FbSvk2krtSk)
- [IBM Quantum Learning](https://quantum.cloud.ibm.com/learning)
- [IBM Quantum documentation (guides)](https://quantum.cloud.ibm.com/docs/guides)
- [Qiskit SDK 2.0 API reference](https://quantum.cloud.ibm.com/docs/api/qiskit/2.0)
- [qiskit-ibm-runtime 0.40 API reference](https://quantum.cloud.ibm.com/docs/api/qiskit-ibm-runtime/0.40)
- [Local testing mode](https://quantum.cloud.ibm.com/docs/guides/local-testing-mode)
- [Qiskit Aer `AerSimulator`](https://qiskit.github.io/qiskit-aer/stubs/qiskit_aer.AerSimulator.html)
- [Qiskit Runtime REST API reference](https://quantum.cloud.ibm.com/docs/api/qiskit-runtime-rest)
- [OpenQASM 3 specification](https://openqasm.com/language/)

## Community references

When a community example disagrees with the official documentation, trust the Qiskit 2.0 API reference.

### Study groups and tutorials

- [Qiskit Advocate KR: 2026 Qiskit developer certification study](https://github.com/qiskit-community/korean-community/tree/main/2026%20Qiskit%20Advocate%20Qiskit%20%EA%B0%9C%EB%B0%9C%EC%9E%90%20%EC%9E%90%EA%B2%A9%EC%A6%9D%20%EC%8A%A4%ED%84%B0%EB%94%94) — the Korean study notebooks and practice sets this repository is built from.
- [QAMP 2025: qiskit_2x_certification_exam_tutorial](https://github.com/kibrahim757/qiskit_2x_certification_exam_tutorial) — Qiskit Advocate Mentorship Program project with notebooks for all eight sections and a practice test.
- [Hannan0107/Qiskit-Certification-Practice-Notebooks](https://github.com/Hannan0107/Qiskit-Certification-Practice-Notebooks) — day-by-day notebooks with self-check quizzes, derived from the QAMP tutorial.
- [jvscursulim/study-group-qiskit-2.x-certification](https://github.com/jvscursulim/study-group-qiskit-2.x-certification) — weekly study-group notebooks.
- [algovista-collab/qiskit_v2_study_materials](https://github.com/algovista-collab/qiskit_v2_study_materials) — theory and code for the eight sections.
- [MisterSzled/qiskit_flashcodes](https://github.com/MisterSzled/qiskit_flashcodes) — runnable code-snippet flashcards per exam topic.
- [matthewscottconroy/quantum-computing-study-suite](https://github.com/matthewscottconroy/quantum-computing-study-suite) — notebooks, trainer apps and C1000-179 exam practice.
- [qiskit-community/ibm-quantum-challenge-2024](https://github.com/qiskit-community/ibm-quantum-challenge-2024) — IBM Quantum Challenge labs, useful for transpilation and Qiskit Runtime practice.

### Practice exams and quiz tools

- [CertiQ: JanLahmann/qiskit-developer-certification-prep](https://github.com/JanLahmann/qiskit-developer-certification-prep) — machine-readable syllabus checked against the official study guide and an execution-verified question bank.
- [quantum-tokyo/qiskit-certification-prep](https://github.com/quantum-tokyo/qiskit-certification-prep) — Quantum Tokyo community practice questions for the v2.X exam.
- [dorakingx/qisquiz](https://github.com/dorakingx/qisquiz) ([practice site](https://qisquiz.vercel.app/)) — section practice and timed mock exams mapped to the C1000-179 objectives.
- [vantnprof/Qiskit_v2X_Certificate_Practice](https://github.com/vantnprof/Qiskit_v2X_Certificate_Practice) — a 68-question practice exam with collapsible answers.
- [KurianUthuppu/ibm_qiskit_2_x](https://github.com/KurianUthuppu/ibm_qiskit_2_x) — practice exams with solutions.
- [Luke-J-Miller/Qiskit-v2.X-developer-certification-practice-test](https://github.com/Luke-J-Miller/Qiskit-v2.X-developer-certification-practice-test) — large notebook question bank with adaptive study.
- [MrRobert91/QuantumComputingGuide](https://github.com/MrRobert91/QuantumComputingGuide) — interactive lessons and a mock exam.
- [0sophy1/qrabbit-hole](https://github.com/0sophy1/qrabbit-hole) — story-based conversational quiz.

### Sample-test walkthroughs and exam reports

- [Schrodin's Diary: official v2.X sample test explained, part 1](https://schrodinteq.github.io/ibmcertsamplev2x01/) and [part 2](https://schrodinteq.github.io/ibmcertsamplev2x02/)
- [Schrodin's Diary: passing the v2.X exam, experience and study tips](https://schrodinteq.github.io/ibm-cert-quantum-exam-v2x/)

## Contributing

Corrections are welcome through issues and pull requests. For changes to version-sensitive APIs or
mock-exam answers, include a link to the Qiskit 2.0 or qiskit-ibm-runtime 0.40 documentation you used,
and keep the solution notebooks consistent with the answer keys in the scoring cells.

## License
Licensed under the [Apache License 2.0](LICENSE).

## Credits

- Qiskit Advocate KR study group: 박민준 ([@minjoon-park](https://github.com/minjoon-park)), 이권학 ([@snow0369](https://github.com/snow0369)), 김보성 ([@BStar14](https://github.com/BStar14)), 신소영 ([@0sophy1](https://github.com/0sophy1)), 조정빈 ([@dolf3131](https://github.com/dolf3131)), advisor 최인호 ([@q-inho](https://github.com/q-inho)).
- QAMP 2025 tutorial: Karim Ibrahim and Shek Lun Leung, mentored by Muhammad Faryad and Raja Babu Jamatia.

This is a community study aid. It is not affiliated with or endorsed by IBM. Qiskit is a trademark of IBM.
