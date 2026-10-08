# ONE CPU 1.1 16 · 1.6 Gbit/s

The other version of ONE CPU 1.1 32. Not a second UART block.

Jane Street asked for one machine that can be a protocol after the chip is made. The plug is the width. The CPU is the same 32 bases. The inside stays 1.6 GB/s. Sixteen wires is as fast as this package can go.

| You connect | Pads | Off the chip |
|---|---|---|
| One wire. Map `00` | `uo[0]` | UART, 100 Mbit/s |
| SPI. Map `01` | `uo[6:4]`, `ui[2]` | the SPI walk |
| I2C. Map `10` | `uo[4]`, `uio[0]` | the I2C walk |
| Eight wires. Map `11`, range `000` | `uo[7:0]` | the mix, one byte a rise, 400 Mbit/s |
| Sixteen wires. Map `11`, range `111` | `uo[7:0]` and `uio[7:0]` | both edges, 1.6 Gbit/s |

The sixteen-wire line is the eight-bit mix on the rise, the swapped mix on the fall, and the invert on `uio`. No new site. The 1.6 GB/s does not fit on the pads.

The UART that already built stays in [ttihp-cpu-1-1-uart](https://github.com/JLNuijens/ttihp-cpu-1-1-uart). This repo is the line.

Joshua Luke Nuijens / Axiom 1 Technology, LLC. Apache-2.0.

`tiles: 6x4`. `top_module: tt_um_jlnuijens_one11_16`. Clock 50 MHz.
