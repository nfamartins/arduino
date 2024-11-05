- **Conceitos Teóricos**:
    - Diferença entre entrada digital e analógica.
    - Funcionamento básico dos sensores de umidade, luz e som.
    - Conversão Analógico-Digital (ADC) no Arduino.
    - Corrente e tensão nos componentes
- **Práticas**:
    - Leitura de sensores de luz e som para controlar o LED.
    - Programação de condicionais: acionamento de LEDs com base em leituras de sensor.
    - Uso do monitor serial para visualizar dados em tempo real.
    - Usar o display de 7 segmentos de 4 dígitos para mostrar valores de sensores (por exemplo, exibir a leitura de umidade ou luminosidade em tempo real).
	- Criar uma barra de progresso usando os LEDs e o display de 7 segmentos para representar o nível de umidade.
	- Medir tensão e estimar corrente
- **Projeto Final**: **Sistema de Iluminação Automática**
    - Objetivo: Construir um sistema que acende um LED quando a luz ambiente estiver baixa.
    - Adicionar o display de 7 segmentos para indicar a intensidade de luz ambiente em tempo real, além de acionar o LED conforme a luminosidade.
    - Desafio extra: 
	    - Integrar o sensor de som para controlar o LED com uma batida de palmas. 
	    - Exibir também um contador que registra a quantidade de vezes que a luz foi acionada devido a baixa luminosidade.


# Conceitos
## Corrente e tensão nos componentes

==Cada componente eletrônico tem especificações próprias de tensão e corrente para funcionar corretamente e com segurança==, e isso se aplica também aos pinos do Arduino.

No Arduino, o limite recomendado de **20-40mA** por pino de saída (também chamados de pinos digitais) existe por algumas razões importantes:
1. **Proteção do Microcontrolador**: O microcontrolador (no caso do Arduino Uno, o ATmega328) tem um limite máximo de corrente que pode circular por cada pino sem causar danos. Correntes muito altas podem danificar o pino de saída ou até mesmo comprometer o microcontrolador inteiro. No caso do ATmega328, o limite máximo absoluto para cada pino é cerca de **40mA**, mas valores mais seguros (como **20mA**) são recomendados para evitar o desgaste e prolongar a vida útil do componente.
2. **Limite Total de Corrente do Chip**: Além do limite por pino, o microcontrolador tem um limite de corrente total que ele pode fornecer através de todos os pinos somados. No ATmega328, por exemplo, a corrente total máxima para todos os pinos juntos é cerca de **200mA**. Se você conectar muitos componentes que puxam mais do que esse total, corre o risco de aquecer o microcontrolador e danificá-lo.
3. **Conformidade com Componentes**: Muitos componentes eletrônicos, como LEDs e sensores, funcionam melhor em faixas específicas de corrente. LEDs comuns, por exemplo, operam de forma eficiente entre 10 e 20mA. Correr acima desses valores pode diminuir sua vida útil ou até queimá-los. Por isso, ao projetar circuitos, é importante conhecer os limites de corrente e tensão de cada componente e garantir que eles sejam respeitados.

Praticamente todos os componentes eletrônicos têm especificações detalhadas para corrente e tensão. Alguns exemplos:
- **LEDs**: Geralmente operam entre **1.8V a 2.2V** (dependendo da cor) e correntes típicas de **10 a 20mA**.
- **Motores**: Motores de corrente contínua (DC) e motores de passo têm especificações de corrente e tensão, que são muito mais altas do que um LED, frequentemente acima de **100mA**.
- **Sensores**: Cada sensor possui um intervalo de tensão de operação (como **3.3V ou 5V**) e uma corrente de consumo que precisa ser atendida para funcionar corretamente.
- **Relés**: São componentes que podem demandar mais corrente (geralmente **30-70mA**), por isso frequentemente é necessário usar transistores para controlar relés com o Arduino, já que ele sozinho não pode fornecer a corrente necessária.
Essas especificações são geralmente fornecidas no **datasheet** do componente, que é um documento técnico que detalha as características elétricas, limites e recomendações para uso.

# Práticas
## 6. Medir a tensão e estimar a corrente
### 1. Medindo a Tensão com o Arduino

O Arduino Uno possui **pinos analógicos** (A0 a A5) que podem medir tensões de 0 a 5V, com uma resolução de 10 bits (ou seja, valores de 0 a 1023). Isso permite medir tensões com um bom grau de precisão para circuitos de baixa tensão.

#### Passos para medir a tensão

1. **Montagem do Circuito**:
    - Conecte o ponto onde você deseja medir a tensão ao pino analógico do Arduino (por exemplo, A0).
    - Conecte o GND do Arduino ao GND do circuito.
2. **Escreva o Código no Arduino**: O código abaixo lê o valor analógico do pino A0 e o converte para volts:
    
    cpp
    
    Copiar código
    
    `const int analogPin = A0; // Pino onde a tensão será medida const float Vcc = 5.0; // Tensão de referência do Arduino (5V para Uno)  void setup() {     Serial.begin(9600); // Inicializa a comunicação serial }  void loop() {     int analogValue = analogRead(analogPin); // Lê o valor analógico     float voltage = (analogValue / 1023.0) * Vcc; // Converte para volts     Serial.print("Tensão: ");     Serial.print(voltage);     Serial.println(" V");     delay(1000); // Aguarda um segundo entre as leituras }`
    
3. **Interprete os Resultados**:  
    Abra o **Monitor Serial** no Arduino IDE para ver a tensão medida em volts. Esse valor será a tensão do ponto onde o pino A0 está conectado.

### 2. Estimando a Corrente com o Arduino (Usando um Resistor)

Para medir a corrente sem um multímetro, podemos usar a **Lei de Ohm** e medir a queda de tensão em um resistor conhecido que você coloca em série com o circuito. Essa técnica é chamada de **resistor de derivação**.

#### Passos para Estimar a Corrente

1. **Escolha um Resistor de Derivação**:  
    Escolha um resistor de baixo valor (como 10Ω ou 1Ω) e coloque-o em série com o componente onde você deseja medir a corrente.
    
2. **Meça a Queda de Tensão no Resistor**: Conecte o pino analógico do Arduino em um dos terminais do resistor e o GND do Arduino no outro terminal. Com isso, você estará medindo a queda de tensão no resistor.
    
3. **Escreva o Código para Calcular a Corrente**: Use a Lei de Ohm para calcular a corrente I=VRI = \frac{V}{R}I=RV​, onde VVV é a queda de tensão medida pelo Arduino e RRR é o valor do resistor.
    
    cpp
    
    Copiar código
    
    `const int analogPin = A0; // Pino onde a tensão do resistor é medida const float resistorValue = 10.0; // Valor do resistor de derivação em ohms const float Vcc = 5.0; // Tensão de referência do Arduino  void setup() {     Serial.begin(9600); }  void loop() {     int analogValue = analogRead(analogPin);     float voltageDrop = (analogValue / 1023.0) * Vcc; // Converte para volts     float current = voltageDrop / resistorValue; // Calcula a corrente em amperes          Serial.print("Queda de Tensão: ");     Serial.print(voltageDrop);     Serial.print(" V, Corrente: ");     Serial.print(current * 1000); // Corrente em mA     Serial.println(" mA");     delay(1000); }`
    
4. **Interprete os Resultados**: Acesse o Monitor Serial para ver a queda de tensão e a corrente estimada em miliamperes (mA). Essa técnica não é tão precisa quanto um multímetro, mas dá uma boa estimativa da corrente no circuito.
    

### Observação Importante

Essas medições funcionam bem para tensões e correntes **baixas e constantes**. Se a corrente for muito alta, pode não ser seguro para o Arduino, então tenha cuidado e comece com resistores maiores se não tiver certeza da corrente no circuito.

Usar o Arduino como um "multímetro improvisado" é uma solução criativa e muito útil para aprender mais sobre o comportamento dos circuitos!
