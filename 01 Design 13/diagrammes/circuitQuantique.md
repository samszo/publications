# Circuit quantique

```mermaid
flowchart LR
    subgraph Q0["qubit 0"]
        direction LR
        R0["Ry(θ₀)"] --> G1a["● CX₁<br/>(control)"] --> M0["M<br/><i>Mesure</i>"]
    end

    subgraph Q1["qubit 1"]
        direction LR
        R1["Ry(θ₁)"] --> G2a["● CX₂<br/>(control)"] --> M1["M<br/><i>Mesure</i>"]
    end

    subgraph Q2["qubit 2"]
        direction LR
        R2["Ry(θ₂)"] --> G1b["⊕ CX₁<br/>(target)"] --> G3a["● CX₃<br/>(control)"] --> M2["M<br/><i>Mesure</i>"]
    end

    subgraph Q3["qubit 3"]
        direction LR
        R3["Ry(θ₃)"] --> G2b["⊕ CX₂<br/>(target)"] --> G3b["⊕ CX₃<br/>(target)"] --> M3["M<br/><i>Mesure</i>"]
    end

    G1a -. "intrication CX₁" .- G1b
    G2a -. "intrication CX₂" .- G2b
    G3a -. "intrication CX₃" .- G3b

    classDef ry fill:#edf2f4,color:#2b2d42,stroke:#8d99ae,stroke-width:1px;
    classDef control fill:#2b2d42,color:#ffffff,stroke:#2b2d42,stroke-width:2px;
    classDef target fill:#8d99ae,color:#ffffff,stroke:#2b2d42,stroke-width:2px;
    classDef mesure fill:#ef233c,color:#ffffff,stroke:#2b2d42,stroke-width:1px;

    class R0,R1,R2,R3 ry;
    class G1a,G2a,G3a control;
    class G1b,G2b,G3b target;
    class M0,M1,M2,M3 mesure;
```

**Légende :**
- **Couche Ry** — rotations paramétrées `Ry(θᵢ)` par qubit (encodent affects & similarités).
- **Couche CX** — intrications (`●` control → `⊕` target) le long des arêtes physiques : CX₁(0→2), CX₂(1→3), CX₃(2→3).
- **Mesure** — lecture finale `M` de chaque qubit.

## Autre proposition — sequenceDiagram

```mermaid
sequenceDiagram
    participant Q0 as qubit 0
    participant Q1 as qubit 1
    participant Q2 as qubit 2
    participant Q3 as qubit 3

    Note over Q0,Q3: Couche Ry (Affects & Similarités)
    Note over Q0: Ry(θ₀)
    Note over Q1: Ry(θ₁)
    Note over Q2: Ry(θ₂)
    Note over Q3: Ry(θ₃)

    Note over Q0,Q3: Couche CX (Intrications le long des arêtes physiques)
    Q0->>Q2: CX₁ (control → target)
    Q1->>Q3: CX₂ (control → target)
    Q2->>Q3: CX₃ (control → target)

    Note over Q0,Q3: Mesure
    Q0->>Q0: M
    Q1->>Q1: M
    Q2->>Q2: M
    Q3->>Q3: M
```
