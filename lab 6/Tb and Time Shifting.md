### 1. Purpose of `ask_time`, `fsk_time`, `psk_time`

These variables are used as the **time axis (x-axis)** for plotting signals.

They store the exact time values for each sample of the generated signal.

---

| Variable | Meaning                    |
| -------- | -------------------------- |
| ask_time | Time values for ASK signal |
| fsk_time | Time values for FSK signal |
| psk_time | Time values for PSK signal |

---

### 3. How plotting works

```matlab
plot(ask_time, ask_signal)
```

* x-axis → time (`ask_time`)
* y-axis → signal amplitude (`ask_signal`)

---

### 4. Why time shifting is used

```matlab
t_bit + (i-1)*Tb
```

This ensures:

* Each bit is placed in its correct time slot
* Signals do not overlap
* A continuous waveform is formed

---

### 5. Key concept

* Without time arrays → all bits overlap at same time (wrong)
* With time arrays → bits appear sequentially in time (correct)

---

The time arrays are used as the x-axis to place each modulated bit signal in its correct time position, forming a proper continuous digital transmission waveform.
---

**Tb (Bit Duration):**
Tb is the time required to transmit one bit in a digital communication system. It defines how long each bit stays on the time axis.

In MATLAB,

```matlab
Tb = 1;
```

means each bit duration is 1 second.

---

**Time Shifting:**
Time shifting is used to place each bit signal in its correct time position so that signals do not overlap.

In code:

```matlab
t_bit + (i-1)*Tb
```

This shifts each bit by Tb so that:

* 1st bit → 0 to Tb
* 2nd bit → Tb to 2Tb
* 3rd bit → 2Tb to 3Tb

---


Tb defines the duration of each bit, and time shifting arranges all bits sequentially on the time axis to form a continuous waveform.
