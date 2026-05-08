# Pinball Arduino - Projeto Voluntário

Este repositório contém o código-fonte para um sistema de controle de uma máquina de Pinball desenvolvida com Arduino. O projeto foi elaborado como uma iniciativa voluntária para explorar conceitos de sistemas embarcados, eletrónica e lógica de programação.

## Funcionalidades

- **Contagem de Pontos:** Sistema de pontuação acumulativa (incrementos de 10 pontos).
- **Interface em Tempo Real:** Exibição da pontuação atual num LCD 16x2.
- **Interrupções de Hardware:** Utilização de `attachInterrupt` para garantir a captura de colisões de alta velocidade da bola nos alvos (bumpers).
- **Sensor de Reset:** Sensor infravermelho posicionado na base para detetar o fim da jogada e reiniciar o contador.
- **Debounce:** Tratamento via software para evitar leituras falsas causadas pelo ruído mecânico dos botões.

## Hardware Necessário

- **Microcontrolador:** Arduino (ex: Uno, Mega ou Nano).
- **Display:** LCD 16x2 (Compatível com Hitachi HD44780).
- **Entradas:** - 3x Botões/Sensores de impacto (Alvos).
  - 1x Sensor Infravermelho (Deteção de queda da bola).
- **Comunicação:** Serial configurada para 115200 baud.

## Pinagem Utilizada

| Componente | Pino Arduino | Função |
| :--- | :--- | :--- |
| **LCD RS** | 12 | Register Select |
| **LCD Enable** | 11 | Ativação |
| **LCD D4-D7** | 7, 6, 5, 4 | Barramento de Dados |
| **Infravermelho** | 8 | Sensor de Reset (Fim de jogo) |
| **Botão 1** | 21 | Alvo 1 (Interrupção) |
| **Botão 2** | 3 | Alvo 2 (Interrupção) |
| **Botão 3** | 2 | Alvo 3 (Interrupção) |

## Como Executar

1.  Clone este repositório ou copie o código para a sua IDE Arduino.
2.  Certifique-se de que a biblioteca `LiquidCrystal.h` está instalada (incluída por padrão na IDE).
3.  Realize as conexões conforme a tabela de pinagem acima.
4.  Faça o upload do código para o seu microcontrolador.
5.  Abra o **Serial Monitor** com o baud rate em `115200` para acompanhar os logs do sistema.

## Estrutura do Código

O software utiliza um modelo baseado em interrupções para máxima precisão:
- `setup()`: Configura os pinos, inicializa o LCD e define as interrupções externas.
- `loop()`: Monitoriza o estado do sensor infravermelho para resetar o jogo.
- `buttonPressed()`: Função de callback que trata o *debounce* temporal antes de somar os pontos.
- `SomaContador()`: Incrementa a variável global de pontuação e atualiza a interface visual.

---
*Projeto desenvolvido voluntariamente para fins educacionais.*
