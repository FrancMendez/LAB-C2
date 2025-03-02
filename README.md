# Universisdad Mariano Galvez- Emprendimiento Innovacion Y Proyectos - Francisco Josue Mendez Suriano 091-14-9796
Laboratorio C2 
# Análisis de circuitos con compuertas digitales, seáles en el tiempo, Glitches en Circuitos Lógicos

## Introducción
Los glitches en circuitos lógicos son pulsos no deseados que pueden afectar el funcionamiento de sistemas digitales. Estos errores ocurren debido a diferencias en los tiempos de propagación de las compuertas lógicas. En este documento, analizaremos un circuito que genera glitches, explicaremos por qué ocurren y cómo se pueden mitigar sus efectos.

## Análisis del Circuito
El circuito analizado consta de:
- **Dos inversores** en las entradas A y B.
- **Dos compuertas AND**.
- **Una compuerta OR** para la salida final.

### Funcionamiento
1. **Inversión de señales:** Los valores de A y B se invierten antes de ser procesados por la primera AND.
2. **Procesamiento en las AND:** Una AND recibe los valores invertidos de A y B, mientras que la otra AND recibe B y C directamente.
3. **Salida OR:** Ambas salidas de las AND se combinan en una compuerta OR para generar Y.

### Causa del Glitch
Los glitches ocurren debido a los tiempos de propagación distintos en las compuertas. Cuando A o B cambian de estado, los inversores tardan en actualizar sus salidas. Durante ese breve instante, la lógica combinacional de las AND y OR puede generar pulsos espurios en la salida.

## Simulación del Circuito
Para comprobar la generación del glitch, se recomienda:
1. **Diseñar el circuito en un simulador** como LTSpice o Logisim.
2. **Aplicar señales de entrada con transiciones rápidas** en A o B.
3. **Usar un osciloscopio** para visualizar los pulsos inesperados en la salida Y.

## Documentación de Ejercicios

### Ejercicio 1
**Video explicativo:** [YouTube](https://youtu.be/uEpsjXD6EYI)

### Ejercicio 2
**Video explicativo:** [YouTube](https://youtu.be/lhvAfLoD9Ms)

#### Selección de Compuertas Lógicas en Digi-Key
Se seleccionó la compuerta **SN74LVC1G08DBVR** de Texas Instruments, una compuerta AND de 1 canal y 2 entradas que opera en un rango de voltaje de 1.65V a 5.5V, adecuada para operaciones a 1.8V. Su encapsulado es **SOT-23-5**, ideal para montaje en superficie.

#### Cálculo del Margen de Ruido (Noise Margin)
**Parámetros clave:**
- VOH (Salida alta mínima): 1.65V
- VOL (Salida baja máxima): 0.15V
- VIH (Entrada alta mínima): 1.2V
- VIL (Entrada baja máxima): 0.6V

Fórmulas:
- NMH = VOH - VIH = 1.65V - 1.2V = 0.45V
- NML = VIL - VOL = 0.6V - 0.15V = 0.45V

**Resultados:**
- Margen de ruido alto (NMH): **0.45V**
- Margen de ruido bajo (NML): **0.45V**

#### Operación en la Zona Prohibida (Forbidden Zone)
Se simula una compuerta en **LTSpice** con:
- **Operación normal**: Entrada a **5VDC**
- **Zona prohibida**: Entrada a **3VDC**

**Resultados:**
- En la zona prohibida (1.5V - 3.5V), la salida de la compuerta AND se vuelve inestable.
- Se observan oscilaciones y errores lógicos que pueden afectar el circuito digital.

## Simulación de un Sumador Completo de 1 Bit
**Cálculo del Retardo de Propagación:**
- **Para S:** Pasa por dos XOR → **tPD = 2ps + 2ps = 4ps**
- **Para C:** Pasa por dos AND y una OR → **tPD = 2ps + 2ps + 2ps = 6ps**

**Resultados:**
- Contamination Delay: **tCD = 1ps**
- Propagation Delay: **tPD = 6ps**

## Simulación de un Glitch
Se replica el circuito que genera un glitch y se observa cómo las señales no llegan al mismo tiempo, lo que produce ruido en la salida.

**Resultados de Simulación:**
- Retardo a **10ms**: Glitch detectado.
- Retardo a **150ms**: Mayor estabilidad.
- Implementando estrategias de sincronización (flip-flops, buffers): Reducción del glitch.

## Conclusión Final
El circuito analizado demuestra cómo un diseño sin considerar retardos puede generar glitches, los cuales afectan el funcionamiento correcto de un sistema digital. Simular y optimizar los circuitos es esencial para garantizar su fiabilidad en aplicaciones reales.

**Soluciones para evitar glitches:**
- Uso de compuertas con tiempos de propagación uniformes.
- Aplicación de flip-flops o buffers para sincronizar señales.
- Diseño con redundancia para minimizar transiciones no deseadas.

