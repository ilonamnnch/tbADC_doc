# System-Level Analysis

## Global Transfer Function

Combining VTC and TDC:

\[
N = \frac{t_{delay}}{t_{cell}} = \frac{C}{I \cdot t_{cell}} (V_{in} - V_{thr})
\]

---

## Gain

\[
K = \frac{C}{I \cdot t_{cell}} = \frac{1\,\mu s/V}{5ns} = 200
\]

---

## Digital Output

\[
D_{out} = 200 \cdot (V_{in} - 0.5)
\]

---

## Voltage Resolution

\[
LSB_V = \frac{t_{cell}}{C/I}
\]

\[
LSB_V = \frac{5ns}{1\,\mu s/V} = 5mV
\]

---

## Effective Resolution

\[
N_{bits} = \log_2(255) \approx 8\,bits
\]

---

## Interpretation

The ADC behaves as a linear voltage-to-code converter.

---

## Advantages

- Scalable architecture
- Low analog complexity
- High resolution potential