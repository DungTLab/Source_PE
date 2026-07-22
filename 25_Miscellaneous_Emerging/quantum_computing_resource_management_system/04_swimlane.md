# Swimlane Diagram — Quantum Computing Resource Management System

## Mermaid Code

```mermaid
flowchart LR
    Start(["Start"])

    subgraph Lane1["Quantum Researcher"]
        R1["Submit OpenQASM Circuit & Shot Count"]
        R2["Select Zero-Noise Error Mitigation"]
        R3["View Quantum Histogram & State Vector"]
    end

    subgraph Lane2["System"]
        S1["Validate OpenQASM Syntax & User Credits"]
        S2["Check Cryogenic Temperature (<20 mK)"]
        S3{"QPU Backend Online & Thermal Safe?"}
        S4["Enqueue Quantum Job for Execution"]
        S5["Apply Zero-Noise Error Mitigation"]
        S6["Deduct Quantum Credits & Post Result"]
    end

    subgraph Lane3["Qiskit Transpiler Engine"]
        T1["Map Logical Qubits to QPU Topology"]
        T2["Insert SWAPs & Decompose Basis Gates"]
    end

    subgraph Lane4["Quantum Processor (QPU)"]
        Q1["Fire Microwave Pulse Waveforms"]
        Q2["Discriminates Readout IQ Voltages to Bits"]
    end

    Finish(["End"])

    Start --> R1 --> S1 --> S3
    S3 -->|"No (Thermal Alert)"| Finish
    S3 -->|"Yes (Online)"| T1 --> T2 --> S4 --> Q1 --> Q2 --> R2 --> S5 --> S6 --> R3 --> Finish
```

## Flow Description | Mô tả luồng

| Lane | Actor | Role in Flow |
|------|-------|-------------|
| 1 | Quantum Researcher | Submits OpenQASM 3.0 quantum circuits via SDK, sets shot counts, selects error mitigation parameters, and visualizes measurement state histograms. |
| 2 | System | Validates circuit syntax and credit balances, verifies cryogenic refrigerator sub-kelvin temperatures (<20 mK), queues jobs, applies error mitigation algorithms, and deducts credits. |
| 3 | Qiskit Transpiler Engine | Maps abstract logical qubits onto physical QPU Heavy-Hex coupling topology graphs, inserts SWAP gates, and decomposes gates into native basis sets (`{RZ, SX, X, ECR}`). |
| 4 | Quantum Processor (QPU) | Converts physical circuits into microsecond microwave pulse waveforms, fires requested shot iterations (8192 shots), and discriminates IQ voltages into measurement bitstrings. |
