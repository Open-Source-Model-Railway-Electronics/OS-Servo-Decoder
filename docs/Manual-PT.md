> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; [🇪🇸 ES](Manual-ES.md) &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; 🇵🇹 PT

# Manual dos OS-Servo-Decoders

## 📘 Introdução
O OS-Servo-Decoder é um decoder de acessórios DCC simples e robusto concebido para accionar até 8 servomotores. Suporta ferrovias em miniatura modernas com opções de configuração flexíveis, módulos de relé externos para comutação de polaridade (opcional) e controlo directo por interruptores de entrada, comandos de acessório DCC e funções de locomotiva (F1–F8).

---

## 📚 Índice

- [Manual dos OS-Servo-Decoders](#manual-dos-os-servo-decoders)
  - [📘 Introdução](#-introdução)
  - [📚 Índice](#-índice)
  - [🔧 Características](#-características)
  - [🔌 Ligar o Decoder](#-ligar-o-decoder)
  - [💪 Controlar as Saídas de Servo](#-controlar-as-saídas-de-servo)
  - [🛠️ Modo de Configuração DCC](#️-modo-de-configuração-dcc)
  - [🛠️ Modo de Configuração por Botão](#️-modo-de-configuração-por-botão)
  - [🌟 Guardar Posições de Servo](#-guardar-posições-de-servo)
  - [🚗 Modos de Função de Locomotiva](#-modos-de-função-de-locomotiva)
  - [⚖️ Desvio de Endereço](#️-desvio-de-endereço)
  - [⏰ Modo de Comutação Automática](#-modo-de-comutação-automática)
  - [📊 Resumo](#-resumo)

---

## 🔧 Características
- Controla até 8 servos  
- Utiliza bornes de parafuso amovíveis para fácil cablagem  
- Módulos de relé externos  
- Suporta completamente:  
  - Movimento padrão de agulha  
  - Comutação de polaridade (onde suportado)  
  - Posições finais de servo ajustáveis (por botões)  
- Configuração autónoma: sem PC, CV nem programadores necessários  
- Controlo opcional por funções de locomotiva DCC (F1–F18)  
- Suporta desvio de 4 endereços da Roco  

---

## 🔌 Ligar o Decoder

![OS-Servo-Decoder-8 com diferentes configurações de extensão de relé](board_w_extensions.png)

*O OS-Servo-Decoder-8 mostrado com vários módulos de extensão de relé ligados (em cima à esquerda: relés de retenção; em cima à direita: relés de uso geral; em baixo: combinações com servos ligados).*

O OS-Servo-Decoder-8 utiliza o mesmo esquema de cablagem que o OS-Solenoid-Decoder:

- **Header superior (POW / DCC):** Ligue tensão de via DCC ou uma fonte de alimentação DC (máx. 19 V)
- ⚠️ **Importante:** Não utilize tensão AC — isto danificará o decoder
- **Headers de servo (lado direito):** Ligue cada servomotor ao conector de 3 pinos
  - Pinagem padrão: **GND — +5 V — Sinal**
- **Conectores de relé (lado esquerdo):** A, COM, B — para módulos de extensão de relé OS

---

## 💪 Controlar as Saídas de Servo

Cada saída de servo é controlada por um endereço de acessório DCC. Quando o decoder recebe um comando DCC para um endereço atribuído, move o servo suavemente para a posição guardada para esse estado de comando (DIRECTO ou CURVO).

- O comando **DIRECTO** move o servo para a sua posição final de direito guardada.
- O comando **CURVO** move o servo para a sua posição final de curvo guardada.
- Se estiverem instalados módulos de extensão de relé, os contactos do relé comutam em sincronia com o servo para a polarização de frog.

As posições finais do servo são guardadas usando teclas de função de locomotiva — consulte [Guardar Posições de Servo](#-guardar-posições-de-servo) abaixo.

---

## 🛠️ Modo de Configuração DCC

O decoder suporta um modo de configuração que funciona inteiramente a partir do seu manípulo DCC — sem computador, sem programador de CV.

Para entrar no modo de configuração, seleccione o endereço de locomotiva **9999** no seu manípulo e coloque **F0, F1 e F2 todas a OFF**. O decoder entra no modo de configuração e aceita comandos de teclas de função.

Estando no modo de configuração, use as teclas de função (F1–F8) para definir opções conforme descrito nas secções abaixo. Prima **F0 = OFF** para sair e regressar ao funcionamento normal.

---

## 🛠️ Modo de Configuração por Botão

A placa tem dois botões físicos: **CONFIGURE** e **TOGGLE**.

- **CONFIGURE** — entra no modo de configuração directamente, sem necessidade de um manípulo. O decoder responde com indicação LED indicando a configuração activa.
- **TOGGLE** — comuta manualmente a saída de servo actualmente seleccionada entre as suas duas posições guardadas. Útil para testar o movimento e ajustar as posições finais.

---

## 🌟 Guardar Posições de Servo
No Modo de Execução, utilize estas funções para programar:

- **F1 = ON ➔** Guardar posição actual como *CURVO*  
- **F2 = ON ➔** Guardar posição actual como *DIRECTO*  
- **F3 = ON ➔** Inverter relé de frog *(apenas no modelo de 6 relés)*  
- **F0 = OFF ➔** Sair do Modo de Execução  

---

## 🚗 Modos de Função de Locomotiva
No Modo de Configuração, pode escolher controlar o decoder usando teclas de função de locomotiva em vez de comandos de acessório.

- **F4 = ON ➔** Desactivar controlo por locomotiva *(predefinição)*  
- **F5 = ON ➔** Activar modo de função de locomotiva *(F1–F8)* — usa 1 endereço  
- **F6 = ON ➔** Activar modo de 4 funções *(F1–F4)* — usa 2 endereços  

Isto permite uma comutação ultra-rápida com manípulos como o Roco Lokmaus ou Multimaus.

---

## ⚖️ Desvio de Endereço
Para compensar o desvio de 4 endereços da Roco, utilize:

- **F7 = ON ➔** Activar desvio de 4 endereços  

---

## ⏰ Modo de Comutação Automática
Activar a comutação automática de um motor seleccionado:

- **F8 = ON ➔** O motor comuta de 5 em 5 segundos  
  - A velocidade é controlada pelo manípulo  
  - A direcção do manípulo não interessa  
  - Manípulo 0 = lento, Máximo = rápido  

Neste modo, o motor deixa de estar subordinado às teclas de função do manípulo.

---

## 📊 Resumo
- Use os botões para configuração directa e ajuste do servo  
- Use o endereço de locomotiva DCC **9999** com **F0, F1, F2 OFF** para entrar no modo de configuração  
- Use **F1/F2** para guardar posições de servo  
- Use **F4–F8** para activar o controlo por função de locomotiva, o desvio de endereço ou os modos de comutação  

Todos os OS-Servo-Decoders partilham esta interface e lógica.  
Sem computador. Sem CVs. Basta ligar, endereçar e utilizar.
