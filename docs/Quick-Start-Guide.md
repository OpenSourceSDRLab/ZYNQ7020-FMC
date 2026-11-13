---
title: ZYNQ7020-FMC Quick Start Guide
product: ZYNQ7020-FMC
doc_id: OSSDRLAB-ZYNQ7020-FMC-QSG
version: 1.0
date: 2026-11-12
repo: https://github.com/OpenSourceSDRLab/ZYNQ7020-FMC
---

<!-- ossl:header -->
<p><a href="https://www.opensourcesdrlab.com"><img src="../images/OpenSourceSDRLab-banner.jpg" alt="OpenSourceSDRLab" width="100%"></a></p>

# ZYNQ7020-FMC Quick Start Guide

| Product | Document | Version | Date |
|---|---|---|---|
| ZYNQ7020-FMC | OSSDRLAB-ZYNQ7020-FMC-QSG | 1.0 | 2026-11-12 |
<!-- /ossl:header -->

## 1. Overview

The ZYNQ7020-FMC is a Zynq-7000 development board made of two parts:

- a **core module** with the Xilinx/AMD XC7Z020-2CLG400I, 1 GB of DDR3 memory and 32 MB of quad-SPI flash;
- a **carrier board** with an FMC LPC connector, Gigabit Ethernet, USB 2.0 OTG, USB-UART, microSD, JTAG and a 2.54 mm expansion header.

This guide shows how to boot the board, run the peripheral tests, use the AD936X reference design with an AD9361 FMC card, and rebuild the designs from the sources in this repository.

## 2. What you need

| Item | Notes |
|---|---|
| ZYNQ7020-FMC board | core module fitted on the carrier board |
| 12 V DC power adapter | 5.5 × 2.1 mm barrel plug |
| USB Type-C cable | for the USB-UART console port |
| microSD card | any size, formatted FAT32 |
| Ethernet cable | for the lwIP echo test |
| JTAG cable | Xilinx-compatible JTAG cable, only for running programs from Vitis |
| AD9361 FMC card | for the AD936X design, for example the OpenSourceSDRLab [FMC-936X](https://opensourcesdrlab.com/products/opensourcesdrlab-fmc-936x-high-quality-development-board-card-with-lpc-interface-replacement-for-fmcomms2) |
| PC | a serial terminal program; Vivado and Vitis **2021.1** from AMD to rebuild the designs: <https://www.xilinx.com/support/download.html> |
| Prebuilt files | `ZYNQ7020-FMC_Peripheral-Test_prebuilt_Vivado2021.1.zip` and `ZYNQ7020-FMC_AD936X_prebuilt_Vivado2021.1.zip` from the [Releases](../../../releases) page |

The USB-UART bridge is a CH340E. Windows 10/11, Linux and macOS normally install its driver automatically.

## 3. Board interfaces

| Interface | Details |
|---|---|
| Power | 12 V DC input jack |
| FMC LPC | 34 LA differential pairs on PL banks 34 and 35, FMC I2C and JTAG |
| Gigabit Ethernet | RTL8211F PHY on PS MIO 16–27 (RGMII), MDIO on MIO 52–53, RJ45 jack |
| USB 2.0 OTG | USB3320C ULPI PHY on PS MIO 28–39, reset on MIO 46, USB Type-C |
| USB-UART (console) | CH340E on PS UART1 (MIO 48 TX, MIO 49 RX), USB Type-C |
| microSD | PS SD0 on MIO 40–45 |
| Quad-SPI flash | W25Q256JV (32 MB) on MIO 1–6 |
| Boot-mode switch | 2-position switch on MIO 4 and MIO 5, see section 4 |
| JTAG | 2.54 mm header; pin order on sheet 6 of the carrier schematic |
| Expansion header | 26-pin 2.54 mm header: 20 I/O on PL bank 13, 5 V, 3.3 V, GND |
| Reset | push button on PS_POR_B, MAX809 supervisor |

Full pin lists: [Pinout.md](../docs/Pinout.md) and `hardware/ZYNQ7020-FMC_Pinout.xlsx`. Schematics: `hardware/ZYNQ7020-FMC_Core-Module_Schematic.pdf` and `hardware/ZYNQ7020-FMC_Carrier_Schematic.pdf`.

## 4. Boot-mode switch

The two switch positions pull MIO 4 and MIO 5 to ground when they are **ON**. With both OFF the board boots from the microSD card.

| Boot source | Switch 1 (MIO 4) | Switch 2 (MIO 5) |
|---|---|---|
| microSD card | OFF | OFF |
| Quad-SPI flash | ON | OFF |
| JTAG | ON | ON |

> **Tip:** the switch numbers above follow the schematic (switch 1 = pins 1–4 on MIO 4). If the boot source does not match, check the silkscreen next to the switch.

## 5. First power-on: Hello World from the microSD card

1. Unzip `ZYNQ7020-FMC_Peripheral-Test_prebuilt_Vivado2021.1.zip`.
2. Copy `BOOT.bin` to the root of the FAT32 microSD card and insert the card.
3. Set the boot-mode switch to **microSD** (both OFF).
4. Connect the USB-UART port to the PC and open its serial port at **115200 baud, 8 data bits, no parity, 1 stop bit**.
5. Connect the 12 V supply. The console prints `Hello World` every 0.5 seconds.

Press the reset button to restart the program.

## 6. Other peripheral tests (JTAG)

The other test programs are run from Vitis over JTAG:

1. Set the boot-mode switch to **JTAG** (both ON), connect the JTAG cable and power on.
2. In Vitis 2021.1, create a platform project from `design_1_wrapper.xsa` (in the repository or in the prebuilt zip).
3. Program the FPGA with `design_1_wrapper.bit`, then download and run one of the `.elf` files (or build it from the sources, see section 8):

| Program | What it does |
|---|---|
| `Hello_World.elf` | prints `Hello World` on the console every 0.5 s |
| `DDR_Test.elf` | Zynq DRAM diagnostics: shows a menu on the console for a memory test and read/write eye measurements |
| `LWIP_ECHO_Test.elf` | TCP echo server on the Gigabit Ethernet port. The board uses the static address `192.168.1.10`; set your PC to an address in `192.168.1.x` and connect to TCP port **7** (for example `telnet 192.168.1.10 7`). Every line you type is sent back. |
| `xusbps_intr_example_1.elf` | USB device example: connect the USB OTG port to the PC and the board appears as a small USB mass-storage device |

To run a program without the JTAG cable, build a `BOOT.bin` with bootgen from `fsbl.elf`, `design_1_wrapper.bit` and the `.elf`, and copy it to the microSD card.

## 7. AD936X reference design with an AD9361 FMC card

The AD936X design is the Analog Devices `fmcomms2` HDL reference design and the Analog Devices no-OS AD9361 driver, adapted to the ZYNQ7020-FMC. It works with an FMC card that follows the Analog Devices AD-FMCOMMS2 pinout, such as the OpenSourceSDRLab FMC-936X.

1. With the power off, fit the AD9361 card on the **FMC LPC** connector and connect the antennas or cables to its SMA ports.
2. Unzip `ZYNQ7020-FMC_AD936X_prebuilt_Vivado2021.1.zip` and copy its `BOOT.bin` to the microSD card.
3. Set the boot-mode switch to **microSD**, open the serial console at 115200 baud and power on.
4. The application initialises the AD9361 (2 RX / 2 TX, LVDS interface, 1 GHz RX and TX local oscillators, 40 MHz reference clock), starts the transmit DMA with a test waveform, captures a receive buffer into DDR memory and prints the captured samples on the console as lines of the form `ADC1_I=…,ADC1_Q=…,ADC2_I=…,ADC2_Q=…`.

The radio settings are in `vivado/AD936X/AD936X_PS/AD936X/src/main.c` (`default_init_param`). The example options (DMA examples, IIO support) are selected in `src/app_config.h`.

## 8. Reference designs in this repository

| Folder | Contents |
|---|---|
| `vivado/AD936X/AD936X_PL/library/` | Analog Devices HDL IP library (`hdl_2021_r1`), with the packaged IP definitions the project needs |
| `vivado/AD936X/AD936X_PL/projects/fmcomms2/zc702/` | Vivado project `zc702.xpr`. The folder keeps the name of the Analog Devices ZC702 reference project it was derived from; it targets the XC7Z020-CLG400-2 of this board, with the pin constraints of the FMC LPC connector |
| `vivado/AD936X/AD936X_PS/` | `system_top.xsa` and the application sources in `AD936X/` (`src/`, `ad9361/`, `AXI_Core/`, `iio/`, `api/`, `util/`, `include/`, `xilinx/`) |
| `vivado/Peripheral_Test/XC7Z020_PL/` | Vivado project `XC7Z020_PL.xpr` (Zynq processing system configured for this board) |
| `vivado/Peripheral_Test/XC7Z020_PS/` | `design_1_wrapper.xsa` and the `src/` folders of the four test applications |

### Rebuilding the AD936X design

1. Open `vivado/AD936X/AD936X_PL/projects/fmcomms2/zc702/zc702.xpr` in Vivado 2021.1. The project finds the Analog Devices IP in `../../../library`.
2. Run **Generate Bitstream**, then **File › Export › Export Hardware** (include the bitstream).
3. In Vitis 2021.1, create a platform project from the exported `.xsa` (standalone, `ps7_cortexa9_0`), then an empty C application.
4. Copy the folders from `vivado/AD936X/AD936X_PS/AD936X/` into the application, add each folder to the include paths, use `src/lscript.ld` as the linker script, and build.

If Vivado reports missing or locked Analog Devices IP, rebuild the IP library with the Analog Devices HDL make flow (`make` in the `library` folder, see the Analog Devices HDL documentation: <https://wiki.analog.com/resources/fpga/docs/build>).

### Rebuilding the peripheral tests

1. Open `vivado/Peripheral_Test/XC7Z020_PL/XC7Z020_PL.xpr`, generate the block design wrapper if Vivado asks for it, generate the bitstream and export the hardware.
2. In Vitis, create a platform from the `.xsa`. For the lwIP test, enable the `lwip211` library in the board support package.
3. Create one application per test from the matching Vitis template (Hello World, Zynq DRAM tests, lwIP Echo Server, empty application for the USB example) and replace its `src/` folder with the one from this repository.

## 9. Support

- Email: support@opensourcesdrlab.com
- Forum: <https://forum.opensourcesdrlab.com>
- Discord: <https://discord.gg/nnxY6DkmvT>
- Blog and user manuals: <https://blog.opensourcesdrlab.com>

<!-- ossl:footer -->
---
<sub>© 2026 OpenSourceSDRLab. All rights reserved. · <a href="https://www.opensourcesdrlab.com">www.opensourcesdrlab.com</a></sub>
<!-- /ossl:footer -->
