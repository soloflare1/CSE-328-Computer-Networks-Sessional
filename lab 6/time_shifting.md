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
