<p><a href="https://www.opensourcesdrlab.com"><img src="images/OpenSourceSDRLab-banner.jpg" alt="OpenSourceSDRLab" width="100%"></a></p>

# ZYNQ7020-FMC

Schematics, pin assignment, Vivado reference designs and prebuilt files for the **OpenSourceSDRLab ZYNQ7020-FMC** development board: a Xilinx/AMD Zynq-7000 XC7Z020 core module on a carrier board with an FMC LPC connector, Gigabit Ethernet, USB OTG, microSD and USB-UART.

## Product link

Compatible AD9361 FMC card used by the AD936X reference design: [OpenSourceSDRLab FMC-936X](https://opensourcesdrlab.com/products/opensourcesdrlab-fmc-936x-high-quality-development-board-card-with-lpc-interface-replacement-for-fmcomms2)

## About the board

- Core module: Xilinx/AMD Zynq-7000 **XC7Z020-2CLG400I** (dual-core Arm Cortex-A9 + Artix-7 class logic), **1 GB DDR3** (2 × MT41K256M16, 32-bit), **32 MB quad-SPI flash** (W25Q256JV), 33.333 MHz PS clock, connected to the carrier through two 120-pin board-to-board connectors
- Carrier board (V1.1):
  - **FMC LPC** connector (34 LA differential pairs on PL banks 34 and 35)
  - **Gigabit Ethernet**: RTL8211F PHY (RGMII on PS MIO) and RJ45 jack
  - **USB 2.0 OTG**: USB3320C ULPI PHY, USB Type-C
  - **USB-UART**: CH340E, USB Type-C (PS UART1, console)
  - **microSD** card slot (PS SD0) and a 2-position **boot-mode switch** (SD / QSPI / JTAG)
  - **JTAG** header, 26-pin **2.54 mm expansion header** (20 I/O on PL bank 13), reset button
  - **12 V DC** input
- Reference designs: Vivado / Vitis **2021.1**, bare-metal (no OS)
  - **AD936X**: Analog Devices HDL and no-OS AD9361 design for an FMCOMMS2-compatible AD9361 card on the FMC LPC connector
  - **Peripheral test**: Hello World, DDR3 diagnostics, lwIP Ethernet echo server, USB device example

## Quick start

1. Download `ZYNQ7020-FMC_Peripheral-Test_prebuilt_Vivado2021.1.zip` from the [Releases](../../releases) page and copy its `BOOT.bin` to a FAT32 microSD card.
2. Set both boot-mode switches to **OFF** (SD boot), insert the card, connect the USB-UART port to your PC and open a serial terminal at **115200 baud**.
3. Power the board from 12 V. The console prints `Hello World` every half second.

The full steps, including the AD936X design and rebuilding from source, are in the **[Quick Start Guide](docs/Quick-Start-Guide.md)** ([PDF](docs/Quick-Start-Guide.pdf)).

## Repository layout

| Path | Contents |
|---|---|
| `hardware/` | Core module schematic, carrier board schematic (PDF) and pin assignment (`.xlsx`) |
| `docs/` | Quick Start Guide (Markdown and PDF), pin assignment tables (`Pinout.md`) |
| `vivado/AD936X/AD936X_PL/` | Analog Devices HDL library and the `fmcomms2` project adapted to this board (`projects/fmcomms2/zc702/zc702.xpr`) |
| `vivado/AD936X/AD936X_PS/` | Bare-metal AD9361 application sources (Analog Devices no-OS) and the exported hardware `system_top.xsa` |
| `vivado/Peripheral_Test/XC7Z020_PL/` | Vivado project of the peripheral test design (Zynq PS configuration for this board) |
| `vivado/Peripheral_Test/XC7Z020_PS/` | Application sources (Hello World, DDR test, lwIP echo, USB example) and the exported hardware `design_1_wrapper.xsa` |
| `images/` | OpenSourceSDRLab banner and logo |

## Downloads (Releases)

Prebuilt files are attached to the [Releases](../../releases) page instead of being stored in the repository:

| File | Contents |
|---|---|
| `ZYNQ7020-FMC_AD936X_prebuilt_Vivado2021.1.zip` | AD936X design: bitstream, `.xsa`, FSBL, application `.elf` and SD-card `BOOT.bin` |
| `ZYNQ7020-FMC_Peripheral-Test_prebuilt_Vivado2021.1.zip` | Peripheral test design: bitstream, `.xsa`, FSBL, four application `.elf` files and SD-card `BOOT.bin` (Hello World) |
| `SHA256SUMS.txt` | SHA-256 checksums of the files above |

Check a download with `shasum -a 256 -c SHA256SUMS.txt` (macOS / Linux) or `certutil -hashfile <file> SHA256` (Windows).

## Licence

Files created by OpenSourceSDRLab are released under the [Apache License 2.0](LICENSE). The reference designs are built on code from Analog Devices, Xilinx/AMD and the lwIP project, which remains under its own licences; see [NOTICE.md](NOTICE.md).

## Support

- Email: support@opensourcesdrlab.com
- Forum: <https://forum.opensourcesdrlab.com>
- Discord: <https://discord.gg/nnxY6DkmvT>
- Blog and user manuals: <https://blog.opensourcesdrlab.com>

---
<sub>© 2026 OpenSourceSDRLab. All rights reserved. · <a href="https://www.opensourcesdrlab.com">www.opensourcesdrlab.com</a></sub>
