# UVM-based SPI / I2C Verification

SPI와 I2C Master / Slave RTL을 설계하고 **SystemVerilog UVM 환경에서 Protocol 및 Data 동작을 검증하는 프로젝트**입니다.

Simulation 결과뿐 아니라 FPGA와 Logic Analyzer를 이용한 실제 파형 측정을 통해 RTL과 Hardware 동작의 정합성을 확인하는 것을 목표로 합니다.

## Overview

- SPI Master / Slave RTL
- I2C Master / Slave RTL
- UVM Testbench
- Scoreboard
- Functional Coverage
- FPGA Board Validation
- Logic Analyzer Protocol Measurement

## Verification Architecture

```text
Sequence
   ↓
Sequencer
   ↓
Driver
   ↓
Interface
   ↓
SPI / I2C DUT
   ↓
Monitor
   ├────────→ Scoreboard
   └────────→ Functional Coverage
```

## SPI

### Signals

- `SCLK`
- `MOSI`
- `MISO`
- `SS_N`

### Verification Points

- Master → Slave Data Transfer
- Slave → Master Data Transfer
- Loopback Data Match
- Clock / Data Edge Timing
- Transaction Done
- Random Data
- Corner Data Pattern
- Scoreboard Comparison
- Functional Coverage

## I2C

### Signals

- `SCL`
- `SDA`

SDA는 Open-Drain 구조를 고려합니다.

### Verification Points

- START Condition
- STOP Condition
- Slave Address
- Data Transfer
- ACK
- NACK
- Repeated Transaction
- Random Data
- Scoreboard Comparison
- Functional Coverage

## UVM Components

```text
uvm/
├── *_seq_item.sv
├── *_sequence.sv
├── *_sequencer.sv
├── *_driver.sv
├── *_monitor.sv
├── *_scoreboard.sv
├── *_coverage.sv
├── *_agent.sv
├── *_env.sv
├── *_test.sv
└── tb_top.sv
```

## Hardware Validation

Simulation에서 검증한 Protocol Timing을 FPGA에 합성한 뒤 Logic Analyzer로 관찰하여 다음 항목을 비교합니다.

```text
RTL Simulation Waveform
          ↕
FPGA Logic Analyzer Waveform
```

이를 통해 Testbench 내부에서만 맞는 동작이 아니라 실제 Hardware에서도 Protocol 조건을 만족하는지 확인합니다.

## Development Environment

- Verilog HDL
- SystemVerilog
- UVM
- VCS / Verdi
- Xilinx Vivado
- FPGA Board
- Logic Analyzer

## Key Skills

- Serial Protocol RTL Design
- UVM Verification Environment
- Constrained Random Verification
- Scoreboard
- Functional Coverage
- Protocol Debugging
- FPGA Measurement
