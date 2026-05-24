> 🌐 &nbsp; [🇬🇧 EN](Manual-EN.md) &nbsp;|&nbsp; [🇩🇪 DE](Manual-DE.md) &nbsp;|&nbsp; [🇫🇷 FR](Manual-FR.md) &nbsp;|&nbsp; [🇳🇱 NL](Manual-NL.md) &nbsp;|&nbsp; 🇪🇸 ES &nbsp;|&nbsp; [🇮🇹 IT](Manual-IT.md) &nbsp;|&nbsp; [🇵🇱 PL](Manual-PL.md) &nbsp;|&nbsp; [🇨🇿 CS](Manual-CS.md) &nbsp;|&nbsp; [🇩🇰 DA](Manual-DA.md) &nbsp;|&nbsp; [🇳🇴 NO](Manual-NO.md) &nbsp;|&nbsp; [🇸🇪 SV](Manual-SV.md) &nbsp;|&nbsp; [🇭🇺 HU](Manual-HU.md) &nbsp;|&nbsp; [🇵🇹 PT](Manual-PT.md)

# Manual del OS-Servo-Decoder

## 📘 Introducción
El OS-Servo-Decoder es un decodificador de accesorios DCC sencillo y robusto diseñado para accionar hasta 8 servomotores. Ofrece opciones de configuración flexibles para maquetas de ferrocarril modernas, módulos de relé externos para conmutación de polaridad (opcional) y control directo mediante interruptores de entrada, comandos de accesorio DCC y funciones de locomotora (F1–F8).

---

## 📚 Tabla de Contenidos

- [Manual del OS-Servo-Decoder](#manual-del-os-servo-decoder)
  - [📘 Introducción](#-introducción)
  - [📚 Tabla de Contenidos](#-tabla-de-contenidos)
  - [🔧 Características](#-características)
  - [🔌 Conexión del Decodificador](#-conexión-del-decodificador)
  - [💪 Control de las Salidas de Servo](#-control-de-las-salidas-de-servo)
  - [🛠️ Modo de Configuración DCC](#️-modo-de-configuración-dcc)
  - [🛠️ Modo de Configuración por Botón](#️-modo-de-configuración-por-botón)
  - [🌟 Almacenamiento de Posiciones de Servo](#-almacenamiento-de-posiciones-de-servo)
  - [🚗 Modos de Función de Locomotora](#-modos-de-función-de-locomotora)
  - [⚖️ Desplazamiento de Dirección](#️-desplazamiento-de-dirección)
  - [⏰ Modo de Alternancia Automática](#-modo-de-alternancia-automática)
  - [📊 Resumen](#-resumen)

---

## 🔧 Características
- Controla hasta 8 servos  
- Utiliza bornes de tornillo enchufables para un cableado sencillo  
- Módulos de relé externos  
- Compatible completamente con:  
  - Movimiento estándar de agujas  
  - Conmutación de polaridad (donde sea compatible)  
  - Posiciones finales de servo ajustables (mediante botones)  
- Configuración autónoma: no requiere PC, CV ni programadores  
- Control opcional mediante funciones de locomotora DCC (F1–F18)  
- Compatible con el desplazamiento de 4 direcciones de Roco  

---

## 🔌 Conexión del Decodificador

![OS-Servo-Decoder-8 con diferentes configuraciones de extensión de relé](board_w_extensions.png)

*El OS-Servo-Decoder-8 mostrado con varios módulos de extensión de relé enchufados (arriba izquierda: relés enclavados; arriba derecha: relés de uso general; abajo: combinaciones con servos conectados).*

El OS-Servo-Decoder-8 utiliza el mismo esquema de cableado que el OS-Solenoid-Decoder:

- **Cabezal superior (POW / DCC):** Conecte la tensión de vía DCC o una fuente de alimentación DC (máx. 19 V)
- ⚠️ **Importante:** No use tensión AC — esto dañará el decodificador
- **Cabezales de servo (lado derecho):** Conecte cada servomotor al conector de 3 pines
  - Patillaje estándar: **GND — +5 V — Señal**
- **Conectores de relé (lado izquierdo):** A, COM, B — para módulos de extensión de relé OS

---

## 💪 Control de las Salidas de Servo

Cada salida de servo se controla mediante una dirección de accesorio DCC. Cuando el decodificador recibe un comando DCC para una dirección asignada, mueve el servo suavemente hasta la posición almacenada para ese estado de comando (RECTO o CURVO).

- El comando **RECTO** mueve el servo a su posición final recta almacenada.
- El comando **CURVO** mueve el servo a su posición final curva almacenada.
- Si hay módulos de extensión de relé instalados, los contactos del relé conmutan en sincronía con el servo para la polarización del frog.

Las posiciones finales del servo se almacenan usando las teclas de función de locomotora — véase [Almacenamiento de Posiciones de Servo](#-almacenamiento-de-posiciones-de-servo) a continuación.

---

## 🛠️ Modo de Configuración DCC

El decodificador admite un modo de configuración que funciona completamente desde su mando DCC — sin ordenador, sin programador de CV.

Para entrar en el modo de configuración, seleccione la dirección de locomotora **9999** en su mando y ponga **F0, F1 y F2 en OFF**. El decodificador entrará en el modo de configuración y aceptará comandos de tecla de función.

Una vez en el modo de configuración, use las teclas de función (F1–F8) para establecer opciones según se describe en las secciones siguientes. Pulse **F0 = OFF** para salir y volver al funcionamiento normal.

---

## 🛠️ Modo de Configuración por Botón

La placa tiene dos botones físicos: **CONFIGURE** y **TOGGLE**.

- **CONFIGURE** — entra en el modo de configuración directamente, sin necesidad de mando. El decodificador responde con indicación LED que muestra el ajuste activo.
- **TOGGLE** — alterna manualmente la salida de servo seleccionada actualmente entre sus dos posiciones almacenadas. Útil para probar el movimiento y ajustar las posiciones finales.

---

## 🌟 Almacenamiento de Posiciones de Servo
En el Modo de Funcionamiento, use estas funciones para programar:

- **F1 = ON ➔** Guardar posición actual como *CURVO*  
- **F2 = ON ➔** Guardar posición actual como *RECTO*  
- **F3 = ON ➔** Invertir el relé de frog *(solo modelo de 6 relés)*  
- **F0 = OFF ➔** Salir del Modo de Funcionamiento  

---

## 🚗 Modos de Función de Locomotora
En el Modo de Configuración, puede elegir controlar el decodificador usando teclas de función de locomotora en lugar de comandos de accesorio.

- **F4 = ON ➔** Deshabilitar control por locomotora *(predeterminado)*  
- **F5 = ON ➔** Habilitar modo de función de locomotora *(F1–F8)* — usa 1 dirección  
- **F6 = ON ➔** Habilitar modo de 4 funciones *(F1–F4)* — usa 2 direcciones  

Esto permite una conmutación ultrarrápida usando mandos como el Roco Lokmaus o el Multimaus.

---

## ⚖️ Desplazamiento de Dirección
Para compensar el desplazamiento de 4 de Roco, use:

- **F7 = ON ➔** Habilitar desplazamiento de 4 direcciones  

---

## ⏰ Modo de Alternancia Automática
Habilite la alternancia automática de un motor seleccionado:

- **F8 = ON ➔** El motor alterna cada 5 segundos  
  - La velocidad se controla con el regulador  
  - La dirección del regulador no importa  
  - Regulador 0 = lento, Máximo = rápido  

En este modo, el motor ya no está subordinado a las teclas de función del regulador.

---

## 📊 Resumen
- Use los botones para la configuración directa y el ajuste del servo  
- Use la dirección de locomotora DCC **9999** con **F0, F1, F2 en OFF** para entrar en el modo de configuración  
- Use **F1/F2** para almacenar las posiciones del servo  
- Use **F4–F8** para habilitar el control por función de locomotora, el desplazamiento de dirección o los modos de alternancia  

Todos los OS-Servo-Decoders comparten esta interfaz y lógica.  
No se necesita ordenador. Sin CV. Solo cable, dirección y puesta en marcha.
