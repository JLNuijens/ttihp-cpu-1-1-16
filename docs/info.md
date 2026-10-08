# ONE CPU 1.1 16 · 1.6 Gbit/s

Same CPU as ONE CPU 1.1 32. 32 bases. The rise inside is still 1.6 GB/s. This one is the line off the chip.

Jane Street asked for a protocol after fabrication, not a UART block next to an SPI block. The map pin is the connector.

| map `ui[4:3]` | range `ui[7:5]` | line |
|---|---|---|
| `00` | the bit time | UART on `uo[0]`. 100 Mbit/s at count 1 |
| `01` | the bit time | SPI. MOSI `uo[4]`, SCLK `uo[5]`, CS `uo[6]`, MISO `ui[2]` |
| `10` | the bit time | I2C. SCL `uo[4]`, SDA `uio[0]` |
| `11` | `000` | eight wires. `uo[7:0]` holds the mix for the clock. 400 Mbit/s |
| `11` | `111` | sixteen wires. Rise is the mix. Fall is the swapped mix. `uio` is the invert. 1.6 Gbit/s |
| `11` | `001`–`110` | the same walks as the UART chip: JTAG, Manchester, SWD, PS/2, USB, CAN |

FIRE is `ui[0]`. HOT is `ui[1]`. The byte is `uio[7:0]` until the sixteen-wire plug drives those pads.

The mix is the eight bits that already reach a pad on the UART chip. Copying them onto sixteen wires does not add a site.
