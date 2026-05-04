# qrotx Singleband Transmitter Hardware

This is work in progress, it has not yet been tested. Description and calculations will be added later.

## Cloning

This repository uses a git submodule for the KiCad symbol and footprint libraries. Clone with:

```bash
git clone --recurse-submodules git@github.com:qrotx/qrotx-singleband-hw.git
```

If you already cloned without `--recurse-submodules`, initialize the submodule with:

```bash
git submodule update --init
```

## Assembly

### NUCLEO-G474RE Board Modifications

The NUCLEO-G474RE board requires the following modifications before mounting on the PCB.
Reference: [UM2505 STM32G4 Nucleo-64 boards (MB1367) user manual](https://www.st.com/resource/en/user_manual/um2505-stm32g4-nucleo64-boards-mb1367-stmicroelectronics.pdf)

#### Power Supply (JP5)

Change jumper JP5 from the default **5V_STLK** position to the **E5V** position. This powers the
Nucleo board from the E5V pin supplied by the PCB instead of from USB.

#### HSE Clock — Oscillator from External PF0 (Section 7.5.1)

Modify the following solder bridges to configure the HSE clock input for an external
oscillator on PF0:

| Solder Bridge | Default | Required |
|---------------|---------|----------|
| SB24          | OFF     | OFF      |
| SB25          | ON      | OFF      |
| SB26          | ON      | OFF      |
| SB27          | OFF     | OFF      |
| SB28          | OFF     | ON       |

## License
These hardware designs are made available under the CERN Open Hardware Licence Version 2 - Strongly Reciprocal.
See [LICENSE](LICENSE) for the full text.
