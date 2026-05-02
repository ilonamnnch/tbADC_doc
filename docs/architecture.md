# System Architecture

## Conversion Principle

The TB-ADC performs conversion in two stages:

1. Analog-to-Time conversion
2. Time-to-Digital quantization

\[
V_{in} \xrightarrow{\text{VTC}} t_{delay} \xrightarrow{\text{TDC}} D_{out}
\]

---

## Signal Flow

- The input voltage is sampled
- A delay proportional to the input is generated
- This delay propagates through a delay line
- A thermometer code is produced
- The code is converted to binary

---

## Key Design Parameters

| Parameter | Value |
|----------|------|
| Supply Voltage | 1.8 V |
| Threshold Voltage \(V_{thr}\) | 0.5 V |
| VTC Capacitance | 1 pF |
| Discharge Current | 1 µA |
| TDC Cells | 255 |
| Delay per Cell | 5 ns |

---

## Design Insight

The architecture shifts complexity from the analog domain to the time domain, enabling better scalability and robustness in advanced CMOS nodes.