# Technical notes

## Version baseline

| Package | Supported range | Tested with |
|---|---|---|
| qiskit | 2.0.x | 2.0.3 |
| qiskit-aer | 0.17.x | 0.17.1, 0.17.2 |
| qiskit-ibm-runtime | 0.40.x | 0.40.1 |
| qiskit-qasm3-import | 0.6.x | 0.6.0 |

All notebooks were executed end to end on this stack. Stored outputs come from that run.

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

## How answers were checked

Every answer that depends on code behaviour, a number, a shape, a default value or an option path was
checked by running it on the stack above; this includes all 136 mock-exam questions. The answers in the
solution notebooks match the answer keys used by the scoring cells of the practice exams. Runtime service behaviour
that cannot run locally was checked against the qiskit-ibm-runtime 0.40.1 source and the IBM Quantum
documentation of that period.

## References

- [Official certification page](https://www.ibm.com/training/certification/ibm-certified-quantum-computation-using-qiskit-v2x-developer-associate-C9008400)
- [Qiskit SDK 2.0 API](https://quantum.cloud.ibm.com/docs/api/qiskit/2.0)
- [qiskit-ibm-runtime 0.40 API](https://quantum.cloud.ibm.com/docs/api/qiskit-ibm-runtime/0.40)
- [Local testing mode](https://quantum.cloud.ibm.com/docs/guides/local-testing-mode)
- [Qiskit Aer `AerSimulator`](https://qiskit.github.io/qiskit-aer/stubs/qiskit_aer.AerSimulator.html)
