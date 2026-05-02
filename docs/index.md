# Time-Based Analog-to-Digital Converter

!!! warning "Ongoing Work"

    This work is currently in progress.

    While the architecture and design have been completed, the characterization phase is still ongoing. Additional simulations are required to fully evaluate the system performance.

    Furthermore, post-silicon measurements have not yet been conducted, as the fabricated chip has not been received.

    This documentation will be updated accordingly once experimental results become available.

## Overview

This work presents the design and analysis of a Time-Based Analog-to-Digital Converter (TB-ADC) implemented in CMOS technology. The proposed architecture converts an analog input voltage into a time interval, which is subsequently digitized.

\[
V_{in} \rightarrow t_{delay} \rightarrow \text{Digital Code}
\]

## Motivation

As CMOS technologies scale, voltage headroom decreases, making conventional voltage-domain ADCs less efficient. Time-based architectures offer an alternative by leveraging:

- Digital-friendly scaling
- Reduced analog complexity
- High resolution through temporal quantization

## Key Features

- Voltage-to-Time conversion using a capacitive discharge mechanism
- Delay-line based Time-to-Digital conversion
- Thermometer encoding followed by digital processing

---

## Global Architecture

The system is composed of three main blocks:

1. Voltage-to-Time Converter (VTC)
2. Time-to-Digital Converter (TDC)
3. Digital Encoding Logic