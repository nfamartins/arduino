### [[Módulo 1. Fundamentos do Arduino e Eletrônica Básica]]

**Objetivo**: Aprender os conceitos básicos de Arduino e reforçar fundamentos de eletrônica para trabalhar com circuitos simples.

---

### [[Módulo 2. Sensores e Leitura Analógica]]

**Objetivo**: Integrar sensores para capturar dados do ambiente e entender a leitura analógica.

- 

---
### Módulo 3: Controle de Matriz de LED 8x8

**Objetivo**: Aprender a manipular e controlar a matriz de LED 8x8, exibindo caracteres, padrões e animações. A matriz permitirá desenvolver habilidades em multiplexação, otimização de código e controle visual avançado.

- **Conceitos teóricos**:
    - Estrutura de uma matriz de LED 8x8 (linhas e colunas de cátodos e ânodos).
    - Princípios de multiplexação e como controlar múltiplos LEDs sem a necessidade de um pino de controle para cada LED.
    - Uso de resistores para limitar a corrente em matrizes LED.
    - Mapeamento de caracteres e padrões (como letras e números) em uma matriz de LED 8x8.
    - Introdução a tabelas de dados para representar caracteres e como armazená-las no código.
    - Uso de temporizadores e loop para criar animações (ex.: rolagem de texto, piscas e efeitos de movimento).
    - Ajuste de velocidade de animação e técnicas para criar efeitos suaves.
- **Práticas**:
    - Conectar a matriz 8x8 ao Arduino e acender LEDs individuais.
    - Entender e aplicar o conceito de varredura de linha, onde cada linha da matriz é acesa individualmente para criar a ilusão de uma imagem estática.
    - Exibir números e letras na matriz de LED.
    - Desenhar padrões simples, como quadrados, cruzes e setas, utilizando a matriz.
    - Criar uma animação de rolagem de texto (ex.: rolar a palavra "HELLO").
    - Implementar uma barra de progresso usando a matriz para mostrar o andamento de uma ação, como a leitura de um sensor ou o movimento de um servo.
    - Fazer uma animação de "batimentos cardíacos" ou de uma onda, para explorar variações de padrões.
- **Projeto final:**
	- Objetivo: Criar um painel de status integrado que exibe informações sobre o sistema em tempo real usando a matriz de LED. O painel mostrará indicadores de sensores e feedback visual para ações no sistema de automação residencial.
-  **Instruções do Projeto**:
    - **Display de Status**: Usar a matriz de LED para exibir um símbolo indicando o estado geral da automação (ex.: “L” para luz ligada, “A” para irrigação ativa, etc.).
    - **Alerta e Feedback Visual**: Implementar uma rolagem de texto que exibe mensagens como “ALERTA: BAIXA UMIDADE” ou “LUMINOSIDADE OK”.
    - **Integração com o Sistema Completo**: Conectar o projeto de matriz com sensores, como o de umidade e luminosidade, para atualizar o status em tempo real conforme o sistema responde às condições ambientais.
- **Desafios Extra**:
    - **Animações Dinâmicas**: Criar animações que mudam de acordo com o estado dos sensores, como um pulso ou onda que varia conforme o nível de umidade.
    - **Painel de Menu Interativo**: Se combinado com o controle remoto, exibir opções de menu na matriz de LED para selecionar modos de operação do sistema (ex.: “MODO AUTOMÁTICO” ou “MANUAL”).

---
### Módulo 4: Atuadores e Controle de Movimento

**Objetivo**: Introduzir o controle de atuadores e movimentos, usando micro servo e motor de passo.

- **Conceitos Teóricos**:
    - Conceitos de motores: servo vs. motor de passo.
    - Função de controle de PWM para atuadores.
    - Funcionamento e controle básico de relés para automação.
- **Práticas**:
    - Controle de micro servo para posicionamento preciso.
    - Controle do motor de passo com registrador de deslocamento.
    - Usar um relé para controlar dispositivos externos (LED ou buzzer).
    - Exibir o ângulo do servo-motor em tempo real no display de 7 segmentos conforme ele se move.
	- Controlar o movimento do servo usando um potenciômetro e exibir o ângulo resultante no display.
- **Projeto Final**: **Portão Automático Simulado**
    - Objetivo: Simular o movimento de um portão automático, controlado por um sensor de luz ou botão. Usar o display OLED para mostrar o status do portão (“Aberto”, “Fechado” ou “Em movimento”).
    - Desafio extra: 
	    - Integrar o controle de um LED ou buzzer para indicar o status do portão (aberto ou fechado).
	    - Adicionar uma contagem de quantas vezes o portão foi aberto ou fechado e exibi-la no display.

---

### Módulo 5: Automação com Sensores de Água e RFID

**Objetivo**: Implementar automação básica com sensores de nível de água e identificação por RFID.

- **Conceitos Teóricos**:
    - Funcionamento e leitura de sensores de nível de água.
    - Introdução ao protocolo de comunicação RFID e autenticação básica.
    - Conceitos de segurança em automação (como restringir acesso).
- **Práticas**:
    - Monitoramento de nível de água e acionamento de LEDs ou buzzer.
    - Leitura de cartões RFID e validação de tags.
    - Condicionais avançadas e estrutura de decisão para liberar ou bloquear ações.
    - Exibir o nível de água em um display de 7 segmentos ou no OLED, usando um valor de 0 a 100 para indicar a porcentagem de preenchimento.
	- Usar o display OLED para mostrar o status do RFID (“Acesso permitido” ou “Acesso negado”) com base na leitura do cartão ou tag.
- **Projeto Final**: **Sistema de Irrigação Automatizado com Acesso Restrito**
    - Objetivo: Criar um sistema que permite iniciar a irrigação (controlar um relé) somente com o uso de uma tag RFID autorizada e quando o nível de umidade estiver baixo. Adicionar o display OLED para mostrar o status da irrigação (ex: “Irrigação ativa” ou “Aguardando sensor”).
    - Desafio extra: 
	    - Adicionar notificações com LED ou buzzer para indicar status do sistema (ativado, desativado, acesso negado).
	    - Exibir também a última leitura de umidade registrada e o tempo decorrido desde a última ativação.

---

### Módulo 6: Comunicação e Controle Remoto

**Objetivo**: Integrar controle remoto infravermelho para controlar elementos do sistema.

- **Conceitos Teóricos**:
    - Funcionamento de sensores e transmissores de infravermelho.
    - Protocolos de comunicação IR e mapeamento de comandos.
- **Práticas**:
    - Leitura de controle remoto infravermelho para identificar e mapear comandos.
    - Programação de resposta a comandos (ativar LEDs, motores).
    - Construção de um menu de controle no monitor serial.
    - Usar o display de 7 segmentos ou OLED para indicar qual função está sendo controlada pelo controle remoto.
	- Criar um menu básico no display OLED que permite alternar entre as funções de iluminação, irrigação e segurança.
- **Projeto Final**: **Painel de Controle Remoto para Sistema Automatizado**
    
    - Objetivo: Criar um sistema de controle remoto que permite ligar/desligar dispositivos e ajustar intensidade de LEDs, motores, etc. Mostrar no display OLED o modo selecionado pelo controle remoto (ex: “Modo Manual” ou “Modo Automático”).
    - Desafio extra: 
	    - Configurar modos diferentes de operação (ex.: modo manual e automático).
	    - Exibir no OLED as informações do sistema em tempo real, como a leitura de sensores e status dos atuadores.

---

### Módulo 7: Projeto Final de Automação Completa - "Automação Residencial"

**Objetivo**: Integrar tudo o que foi aprendido para criar um sistema de automação residencial simples, incluindo controle de iluminação, segurança e monitoramento ambiental.

- **Projeto Completo**:
    - **Sistema de Automação Residencial**:
        - **Controle de iluminação automática**: Acende LEDs quando escurece ou quando há som (como palmas). Exibir no OLED o nível de luz e o status de ativação da iluminação.
        - **Sistema de rega automatizada**: Ativa a bomba d'água quando o sensor de umidade detectar níveis baixos e permite ativação por RFID. Usar o display de 7 segmentos ou OLED para monitorar o nível de umidade e status de irrigação.
        - **Segurança**: Somente usuários com uma tag RFID podem modificar o sistema de rega e iluminação. Exibir no OLED mensagens sobre tentativas de acesso e se a tag RFID foi aceita.
        - **Controle remoto**: Utiliza o controle infravermelho para ligar/desligar sistemas e alternar entre modos automáticos e manuais. O display OLED pode mostrar o modo de operação selecionado pelo controle remoto.

**Desafios adicionais**:
- Usar um display LCD para mostrar o status dos sistemas (ativado, desativado, etc.).
- Criar modos específicos que podem ser alternados com o controle remoto (ex.: Modo Noturno, Modo Econômico).
- Considerar a implementação de funções de "failsafe" (por exemplo, desligar o sistema automaticamente após determinado tempo para evitar sobrecarga).
- Adicionar ícones e gráficos simples no OLED para representar as leituras de sensores (como um ícone de água ou de luz).
- Implementar um sistema de alertas visuais, como exibir “Alerta: Umidade Baixa” no OLED se a umidade estiver em um nível crítico.