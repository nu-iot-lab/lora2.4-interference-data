# lora2.4-interference-data

Raw logs from experiments measuring LoRa (SX1280, 2.4 GHz) performance under WiFi interference (DSSS and OFDM => IEEE 802.11 ch13/14). Each log includes LoRa transceiver configuration, register dump, and timestamped packet reception stats: RSSI, SNR, CRC, IRQ, packet count, and error count.

---

## Log Format

Each log begins with:

- LoRa hardware and radio parameters (modulation, frequency, bandwidth, coding rate)
- Full 0x900–0x9F0 register memory dump

Followed by timestamped packet entries:

```
65s  56 C5 ... F6 | CRC 6B92 | RSSI -72dBm | SNR 3dB | Length 16 | Packets 3 | Errors 0 | IRQreg 8012
```

Errors are marked explicitly:

```
67s PacketError, RSSI, -76dBm, SNR, -7dB, ..., IRQ_CRC_ERROR
```

---

## Device Placement

The LoRa receiver remained fixed. The WiFi transmitter was placed at:

- 5 cm
- 0.5 m
- 1 m
- 2 m
- 3 m

WiFi interference was generated using beacon-only AP + STA on ch13 (OFDM) or ch14 (DSSS). LoRa operated on 2479 MHz. See [exp_setup.pdf](setup) for full layout.

