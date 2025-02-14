# Projeto de Controle de LEDs e Display com Joystick no Raspberry Pi Pico

Este projeto utiliza um Raspberry Pi Pico para controlar LEDs e um display OLED com base nos movimentos de um joystick. O projeto inclui a leitura de entradas analógicas do joystick, o controle de LEDs PWM e a exibição de informações em um display SSD1306.

## Funcionalidades

- **Controle de LEDs**:
  - Um LED verde é controlado diretamente por um botão no joystick.
  - LEDs azul e vermelho são controlados por PWM com base na posição do joystick.
- **Display OLED**:
  - Exibe um quadrado que se move de acordo com a posição do joystick.
  - Mostra mensagens de status dos LEDs quando o botão A é pressionado.
- **Debouncing**:
  - Implementa debouncing para evitar leituras falsas dos botões.

## Hardware Necessário

- Raspberry Pi Pico
- Joystick analógico
- Display OLED SSD1306 (128x64)
- LEDs (verde, azul, vermelho)
- Resistores adequados para os LEDs
- Botões (opcional, para testes adicionais)

## Conexões

| Componente        | Pino no Pico |
|-------------------|--------------|
| Joystick (Eixo X) | GPIO 26      |
| Joystick (Eixo Y) | GPIO 27      |
| Botão do Joystick | GPIO 22      |
| Botão A           | GPIO 5       |
| LED Verde         | GPIO 11      |
| LED Azul          | GPIO 12      |
| LED Vermelho      | GPIO 13      |

## Configuração do Ambiente

1. **Instale o SDK do Raspberry Pi Pico**:
   - Siga as instruções no [repositório oficial do Raspberry Pi Pico SDK](https://github.com/raspberrypi/pico-sdk).

2. **Clone este repositório**:

   ```bash
   git clone https://github.com/msantana-01/conversores_AD
   cd conversores_AD
   ```

3. **Configure o projeto**:
   - Certifique-se de que o `pico-sdk` está configurado corretamente no seu ambiente.
   - Crie um diretório `build` e configure o CMake:

     ```bash
     mkdir build
     cd build
     cmake ..
     ```

4. **Compile o projeto**:

   ```bash
   make
   ```

5. **Carregue o firmware no Pico**:
   - Conecte o Raspberry Pi Pico ao computador via USB.
   - Pressione o botão `BOOTSEL` no Pico enquanto o conecta para colocá-lo no modo de armazenamento em massa.
   - Copie o arquivo `.uf2` gerado para o Pico.

## Uso

1. **Inicialização**:
   - Ao ligar o Pico, o display mostrará a mensagem "MOVA O JOYSTICK".
   - Mova o joystick para iniciar a interface.

2. **Controle dos LEDs**:
   - O LED verde é alternado ao pressionar o botão do joystick.
   - Os LEDs azul e vermelho mudam de brilho com base na posição do joystick.
   - O botão A alterna o estado dos LEDs PWM (ligado/desligado).

3. **Display**:
   - Um quadrado é movido no display de acordo com a posição do joystick.
   - A borda do display muda de estilo ao pressionar o botão do joystick.

## Estrutura do Código

- **`main.c`**: Contém a lógica principal do projeto, incluindo a leitura do joystick, controle dos LEDs e atualização do display.
- **`display.h`**: Biblioteca para controlar o display OLED SSD1306.
- **Pinos e constantes**: Definidos no início do código para facilitar a modificação.

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou pull requests para melhorias, correções de bugs ou novas funcionalidades.
