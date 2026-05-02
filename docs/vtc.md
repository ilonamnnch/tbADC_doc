# Voltage-to-Time Converter (VTC)

## Overview

The Voltage-to-Time Converter (VTC) is the core analog block of the Time-Based ADC. Its function is to convert an input voltage \( V_{in} \) into a time delay \( t_{delay} \), which is then quantized by the Time-to-Digital Converter (TDC).

\[
V_{in} \rightarrow t_{delay}
\]

---

## Architecture

The VTC is based on a sample-and-hold mechanism followed by a controlled discharge of a capacitive node.

<div class="mermaid">
flowchart LR
    Vin([Vin]) --> SW[Sampling Switch]
    SW --> CAP((VN))
    CAP --> COMP{{Comparator}}
    COMP --> BUF[Buffer Chain]
    BUF --> OUT([vtc_out])

    CAP --> C0[C0]
    C0 --> GND1[gnd]

    CAP --> DIS[Current Mirror Discharge]
    DIS --> GND2[gnd]

    Thr([Vthr]) --> COMP
</div>

---

## Operating Principle

### Sampling Phase

During the tracking phase, the capacitor is charged to the input voltage:

\[
V_N(t_0) = V_{in}
\]

---

### Conversion Phase

After sampling, the node \( V_N \) is disconnected from the input and discharges through a controlled current source.

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
t_{delay} = \frac{C}{I}(V_{in} - V_{thr})
\]

---

## Design Parameters

The VTC is implemented with the following parameters:

| Parameter | Value |
|----------|------|
| Capacitance \( C \) | 100 fF |
| Channel length (sampling devices) | 4 µm |
| Substrate resistance | 50 Ω |
| Current mirror NMOS \(W/L\) | 720 nm / 360 nm |

---

## Design Target

To ensure efficient use of the TDC dynamic range, the VTC is designed to generate delays on the order of microseconds.

This is achieved by reducing the discharge current to:

\[
I \approx 100\,nA
\]

---

## Voltage-to-Time Gain

Using:

- \( C = 100\,fF \)
- \( I = 100\,nA \)

\[
\frac{C}{I} = \frac{100 \times 10^{-15}}{100 \times 10^{-9}} = 1\,\mu s/V
\]

Thus:

\[
t_{delay} = 1\,\mu s/V \cdot (V_{in} - V_{thr})
\]

---

## Expected Behavior

Assuming \( V_{thr} = 0.5\,V \):

| \(V_{in}\) | Delay |
|----------|-------|
| 0.6 V | 0.1 µs |
| 0.8 V | 0.3 µs |
| 1.0 V | 0.5 µs |
| 1.2 V | 0.7 µs |
| 1.4 V | 0.9 µs |
| 1.5 V | 1.0 µs |

---

## Interpretation

- The delay varies linearly with the input voltage  
- Higher input voltage results in longer discharge time  
- The conversion gain is directly controlled by \( C/I \)  

The chosen parameters allow the VTC to fully exploit the dynamic range of the TDC.

---

## Impact of Design Choices

### Capacitance

- Larger \( C \) → longer delay → improved resolution  
- Smaller \( C \) → faster conversion → lower power  

---

### Current Mirror

- Lower current → larger delay → higher resolution  
- Higher current → shorter delay → reduced resolution  

---

### Device Dimensions

- Long-channel devices improve current stability  
- Proper \( W/L \) sizing ensures accurate current mirroring  

---

## Non-Ideal Effects

The VTC performance is affected by several non-idealities:

- Current mirror mismatch  
- Capacitor variation  
- Comparator offset  
- Thermal noise  
- Substrate coupling (not negligible due to 50 Ω resistance)  

---

## Key Insight

The VTC implements a linear mapping:

\[
t_{delay} \propto V_{in}
\]

By properly tuning the ratio \( C/I \), the delay range can be matched to the TDC resolution, enabling efficient time-domain quantization.

---

## Conclusion

The designed VTC provides:

- A linear voltage-to-time conversion  
- A tunable gain through \( C \) and \( I \)  
- A delay range compatible with the TDC  

With the optimized current level, the VTC enables microsecond-scale delays, ensuring that the full TDC dynamic range is utilized and allowing the overall ADC to achieve near 8-bit resolution.