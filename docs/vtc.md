# Voltage-to-Time Converter (VTC)

## Operating Principle

The VTC converts an input voltage into a delay using a controlled discharge mechanism.

---

## VTC Simplified Architecture

<div class="mermaid">
flowchart LR

    %% ===== MAIN PATH =====
    Vin([Vin]) --> SW[Sampling Switch]
    SW --> CAP((VN))
    CAP --> COMP{{Comparator}}
    COMP --> BUF[Buffer Chain]
    BUF --> OUT([vtc_out])

    %% ===== ANALOG PART =====
    CAP --> C0[C0]
    C0 --> GND1[gnd]

    CAP --> DIS[Discharge Current]
    DIS --> GND2[gnd]

    %% ===== THRESHOLD =====
    Thr([Vthr]) --> COMP

    %% ===== STYLE =====
    classDef analog fill:#f8f9fa,stroke:#333,stroke-width:1px;
    classDef digital fill:#e3f2fd,stroke:#1e88e5,stroke-width:1px;
    classDef node fill:#fff3e0,stroke:#fb8c00,stroke-width:1px;

    class Vin,OUT digital;
    class SW,COMP,BUF digital;
    class CAP node;
    class C0,DIS analog;
</div>
## Phases of Operation

### Sampling Phase

When the tracking signal is active:

\[
V_N = V_{in}
\]

---

### Conversion Phase

Once the tracking phase ends, the capacitor discharges:

\[
\frac{dV_N}{dt} = -\frac{I}{C}
\]

---

### Threshold Detection

The comparator triggers when:

\[
V_N(t) = V_{thr}
\]

Solving:

\[
t_{delay} = \frac{C}{I} (V_{in} - V_{thr})
\]

---

## Parameter Values

- \(C = 1\,pF\)
- \(I = 1\,\mu A\)

\[
\frac{C}{I} = 1\,\mu s/V
\]

---

## Key Result

\[
t_{delay} \approx 1\,\mu s/V \cdot (V_{in} - 0.5)
\]

---

## Interpretation

- Higher input voltage → longer delay
- Linear conversion behavior
- Simple analog implementation

---

## Limitations

- Current non-idealities
- Capacitor variation
- Comparator offset
- Noise and jitter