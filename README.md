# 🔧 FSE-UnB — Projetos da Disciplina Fundamentos de Sistemas Embarcados (2025/1)

Este repositório reúne os dois projetos desenvolvidos na disciplina **Fundamentos de Sistemas Embarcados (FSE)** da Universidade de Brasília (UnB).  
Cada projeto explora conceitos fundamentais de sistemas embarcados, envolvendo sensores, atuadores, protocolos de comunicação, controle, interface homem-máquina e estratégias de otimização de energia.

Os projetos incluídos são:

1. **Escape Room IoT com ESP32 e MQTT**  
2. **Máquina de Raio-X com controle PID, encoders e comunicação MODBUS**

---

## 📁 Estrutura do Repositório

| Pasta         | Projeto                                                                                     |
|---------------|---------------------------------------------------------------------------------------------|
| `escape_room` | Escape Room IoT baseado em ESP32, MQTT e ThingsBoard                                       |
| `raio_x`      | Máquina de Raio-X com motores DC, encoders, GPIO, PWM, PID e comunicação MODBUS/UART        |

---

# 🕹️ Projeto 1 — Escape Room IoT (ESP32 + MQTT + ThingsBoard)

O **Escape Room IoT** é um sistema interativo composto por múltiplas missões embarcadas.  
Cada missão utiliza sensores e atuadores conectados ao ESP32, que se comunica com a plataforma ThingsBoard via protocolo **MQTT**.  
O usuário deve resolver desafios físicos, enquanto o sistema envia telemetria, recebe comandos via RPC e mantém o gerenciamento dos estados do jogo.

### 🚀 Tecnologias e Conceitos Utilizados

- ESP32 (ESP-IDF)
- Protocolo MQTT (Mosquitto / ThingsBoard)
- Sensores e atuadores:
  - Sensor de som  
  - Sensor de botão
  - Sensor hall magnético
  - Sensor de Temperatura
  - Encoder rotativo  
  - LED RGB  
  - Buzzer ativo
  - Tela OLED (I2C)  
- RPC para controle remoto
- Armazenamento não volátil (NVS)
- Modos de energia: **Energy Mode** e **Battery Mode**
- Dashboards e visualizações no ThingsBoard

### 🧩 Missões Implementadas

- **Missão 1 – Sound of Silence**  
  O jogador deve emitir um som alto para ativar a missão. O LED RGB e o buzzer fornecem feedback indicando sucesso ou erro.

- **Missão 2 – Stayin’ Alive**  
  O jogador pressiona o botão um número específico de vezes conforme instrução exibida, simulando uma interação rítmica inspirada na música Stayin’ Alive.

- **Missão 3 – Magnetized**  
  O jogador aproxima um ímã do sensor Hall para completar a missão. Cada aproximação representa uma etapa do desafio.

- **Missão 4 – Twist and Shout**  
  O jogador deve girar o encoder rotativo por um número definido de voltas. Quando atingido o valor correto, a missão é concluída.

- **Missão 5 – Summertime Sadness**  
  A missão envolve a leitura da temperatura ambiente. Um valor acima ou abaixo do limiar desencadeia a interação prevista para a fase.


---

# 🩻 Projeto 2 — Máquina de Raio-X (Controle PID, Encoders e MODBUS)

Este projeto implementa o controle de uma **máquina de Raio-X com dois graus de liberdade**, empregando conceitos avançados de sistemas embarcados e integração modular.

### ⚙️ Componentes Principais

- Motores DC  
- Encoders de quadratura  
- Sensores de fim de curso  
- Controle de direção via GPIO  
- Controle de velocidade via PWM  
- Controle de posição com algoritmo PID  
- Comunicação com tela touch via **MODBUS/UART**
- Tratamento de sinais (SIGINT)  

### 📦 Arquitetura do Código

- `botoesfisicos.c / .h` — Leitura dos botões físicos e ações diretas  
- `encoder.c / .h` — Leitura e processamento dos encoders quadratura  
- `motor.c / .h` — Controle de motores (PWM, velocidade, direção)  
- `pid.c / .h` — Implementação completa do controlador PID  
- `modbus.c / .h` — Empacotamento e desempacotamento MODBUS + CRC  
- `gpio.c / .h` — Controle baixo nível dos pinos  
- `main.c` — Loop principal, integração entre módulos e lógica operacional  

### 🔩 Funcionalidades

- Controle de posição suave e preciso usando PID  
- Monitoramento contínuo via encoders  
- Segurança por sensores de fim de curso  
- Interface com tela touch (modos manual e automático)  
- Execução robusta com tratamento de interrupções  
- Pacotes MODBUS com verificação de integridade (CRC)

### 🎯 Objetivo Geral

Reproduzir o comportamento de uma máquina de Raio-X real, assegurando:

- Precisão no posicionamento  
- Segurança operacional  
- Modularidade do código  
- Arquitetura clara e escalável  

