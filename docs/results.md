# Results and Discussion

## Overview

This section presents a first-order evaluation of the Time-Based ADC based on analytical estimations derived from the design parameters.

At this stage, the fabricated chip has not yet been received, therefore the results rely on schematic-level assumptions and theoretical analysis. The objective is to verify the coherence of the architecture and evaluate its expected performance.

---

## VTC Delay Estimation

The VTC generates a delay according to:

\[
t_{delay} = \frac{C}{I}(V_{in} - V_{thr})
\]

Using the design target:

| Parameter | Value |
|----------|------|
| Capacitance \(C\) | 100 fF |
| Discharge current \(I\) | 100 nA |
| Comparator threshold \(V_{thr}\) | 0.5 V |

The voltage-to-time gain becomes:

\[
\frac{C}{I} = \frac{100 \times 10^{-15}}{100 \times 10^{-9}} = 1\,\mu s/V
\]

Thus:

\[
t_{delay} = 1\,\mu s/V \cdot (V_{in} - 0.5)
\]

---

## Expected VTC Behavior

| \(V_{in}\) | \(V_{in}-V_{thr}\) | Delay |
|----------|-------------------|-------|
| 0.6 V | 0.1 V | 0.1 µs |
| 0.8 V | 0.3 V | 0.3 µs |
| 1.0 V | 0.5 V | 0.5 µs |
| 1.2 V | 0.7 V | 0.7 µs |
| 1.4 V | 0.9 V | 0.9 µs |
| 1.5 V | 1.0 V | 1.0 µs |

The delay varies linearly with the input voltage, confirming the expected behavior of the VTC.

---

## TDC Dynamic Range

The TDC is implemented with:

- 255 delay cells  
- \( t_{cell} \approx 5\,ns \)

The full-scale range is:

\[
T_{FS} = 255 \cdot 5\,ns = 1.275\,\mu s
\]

This range is well matched to the VTC delay span (~1 µs).

---

## ADC Code Estimation

The output code is given by:

\[
D_{out} = \frac{t_{delay}}{t_{cell}}
\]

Using:

\[
t_{cell} = 5\,ns
\]

we obtain:

| \(V_{in}\) | \(t_{delay}\) | Code |
|----------|--------------|------|
| 0.6 V | 0.1 µs | 20 |
| 0.8 V | 0.3 µs | 60 |
| 1.0 V | 0.5 µs | 100 |
| 1.2 V | 0.7 µs | 140 |
| 1.4 V | 0.9 µs | 180 |
| 1.5 V | 1.0 µs | 200 |

---

## Global Transfer Function

Combining VTC and TDC:

\[
D_{out} = \frac{C}{I \cdot t_{cell}}(V_{in} - V_{thr})
\]

\[
D_{out} = \frac{1\,\mu s/V}{5\,ns}(V_{in} - 0.5)
\]

\[
D_{out} = 200 \cdot (V_{in} - 0.5)
\]

---

## Resolution

The effective voltage resolution is:

\[
LSB_V = \frac{t_{cell}}{C/I}
\]

\[
LSB_V = \frac{5\,ns}{1\,\mu s/V} = 5\,mV
\]

The equivalent number of bits is:

\[
N_{bits} \approx \log_2(200) \approx 7.6\,bits
\]

This corresponds to a near 8-bit resolution.

---

## Interpretation

The optimized VTC now generates delays that fully span the TDC range. This ensures that:

- the delay line is efficiently used  
- the quantization is uniform  
- the ADC achieves a high effective resolution  

The system exhibits a linear mapping:

\[
V_{in} \rightarrow t_{delay} \rightarrow D_{out}
\]

---

## Key Insight

The performance of a Time-Based ADC is primarily determined by the ratio:

\[
\frac{C}{I}
\]

By tuning this parameter, the VTC delay can be matched to the TDC range, which is essential to maximize resolution.

---

## Limitations

The current results are based on first-order estimations and do not include:

- transistor non-linearities  
- mismatch effects  
- parasitic capacitances  
- comparator offset  
- timing jitter  

These effects will impact the final performance.

---

## Future Work

Further validation requires:

- transient simulations of the full system  
- Monte Carlo analysis  
- PVT corner evaluation  
- post-layout extraction  
- silicon measurements  

---

## Conclusion

The analytical results demonstrate that, with the optimized current level, the VTC and TDC are properly matched.

This allows the ADC to achieve:

- a wide dynamic range  
- a linear transfer function  
- an effective resolution close to 8 bits  

The next step is to validate these predictions through simulation and experimental characterization once the fabricated chip becomes available.