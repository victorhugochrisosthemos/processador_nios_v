# [Nios V](https://www.macnica.co.jp/en/business/semiconductor/manufacturers/altera/products/141802/)
![nios-v-blog-graphic](https://github.com/user-attachments/assets/1f35953b-1c1e-40ae-8088-1629803329d3)
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
- Se precisar de eficiência para um processameto específico, use um microcontrolador
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
![NiosV-Ce](https://github.com/user-attachments/assets/8230b154-ab77-41c0-aee1-53f6854125f6)
- É um microcontrolador compacto, projetado para aplicações de controle que não exigem alto desempenho ou muitos recursos de processamento
- O consumo de recursos do FPGA precisa ser mínimo
- Conjunto de instruções RV32I, sem extensões para multiplicação, ponto flutuante
- Não há suporte para debug via JTAG ou para ferramentas de rastreamento de execução
    -> Isso significa que ele não pode parar a execução de uma tarefa para atender eventos externos, como uma entrada de sensor ou um timer
    -> Ele é adequado para tarefas contínuas e previsíveis, como controle de atuadores ou lógica simples de automação
- Recomendado para tarefas simples e previsíveis com lógica básica, ascender LED, etc


## 2. Ambiente de Desenvolvimento
- Com o Nios V, você pode fazer configuração de hardware no FPGA e programar software embarcado
- Você pode usar o Intel Quartus Prime's “Platform Designer” para incorporar Nios V e periféricos e gerar um BSP (Board Support Package)
- O módulo Platform Designer permite fazer a integração de IPs (Intelectual Property - blocos de hardware que podem ser de outros fabricantes)
- BSP (Board Support Package) é um conjunto de drivers e bibliotecas que permite que o software embarcado interaja com o hardware corretamente
- Construção de aplicativos: interface de linha de comando ou IDE baseado em Eclipse
- Depuração de aplicações: “Ashling RiscFree IDE para Intel FPGAs (free)” ou plugin de depuração de código aberto suporta Intel HAL
- O Ashling RiscFree IDE é uma IDE de arquitetura de processadores RISC-V
- Intel HAL (Hardware Abstraction Layer) é uma camada de software que facilita a comunicação entre o sistema operacional e o hardware do FPGA

### 2.1. RiscFree e Intel Quartus Prime
- O RiscFree é um ambiente de desenvolvimento (IDE) focada no desenvolvimento de software embarcado para RISC-V
- O Intel Quartus Prime é uma ferramenta EDA (Electronic Design Automation) da Intel usada para projetar e <br>
programar FPGAs. Com ele pode criar, gerar simulações e implementar circuitos digitais em FPGA com linguagens de descrição de hardware VHDL e Verilog
- Se você estiver usando uma FPGA Intel com um núcleo RISC-V, você pode usar tanto o RiscFree quanto o Intel Quartus Prime, <br>
utilizando Quartus Prime para configurar e programar o FPGA e o RiscFree para desenvolver e depurar código para o processador RISC-V dentro da FPGA.

### 2.2. RiscFree
- [Projeto com Ashling RiscFree](https://malt.zendesk.com/hc/ja/articles/9280647796761-Ashling-RiscFree-IDE-%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%9F-Nios-V-%E3%83%97%E3%83%AD%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E9%96%8B%E7%99%BA%E6%89%8B%E9%A0%86)
- O RiscFree IDE fornece um ambiente para desenvolvimento de software em C e C++
- IDE baseado em CDT Eclipse* com suporte completo de criação, edição, compilação e depuração de código-fonte e projeto usando a cadeia de ferramentas RISC-V GNU compilador collection (GCC)
- Gerente de Projeto e Build Manager, incluindo suporte a Make e CMake com importação, compilação e depuração de estruturas de aplicativos criadas usando o Intel Quartus Prime software
- Cadeia de ferramentas RISC-V GNU GCC com suporte para bibliotecas de tempo de execução newlib ou picolibc usando Nios V API de Camada de Abstração de Hardware (HAL) para acesso a hardware
- Apoio integrado para Intel FPGA Baixar Cabo II sonda de depuração JTAG
- Suporte de depuração baseado em ROM ou RAM, por exemplo, pontos de interrupção de hardware para suporte baseado em flash
- Visualizador de Registros de Alto Nível baseado em arquivos padrão do setor System View Description (SVD)
- Terminal serial integrado

### 2.3. Intel Quartus Prime
#### 2.3.1. Baixando e instalando o Software de projeto Intel® Quartus® Prime Lite Edition versão 23.1.1 para Windows
- [Site da Intel com o download](https://www.intel.com.br/content/www/br/pt/software-kit/825278/intel-quartus-prime-lite-edition-design-software-version-23-1-1-for-windows.html)
- Ao baixar, selecione os módulos de desenvolvimento necessários
- Depois de feito, a IDE RiscFree terá sido instalada também


<!-- 
- Quando se pensa em automatização com hardware, considera-se o uso de FPGA's para customizar circuitos integrados
- O mercado de FPGA's no mundo é de bilhões de dólares com projeção de crescimento com aplicações em cenários como Agronegócio, Big Data, Smart Cities, Indústrica 4.0, Inteligência Artificial, IoT, Segurança e Saúde
- Sobre o ecossistema FPGA, no Brasil temos a Empresa Macnica, distribuidora de FPGA da Intel no país, capacitada também a promover cursos através de seu site para desenvolvedores
- Nesse contexto, desenvolver FPGA utilizando o processador Nios V é vantajoso
- Existem versões do processador voltados para Sistemas Embarcados e Microcontroladores Compactos
- Além disso, o fato do Nios V ser baseado arquitetura RISC-V permite o uso sem pagar licenciamento, podendo também adicionar instruções no processador, extensões como criptografia, etc
- O uso do Nios V em FPGA pode ser uma solução mais econômica do que projetar um processador ASIC (Application-Specific Integrated Circuit)



Links:

https://blog.macnicadhw.com.br/fabricantes/tecnologia-fpga-mercado-brasileiro/
https://www.businessresearchinsights.com/pt/market-reports/medium-density-fpga-market-114251
https://www.mordorintelligence.com/pt/industry-reports/field-programmable-gate-array-fpga-market



-->





