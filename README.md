# [Nios V](https://www.intel.com.br/content/www/br/pt/products/details/fpga/intellectual-property/processors-peripherals/niosv.html)

![nios-v-blog-graphic](https://github.com/user-attachments/assets/e407f1ac-3645-4be8-ac72-91c45ee0ec75)


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

## 3. Fluxo de Design
![nios-v-processor-design-flow-diagram_1920-1080](https://github.com/user-attachments/assets/ac84c855-d894-4c09-b68d-614ac4dfbcb0)

- O fluxo de desenvolvimento do processador Nios® V consiste em três elementos:<br>
--> Projeto do sistema, envolvendo hardware e software<br>
--> Design de hardware<br>
--> Design de software<br>
- Inicie o desenvolvimento do seu processador Nios® V criando um conceito de sistema e realizando uma análise de requisitos de sistema. Em seguida, crie e gere o sistema no Platform Designer e produzirá um arquivo do Platform Designer. O ficheiro Platform Designer inclui núcleos de processador Nios V e componentes padrão. Após a geração do sistema, os fluxos de hardware e software podem ser iniciados
- Para o desenvolvimento de hardware do processador Nios V, é necessário:<br>
--> Selecionar o FPGA de destino com base nos requisitos do sistema. Consulte Considerações de Design seção<br>
--> Integre o sistema Platform Designer com o projeto de software Quartus® Prime<br>
--> Atribuir locais de pinos<br>
--> Configurar requisitos de tempo e outras restrições de projeto<br>
--> Depois de compilar o design do hardware, baixe o arquivo .sof para a placa de destino<br>
- Para o desenvolvimento de software do processador Nios V, é necessário:<br>
--> Desenvolva o seu software com as Ferramentas de Processador Nios V e o IDE Ashling RiscFree para Intel FPGA. O software do processador Nios® V inclui o HAL, controladores periféricos, códigos de aplicação C/C++ do utilizador e bibliotecas personalizadas<br>
--> Faça o download do ficheiro .elf para o sistema de processador Nios® V na placa de destino depois de criar o pacote de suporte de aplicações e placas (BSP). O sistema de processador Nios® V está pronto para testes e depuração<br>
- Se verificar que o seu software não cumpre as especificações durante o teste, volte ao início do fluxo de software e verifique os códigos de aplicação, controladores e BSP para corrigir quaisquer erros e garantir que o sistema de processador Nios® V é executado corretamente<br>
- Se o hardware não atender às especificações, retorne à etapa de definição e geração do sistema Platform Designer e reinicie o fluxo de hardware e software. O arquivo-chave necessário para gerar o software do aplicativo é o arquivo de sistema Platform Designer. Como esse arquivo descreve componentes e conexões de hardware, você deve regenerar esse arquivo se fizer uma alteração de hardware. O sistema está completo quando o software e o hardware atendem às especificações<br>

## 4. Hello World

### 4.1. Como executar um processador Nios® V “A aplicação Hello World” no Zephyr RTOS?
![Block-Diagram](https://github.com/user-attachments/assets/980e98c4-d525-43c1-a0f4-2e3470f827f4)
- Nessa imagem mostra o processador Nios V/m e a interconexão Avalon
- A interconexão Avalon (Avalon Interconnect) é um barramento proprietário da Intel, antigamente era da Altera, usado para conectar componentes dentro do FPGA
- O Zephyr RTOS possui suporte para o Nios V, permitindo que ele seja usado como sistema operacional em plataformas baseadas nesse processador
- O Zephyr pode ser configurado para se comunicar com os periféricos representados no diagrama, como memória on-chip e comunicação via JTAG UART
- O Zephyr pode ser usado para facilitar a comunicação entre o host PC e o sistema embarcado na FPGA, utilizando protocolos compatíveis via JTAG UART ou outro meio de depuração

#### 4.1.1. Nios V/g

- [Exemplo de Design Nios® V/g Zephyr - Hello World](https://www.rocketboards.org/foswiki/Documentation/NiosVgZephyrDesignExampleHelloWorld)
- [Exemplo de Design: Arria® 10 FPGA - Nios® V/g Processador Hello World](https://www.intel.com/content/www/us/en/design-example/776196/intel-arria-10-fpga-hello-world-design-on-nios-v-g-processor.html)

#### 4.1.2. Nios V/m

- [Exemplo de Design Nios V/m Zephyr - Hello World](https://www.rocketboards.org/foswiki/Documentation/NiosVZephyrDesignExampleHelloWorld)
- [Exemplo de Design: Arria® 10 FPGA - Nios® V/m Processador Hello World](https://www.intel.com/content/www/us/en/design-example/776196/intel-arria-10-fpga-hello-world-design-on-nios-v-g-processor.html)

### 4.2. Como executar um processador Nios V com o pacote de software MicroC/TCP-IP?

- O MicroC/TCP-IP é uma pilha de protocolos TCP/IP otimizada para sistemas embarcados
- Essa pilha TCP/IP é para rodar em microcontroladores FPGAs, tendo conexões Ethernet ou Wi-Fi com baixo consumo de memória
- [Processador Nios® V - Utilização da Pilha MicroC/TCP-IP](https://www.intel.com/content/www/us/en/docs/programmable/726952/current/processor-using-the-microc-tcp-ip-stack.html)
- Exemplos de Design: <br>
-> [Arria® 10 FPGA - Design de Servidor de Soquete Simples para Processador Nios V/m](https://www.intel.com/content/www/us/en/design-example/791231/intel-arria-10-fpga-simple-socket-server-design-for-nios-v-m-processor.html)<br>
-> [Arria® 10 FPGA - uC/OS-II RTOS com Iperf para Processador Nios V/m](https://www.intel.com/content/www/us/en/design-example/787050/intel-arria-10-fpga-c-os-ii-rtos-with-iperf-for-nios-v-m-processor.html)

### ... Em progresso


## Links úteis
- [Intel Nios V](https://www.intel.com.br/content/www/br/pt/products/details/fpga/intellectual-property/processors-peripherals/niosv.html)
- [Macnica Nios V](https://www.intel.com.br/content/www/br/pt/products/details/fpga/intellectual-property/processors-peripherals/niosv.html)
- [Suporte Intel](https://www.intel.com.br/content/www/br/pt/support/programmable/support-resources/intellectual-property/intellectual-property.html)
- [Desenvolvedores de Nios V](https://www.intel.com.br/content/www/br/pt/support/programmable/support-resources/support-centers/nios-v-support.html)


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





