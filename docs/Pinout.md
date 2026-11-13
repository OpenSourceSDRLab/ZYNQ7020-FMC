# ZYNQ7020-FMC pin assignment

Pin assignment of the ZYNQ7020 core module on the ZYNQ7020-FMC carrier (device XC7Z020-2CLG400). The same tables are in `hardware/ZYNQ7020-FMC_Pinout.xlsx`.

## ZYNQ7020 PS MIO assignment

| FPGA pin | MIO | Function |
|---|---|---|
| E6 | PS_MIO0 | — |
| A7 | PS_MIO1 | QSPI_CS |
| B8 | PS_MIO2 | QSPI_D0 |
| D6 | PS_MIO3 | QSPI_D1 |
| B7 | PS_MIO4 | QSPI_D2 / BOOT_MODE0 |
| A6 | PS_MIO5 | QSPI_D3 / BOOT_MODE1 |
| A5 | PS_MIO6 | QSPI_SCK |
| D8 | PS_MIO7 | — |
| D5 | PS_MIO8 | — |
| B5 | PS_MIO9 | — |
| E9 | PS_MIO10 | — |
| C6 | PS_MIO11 | — |
| D9 | PS_MIO12 | — |
| E8 | PS_MIO13 | — |
| C5 | PS_MIO14 | — |
| C8 | PS_MIO15 | — |
| A19 | PS_MIO16 | PHY_TXCK |
| E14 | PS_MIO17 | PHY_TXD0 |
| B18 | PS_MIO18 | PHY_TXD1 |
| D10 | PS_MIO19 | PHY_TXD2 |
| A17 | PS_MIO20 | PHY_TXD3 |
| F14 | PS_MIO21 | PHY_TXCTL |
| B17 | PS_MIO22 | PHY_RXCK |
| D11 | PS_MIO23 | PHY_RXD0 |
| A16 | PS_MIO24 | PHY_RXD1 |
| F15 | PS_MIO25 | PHY_RXD2 |
| A15 | PS_MIO26 | PHY_RXD3 |
| D13 | PS_MIO27 | PHY_RXCTL |
| C16 | PS_MIO28 | OTG_DATA4 |
| C13 | PS_MIO29 | OTG_DIR |
| C15 | PS_MIO30 | OTG_STP |
| E16 | PS_MIO31 | OTG_NXT |
| A14 | PS_MIO32 | OTG_DATA0 |
| D15 | PS_MIO33 | OTG_DATA1 |
| A12 | PS_MIO34 | OTG_DATA2 |
| F12 | PS_MIO35 | OTG_DATA3 |
| A11 | PS_MIO36 | OTG_CLK |
| A10 | PS_MIO37 | OTG_DATA5 |
| E13 | PS_MIO38 | OTG_DATA6 |
| C18 | PS_MIO39 | OTG_DATA7 |
| D14 | PS_MIO40 | SD_CLK |
| C17 | PS_MIO41 | SD_CMD |
| E12 | PS_MIO42 | SD_D0 |
| A9 | PS_MIO43 | SD_D1 |
| F13 | PS_MIO44 | SD_D2 |
| B15 | PS_MIO45 | SD_D3 |
| D16 | PS_MIO46 | OTG_RESETN |
| B14 | PS_MIO47 | — |
| B12 | PS_MIO48 | UART_TX |
| C12 | PS_MIO49 | UART_RX |
| B13 | PS_MIO50 | — |
| B9 | PS_MIO51 | — |
| C10 | PS_MIO52 | PHY_MDC |
| C11 | PS_MIO53 | PHY_MDIO |

## 2.54 mm expansion header (26 pins, PL bank 13)

| FPGA pin | Header pin | Signal / bank |
|---|---|---|
| — | 1 | GND |
| — | 2 | VCC5V |
| W10 | 3 | IO13_L16_P / BANK 13 |
| W9 | 4 | IO13_L16_N / BANK 13 |
| Y9 | 5 | IO13_L14_P / BANK 13 |
| Y8 | 6 | IO13_L14_N / BANK 13 |
| W11 | 7 | IO13_L18_P / BANK 13 |
| Y11 | 8 | IO13_L18_N / BANK 13 |
| U9 | 9 | IO13_L17_P / BANK 13 |
| U8 | 10 | IO13_L17_N / BANK 13 |
| Y7 | 11 | IO13_L13_P / BANK 13 |
| Y6 | 12 | IO13_L13_N / BANK 13 |
| V8 | 13 | IO13_L15_P / BANK 13 |
| W8 | 14 | IO13_L15_N / BANK 13 |
| V11 | 15 | IO13_L21_P / BANK 13 |
| V10 | 16 | IO13_L21_N / BANK 13 |
| Y12 | 17 | IO13_L20_P / BANK 13 |
| Y13 | 18 | IO13_L20_N / BANK 13 |
| T9 | 19 | IO13_L12_P / BANK 13 |
| U10 | 20 | IO13_L12_N / BANK 13 |
| V6 | 21 | IO13_L22_P / BANK 13 |
| W6 | 22 | IO13_L22_N / BANK 13 |
| — | 23 | GND |
| — | 24 | GND |
| — | 25 | VCC3V3 |
| — | 26 | VCC3V3 |

## FMC LPC connector (LA pairs, PL banks 34/35)

| FPGA pin | FMC signal | FMC pin |
|---|---|---|
| L16 | FMC_LA00_CC_P | G6 |
| L17 | FMC_LA00_CC_N | G7 |
| U18 | FMC_LA01_CC_P | D8 |
| U19 | FMC_LA01_CC_N | D9 |
| G17 | FMC_LA02_P | H7 |
| G18 | FMC_LA02_N | H8 |
| T14 | FMC_LA03_P | G9 |
| T15 | FMC_LA03_N | G10 |
| E17 | FMC_LA04_P | H10 |
| D18 | FMC_LA04_N | H11 |
| V17 | FMC_LA05_P | D11 |
| V18 | FMC_LA05_N | D12 |
| T16 | FMC_LA06_P | C10 |
| U17 | FMC_LA06_N | C11 |
| E18 | FMC_LA07_P | H13 |
| E19 | FMC_LA07_N | H14 |
| N20 | FMC_LA08_P | G12 |
| P20 | FMC_LA08_N | G13 |
| W14 | FMC_LA09_P | D14 |
| Y14 | FMC_LA09_N | D15 |
| V12 | FMC_LA10_P | C14 |
| W13 | FMC_LA10_N | C15 |
| N15 | FMC_LA11_P | H16 |
| N16 | FMC_LA11_N | H17 |
| V15 | FMC_LA12_P | G15 |
| W15 | FMC_LA12_N | G16 |
| U13 | FMC_LA13_P | D17 |
| V13 | FMC_LA13_N | D18 |
| Y16 | FMC_LA14_P | C18 |
| Y17 | FMC_LA14_N | C19 |
| J18 | FMC_LA15_P | H19 |
| H18 | FMC_LA15_N | H20 |
| T20 | FMC_LA16_P | G18 |
| U20 | FMC_LA16_N | G19 |
| N18 | FMC_LA17_CC_P | D20 |
| P19 | FMC_LA17_CC_N | D21 |
| U14 | FMC_LA18_CC_P | C22 |
| U15 | FMC_LA18_CC_N | C23 |
| L14 | FMC_LA19_P | H22 |
| L15 | FMC_LA19_N | H23 |
| Y18 | FMC_LA20_P | G21 |
| Y19 | FMC_LA20_N | G22 |
| K14 | FMC_LA21_P | H25 |
| J14 | FMC_LA21_N | H26 |
| T17 | FMC_LA22_P | G24 |
| R18 | FMC_LA22_N | G25 |
| V20 | FMC_LA23_P | D23 |
| W20 | FMC_LA23_N | D24 |
| F19 | FMC_LA24_P | H28 |
| F20 | FMC_LA24_N | H29 |
| D19 | FMC_LA25_P | G27 |
| D20 | FMC_LA25_N | G28 |
| W18 | FMC_LA26_P | D26 |
| W19 | FMC_LA26_N | D27 |
| V16 | FMC_LA27_P | C26 |
| W16 | FMC_LA27_N | C27 |
| K19 | FMC_LA28_P | H31 |
| J19 | FMC_LA28_N | H32 |
| J20 | FMC_LA29_P | G30 |
| H20 | FMC_LA29_N | G31 |
| G19 | FMC_LA30_P | H34 |
| G20 | FMC_LA30_N | H35 |
| M17 | FMC_LA31_P | G33 |
| M18 | FMC_LA31_N | G34 |
| M19 | FMC_LA32_P | H37 |
| M20 | FMC_LA32_N | H38 |
| L19 | FMC_LA33_P | G36 |
| L20 | FMC_LA33_N | G37 |

---
<sub>© 2026 OpenSourceSDRLab. All rights reserved. · <a href="https://www.opensourcesdrlab.com">www.opensourcesdrlab.com</a></sub>
