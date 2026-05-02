# Time-to-Digital Converter (TDC)

## Principle

The TDC converts a time delay into a digital code using a delay line.

---

## Architecture

- Chain of delay cells
- START signal propagates
- STOP signal samples the chain

---

## Thermometer Encoding

The output is:

\[
000000111111111
\]

---

## Time Quantization

\[
t_{delay} = N \cdot t_{cell}
\]

---

## Parameters

- Number of cells: 255
- Delay per cell: 5 ns

---

## Full Scale Range

\[
T_{FS} = 255 \cdot 5ns = 1.275\,\mu s
\]

---

## Resolution

\[
t_{cell} = 5ns
\]

---

## Limitations

- Delay mismatch
- Process variation
- Metastability