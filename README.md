# Nios V
- Nios V é um processador de arquitetura RISC-V da Intel utilizado em FPGA’s, permitindo a customização de projetos de hardware
- Faz parte da geração softcore da Intel
- Nios V é isento de direitos autorais
- Possibilidade de expandir ainda mais a funcionalidade colocando periféricos personalizados ao seu redor

## 1. Versões do processador

### 1.1. Nios V/g
![NiosV-Ge](https://github.com/user-attachments/assets/0720a4f0-8542-4dd6-ac52-04891c6499c7)
- Processador de propósito geral, referência ao "g" de general
- Possui desempenho suporior às outras versões de processador Nios V
- Suporta Sistemas Embarcados RTOS. RTOS (Real-Time Operating System) são sistemas operacionais de tempo real usados em aplicações de automação industrial, telecomunicações e dispositivos IoT
- Conjunto de instruções RISC-V utilizada é RV32IM(F)Zicsr_Zicbom
#### 1.1.1. RV32IM(F)Zicsr_Zicbom
- RV32I -> Arquitetura RISC-V de 32 bits de base de números inteiros
- M -> Suporta operações de multiplicação e divisão
- F -> Suporta operações de ponto flutuante
- Zicsr -> Suporta instruções de controle de status e registro (CSR – Control and Status Register)
- Zicbom -> Suporta buffer de operações de memória

### 1.2.Nios V/m

### 1.3.Nios V/c
