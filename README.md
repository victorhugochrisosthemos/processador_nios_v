# Nios V
- Nios V é um processador de arquitetura RISC-V da Intel utilizado em FPGA’s, permitindo a customização de projetos de hardware
- Faz parte da geração softcore da Intel
- Nios V é isento de direitos autorais
- Possibilidade de expandir ainda mais a funcionalidade colocando periféricos personalizados ao seu redor

## 1. Versões do processador

### 1.1. Nios V/g
![NiosV-Ge](https://github.com/user-attachments/assets/0720a4f0-8542-4dd6-ac52-04891c6499c7)
- Processador de propósito geral
- Possui desempenho suporior às outras versões de processador Nios V
- Suporta Sistemas Embarcados RTOS. RTOS (Real-Time Operating System) são sistemas operacionais de tempo real usados em aplicações de automação industrial, telecomunicações e dispositivos IoT
- Conjunto de instruções RISC-V utilizada é RV32IM(F)Zicsr_Zicbom
#### 1.1.1. RV32IM(F)Zicsr_Zicbom
- RV32I -> Arquitetura RISC-V de 32 bits com base de operaçoes em números inteiros
- M -> Suporta operações de multiplicação e divisão
- F -> Suporta operações de ponto flutuante
- Zicsr -> Suporta instruções de controle de status e registro (CSR – Control and Status Register)
- Zicbom -> Suporta buffer de operações de memória

### 1.2. Nios V/m
![NiosV-Me](https://github.com/user-attachments/assets/7de7432b-9b55-4f02-9542-0218aad0109b)
- É um microcontrolador
- Projetado para ser eficiente tanto em desempenho quanto em uso de recursos
- Suporta RTOS, permitindo o uso de sistemas como FreeRTOS, Zephyr
- Conjunto de instruções RV32IZicsr (pipeline) e RV32IZicsr (não-pipeline)

#### 1.2.1. Diferença entre processador e microcontrolador
- Se precisar de eficiência para um processameto especídifico, use um microcontrolador
- Se precisar de desempenho e maior flexibilidade, use um processador
- Um microcontrolador possui processador, memória e periféricos
- O processador limita-se à unidade central de processamento que depende de componentes externos para funcionar
- Exemplo de microcontrolador: Arduino
- Exemplo de processador: Intel Core i7

#### 1.2.2. RV32IZicsr
- RV32I -> Arquitetura RISC-V de 32 bits com base de operaçoes em números inteiros
- Z -> Pode existir personalizações da Intel para essa implementação
- Zicsr -> Suporta instruções de controle de status e registro (CSR – Control and Status Register)
- Esse tipo de aplicação pode usar processar dados com ou sem pipeline. Com pipeline haverá melhor desempenho porque irá segmentar um processo e executar as intruções em partes diferentes do processar. Não utilizar pipeline vai definir um padrão sequencial de processamento, é considerável em cenário em que tamano e energia são pontos importantes
  
### 1.3.Nios V/c
