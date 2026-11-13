# Third-party notices

This repository and its release files contain work by OpenSourceSDRLab together with third-party software. The Apache License 2.0 in [LICENSE](LICENSE) applies **only** to the files created by OpenSourceSDRLab:

- `README.md`, `NOTICE.md`
- `docs/` (Quick Start Guide, pin assignment tables)
- `hardware/` (core module and carrier board schematics, pin assignment workbook)
- `images/`
- the `README.txt` files inside the prebuilt zip files in Releases

All source code in `vivado/` comes from Analog Devices, Xilinx/AMD and other third parties. It keeps its original copyright notices and licences, which have not been changed:

| Component | Files | Owner | Licence |
|---|---|---|---|
| Analog Devices HDL library (snapshot of the `hdl_2021_r1` branch) | `vivado/AD936X/AD936X_PL/library/` | Analog Devices, Inc. | per module, as stated in each file header: dual GPL-2.0 / ADI BSD for most modules; see `LICENSE`, `LICENSE_ADIBSD`, `LICENSE_GPL2` and `LICENSE_LGPL` in `vivado/AD936X/AD936X_PL/` (copied unchanged from the Analog Devices HDL repository) |
| S/PDIF receiver and transmitter cores | `library/axi_spdif_rx/*.vhd`, `library/axi_spdif_tx/tx_*.vhd` | Geir Drange (OpenCores) | LGPL, as stated in each file header |
| Analog Devices HDL project scripts and board files | `vivado/AD936X/AD936X_PL/projects/scripts/`, `projects/common/`, `projects/fmcomms2/common/` | Analog Devices, Inc. | as stated in each file header |
| AD936X project for this board, **modified by OpenSourceSDRLab** (derived from the Analog Devices `fmcomms2/zc702` project) | `vivado/AD936X/AD936X_PL/projects/fmcomms2/zc702/`: `system_top.v`, `system_constr.xdc`, `zc702_system_constr.xdc` (in `projects/common/zc702/`), block design `system.bd` and project file | Analog Devices, Inc.; modifications OpenSourceSDRLab | Analog Devices licence as stated in each file header; the changes retarget the design to the XC7Z020-CLG400 and the FMC LPC pins of this board |
| AD9361 no-OS driver, platform layer and example application, **modified by OpenSourceSDRLab** (application in `src/` adapted to this board; it prints the captured samples on the console) | `vivado/AD936X/AD936X_PS/AD936X/` (all files except `xilinx/no_os_uart.c`) | Analog Devices, Inc. | Analog Devices BSD-style licence, as stated in each file header |
| UART helper of the no-OS platform layer | `vivado/AD936X/AD936X_PS/AD936X/xilinx/no_os_uart.c` | Xilinx, Inc. / AMD | as stated in the file header |
| Xilinx/AMD IP cores, block designs and generated files | `.bd`, `.xci`, `.xsa` files in `vivado/`, and the Xilinx parts of the prebuilt `.bit`, `.xsa`, `fsbl.elf` and `BOOT.bin` in Releases | Xilinx, Inc. / AMD | Xilinx/AMD licence terms |
| Peripheral test applications (Vitis templates: Hello World, Zynq DRAM diagnostics, lwIP echo server, USB mass-storage example; `helloworld.c` **modified by OpenSourceSDRLab** to print in a loop) | `vivado/Peripheral_Test/XC7Z020_PS/*/src/` | Xilinx, Inc. / AMD | as stated in each file header |
| lwIP TCP/IP stack (compiled into `LWIP_ECHO_Test.elf` in Releases) | Releases only | Swedish Institute of Computer Science and lwIP contributors | BSD-3-Clause |

The prebuilt bitstreams, FSBLs and applications in Releases are built from the sources above and are covered by the same third-party licences. The AD936X bitstream contains Analog Devices HDL modules; Analog Devices allows distributing bit files built from its HDL under the ADI BSD licence (see `LICENSE` in `vivado/AD936X/AD936X_PL/`).

Software that is **not** included and must be obtained from AMD:

- Vivado and Vitis 2021.1: <https://www.xilinx.com/support/download.html>

"Analog Devices", "AD9361", "FMCOMMS2", "Xilinx", "AMD", "Zynq", "Vivado" and "Vitis" are trademarks of their respective owners. They are used here only to describe compatibility and do not imply endorsement.
