- **Conceitos Teóricos**:
    - Introdução ao Arduino: arquitetura, pinos, IDE e estrutura do código.
    - Conceitos de corrente, tensão e resistência (Lei de Ohm).
    - Componentes básicos: resistores, LEDs, botões e potenciômetros.
    - Manipulação de entrada e saída digital no Arduino.
- **Práticas**:
    - Configuração do ambiente de desenvolvimento e upload de programas básicos.
    - Projetos simples com LEDs: pisca-pisca, controle de brilho com PWM.
    - Leitura de botões e potenciômetros para controle de LEDs.
	- Aprender a controlar um display de 7 segmentos de um algarismo, mostrando números de 0 a 9.
	- Fazer um contador com o display de 7 segmentos que aumenta ao pressionar um botão.
- **Projeto Final**: **Painel de Controle de LED**
    - Objetivo: Construir um painel com LEDs controlados por botões e potenciômetros.
    - Desafio extra: Adicionar diferentes padrões de pisca-pisca e controle de intensidade usando PWM e botões.


# Conceitos
## Introdução ao Arduino

**Arquitetura do Arduino Uno** 
O Arduino Uno possui um microcontrolador, o ATmega328P, que funciona como o "cérebro" da placa, controlando as entradas e saídas e executando o código que você escreve. **A placa possui uma variedade de pinos de entrada e saída, tanto digitais quanto analógicos, que permitem a conexão com diversos componentes externos**, como LEDs, motores e sensores.

 **Tipos de Pinos**
 No Arduino Uno, temos 14 pinos digitais (D0 a D13), que podem ser usados como entradas ou saídas para sinais digitais, e 6 pinos analógicos (A0 a A5) para leituras de sinais analógicos. Além disso, alguns pinos digitais (3, 5, 6, 9, 10 e 11) suportam PWM (modulação por largura de pulso), essencial para controlar a intensidade de LEDs ou a velocidade de motores.

**IDE do Arduino**
A Arduino IDE é o software onde você escreve, edita e carrega o código (chamado de sketch) para o Arduino. Ela oferece uma estrutura simples e uma biblioteca extensa, facilitando a programação mesmo para iniciantes.

**Estrutura do Código** 
Todo programa Arduino possui duas funções principais: `setup()` e `loop()`. `setup()` é executada uma única vez, no início, e configura os pinos e outras variáveis. `loop()` é a função que roda continuamente, controlando o que o Arduino faz em tempo real, repetidamente, até ser desligado.
## Conceitos básicos de elétrica

**Tensão - Voltagem (V)**
A tensão é a "força" que impulsiona os elétrons através de um circuito. ==É medida em volts (V)==. Em termos práticos, no Arduino, utilizamos uma tensão de 5V ou 3,3V para alimentar os componentes.

**Corrente (I)** 
A corrente é o fluxo de elétrons que percorre o circuito, ==medido em ampères (A)==. Todo componente tem um limite de corrente que ele pode suportar, e o Arduino também tem uma corrente máxima de saída por pino, cerca de 20mA. Exceder esse valor pode danificar a placa ou o componente.

**Resistência (R)**
Resistência é a oposição ao fluxo de corrente, ==medida em ohms (Ω)==. **Usamos resistores para controlar a quantidade de corrente que chega a um componente**, protegendo-o de receber mais corrente do que suporta.

**Lei de Ohm**
A Lei de Ohm ($V = I \times R$) nos ajuda a calcular a quantidade de resistência necessária para manter uma corrente segura em um circuito. Por exemplo, para um LED que funciona em 2V e precisa de 20mA, conectando-o a uma fonte de 5V, calculamos o resistor necessário como:
$$R=\frac{(5V - 2V)}{0.02A} = 150Ω$$
**Leis de Kirchhofff**
1. LKC (das correntes): ==a soma das correntes que entram é igual a soma das correntes que saem==. Lei de Conservação da Carga Elétrica
2. LKT (das tensões): a soma algébrica de todas as variações de tensões (ddps) ao longo da malha é sempre zero. ==Conservação da Tensão Elétrica==.

## Componentes Básicos

**Resistores**
Limitam a corrente em um circuito. São essenciais para proteger componentes sensíveis, como LEDs. O valor do resistor é escolhido com base na corrente que queremos limitar, usando a Lei de Ohm.

**LEDs (Diodos Emissores de Luz)**
São componentes que emitem luz quando uma corrente passa por eles. LEDs têm polaridade, ou seja, um lado positivo (ânodo) e um lado negativo (cátodo), que precisam ser conectados corretamente. O uso de um resistor em série é necessário para evitar que o LED queime.

**Botões (Push Buttons)**
Funcionam como interruptores para abrir ou fechar um circuito. Quando o botão é pressionado, ele conecta os terminais, permitindo a passagem de corrente. Para o Arduino, usamos resistores pull-up ou pull-down para estabilizar a leitura do botão, evitando leituras flutuantes quando o botão não está pressionado.

**Potenciômetros**
São resistores variáveis, usados para ajustar a resistência e, com isso, controlar a quantidade de corrente no circuito. No Arduino, conectamos o potenciômetro a uma entrada analógica, e ele envia um valor entre 0 e 1023, que podemos usar para controlar a intensidade de LEDs, por exemplo.

## Manipulação de Entrada e Saída Digital no Arduino

**Entrada Digital**
O Arduino lê um sinal digital como "ALTO" (HIGH - 5V) ou "BAIXO" (LOW - 0V). Quando usamos um botão, por exemplo, o Arduino interpreta se ele está pressionado (ALTO) ou solto (BAIXO).

**Saída Digital**
Em modo de saída digital, o Arduino pode fornecer um sinal ALTO (5V) ou BAIXO (0V) a um pino, controlando se o componente (por exemplo, um LED) está ligado ou desligado.

**Uso de Funções Básicas**
Funções como `digitalRead()` e `digitalWrite()` são utilizadas para ler e escrever valores digitais. Por exemplo, `digitalWrite(pin, HIGH);` liga um LED, enquanto `digitalWrite(pin, LOW);` o desliga.

# Práticas
## Prática 1: Configuração do Ambiente de Desenvolvimento e Upload de Programas Básicos

**Objetivo**: Aprender a configurar a IDE do Arduino, conectar a placa ao computador e carregar um programa simples.

1. **Instalação da IDE do Arduino**:
    - Baixe e instale a IDE do Arduino para o seu sistema operacional (Windows, Mac ou Linux).
    - Abra a IDE e vá até **Ferramentas** > **Placa** > **Arduino Uno**.
    - Conecte a placa ao computador usando um cabo USB. Verifique se a porta correta está selecionada em **Ferramentas** > **Porta**.

2. **Programa Básico - Blink**:
	- Na IDE, vá até **Arquivo** > **Preferências**
		- Na aba **Configurações**, na **localização do Sketchbook**, selecione a pasta **sketches** deste repositório
	- Vá até **Arquivo** > **Sketchbook**>**Blink**
    - Este programa pisca o LED embutido na placa Arduino (no pino 13) a cada segundo.
    - Faça upload do programa clicando no botão **Upload** (seta para a direita) na barra superior da IDE.
    - Observe o LED piscando na placa. Experimente alterar o tempo de atraso (`delay()`) para mudar a frequência do pisca-pisca.