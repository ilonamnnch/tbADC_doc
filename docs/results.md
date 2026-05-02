# Simulation Results

## VTC Characterization

Using estimated parameters:

\[
t_{delay} = 1\,\mu s/V \cdot (V_{in} - 0.5)
\]

---

## Delay Table

| \(V_{in}\) | \(t_{delay}\) | Code |
|---|---|---|
| 0.5 V | 0 ns | 0 |
| 0.6 V | 100 ns | 20 |
| 0.7 V | 200 ns | 40 |
| 0.8 V | 300 ns | 60 |
| 0.9 V | 400 ns | 80 |
| 1.0 V | 500 ns | 100 |
| 1.1 V | 600 ns | 120 |
| 1.2 V | 700 ns | 140 |
| 1.3 V | 800 ns | 160 |
| 1.4 V | 900 ns | 180 |
| 1.5 V | 1000 ns | 200 |
| 1.6 V | 1100 ns | 220 |
| 1.7 V | 1200 ns | 240 |

---

## Observations

- Linear increase of delay with input voltage
- Monotonic behavior
- Good matching with theoretical model

---

## TDC Matching

The TDC range:

\[
1.275\,\mu s
\]

is compatible with the VTC delay span (~1.2 µs).