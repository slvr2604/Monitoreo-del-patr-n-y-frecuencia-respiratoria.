# Monitoreo-del-patr-n-y-frecuencia-respiratoria.
Primera entrega de laboratorio instrumentación biomédica y biosensores BMED C. Grupo conformado por: 
Alissia Montealegre Quintero. 
Raul Alexander Peñuela Jimenez.
Silvia Lorena Vargas Rueda.


# Monitoreo del Patrón y Frecuencia Respiratoria

## Resumen

La respiración es un proceso fisiológico esencial que garantiza el intercambio de oxígeno y dióxido de carbono entre el organismo y el medio ambiente. El monitoreo de sus variables permite evaluar el estado funcional del sistema respiratorio y constituye una herramienta de gran utilidad en aplicaciones clínicas.

En esta práctica se diseñó un sistema de adquisición para registrar el patrón respiratorio de un individuo sano mediante un sensor resistivo sensible a la fuerza (**FSR402**), ubicado sobre la región toracoabdominal para detectar las variaciones de presión de contacto generadas durante la respiración.

La señal fue adquirida mediante una tarjeta **DAQ** y procesada en **MATLAB** para su visualización y análisis. Se realizaron registros en condiciones de reposo y durante el habla con el fin de comparar el comportamiento del patrón respiratorio y estimar la frecuencia respiratoria.

Además, se plantea el análisis de la señal en los dominios del tiempo y de la frecuencia para identificar las componentes dominantes y relacionar los resultados con la fisiología respiratoria.

---

# I. Introducción

La respiración es un proceso fisiológico fundamental para el mantenimiento de la vida, ya que permite el intercambio de oxígeno y dióxido de carbono entre el organismo y el medio externo, garantizando el aporte de oxígeno a los tejidos y la eliminación del dióxido de carbono producido por el metabolismo celular [1].

Debido a su importancia, la evaluación de la función respiratoria constituye una herramienta esencial para valorar el estado fisiológico de un individuo y detectar posibles alteraciones del sistema respiratorio [2].

Entre los principales parámetros respiratorios se encuentran:

- Frecuencia respiratoria.
- Volumen corriente.
- Volumen minuto.
- Patrón respiratorio.

Estos parámetros proporcionan información sobre el funcionamiento del sistema respiratorio y la respuesta del organismo frente a diferentes condiciones fisiológicas [2].

En particular, la frecuencia respiratoria es uno de los signos vitales de mayor utilidad clínica, ya que puede modificarse como consecuencia de cambios en la actividad física, el habla, el estrés o diversas patologías respiratorias [3].

Para el monitoreo de estos parámetros pueden medirse diferentes variables físicas relacionadas con el proceso respiratorio, como:

- Flujo de aire.
- Presión.
- Temperatura.
- Humedad.
- Movimientos de expansión y contracción torácica y abdominal.

La selección de la variable depende de la aplicación y del método de adquisición empleado [4].

Los sistemas de monitoreo no invasivos han cobrado especial importancia debido a que permiten registrar la actividad respiratoria sin generar molestias ni interferir con el proceso fisiológico normal [4].

En esta práctica se empleó un sensor **FSR402** ubicado sobre la región toracoabdominal para detectar las variaciones de fuerza de contacto producidas durante la expansión y contracción del cuerpo a lo largo del ciclo respiratorio.

### Objetivo

Desarrollar un sistema de adquisición capaz de registrar la señal respiratoria de un individuo sano mediante una tarjeta DAQ, procesarla en MATLAB y determinar la frecuencia respiratoria tanto en estado de reposo como durante el habla.

---

# II. Marco Teórico

## A. Fisiología de la respiración

La respiración es el proceso fisiológico mediante el cual el organismo obtiene oxígeno (O₂) del medio externo y elimina dióxido de carbono (CO₂), permitiendo mantener el metabolismo celular y el equilibrio de los gases sanguíneos [1].

Este proceso comprende:

1. Ventilación pulmonar.
2. Intercambio gaseoso alveolar.
3. Transporte de gases mediante el sistema circulatorio.
<img width="549" height="364" alt="image" src="https://github.com/user-attachments/assets/7dbcde89-96a2-4724-bf8a-5c9018667b01" />

### Inspiración

Durante la inspiración:

- El diafragma se contrae y desciende.
- Los músculos intercostales externos elevan la caja torácica.
- Aumenta el volumen torácico.
- Disminuye la presión intrapulmonar.
- Ingresa aire a los pulmones.

### Espiración

Durante la espiración:

- Los músculos respiratorios se relajan.
- Disminuye el volumen torácico.
- Aumenta la presión intrapulmonar.
- El aire sale de los pulmones.

Estos movimientos producen ciclos continuos de expansión y contracción que pueden detectarse mediante sensores ubicados sobre la superficie corporal [4].

---

## B. Parámetros respiratorios

### Frecuencia respiratoria (FR)

Número de ciclos respiratorios completos realizados en un minuto [2].

Valores normales en adultos sanos:

**12 – 20 respiraciones por minuto**

### Volumen corriente (VT)

Cantidad de aire que entra o sale de los pulmones durante una respiración normal [1].

### Volumen minuto (VE)

Cantidad total de aire movilizado en un minuto.

\[
VE = VT \times FR
\]

### Patrón respiratorio

Describe:

- Amplitud.
- Ritmo.
- Regularidad.

Puede modificarse por:

- Habla.
- Ejercicio físico.
- Estrés.
- Alteraciones fisiológicas.

---

## C. Variables físicas involucradas en la respiración

Las principales variables utilizadas para monitoreo respiratorio son:

### Flujo de aire

Permite analizar la ventilación pulmonar.

### Presión

Puede medirse en vías aéreas o pulmones para evaluar la mecánica ventilatoria.

### Temperatura y humedad

Varían entre inspiración y espiración.

### Movimiento torácico y abdominal

Producido por la acción del diafragma y músculos intercostales.

Estas variaciones mecánicas son las empleadas en esta práctica mediante el sensor FSR402.

---

## D. Sensores para el monitoreo respiratorio

Los sistemas respiratorios pueden utilizar:

### Sensores de flujo

Utilizados en:

- Espirómetros.
- Equipos de función pulmonar.

### Sensores de presión

Utilizados en:

- Ventilación mecánica.
- Aplicaciones clínicas.

### Sensores de temperatura

Detectan diferencias térmicas entre inspiración y espiración.

### Sensores de deformación y acelerómetros

Registran los movimientos torácicos y abdominales.

---

## E. Sensor FSR402

El **FSR402 (Force Sensing Resistor)** es un sensor resistivo sensible a la fuerza.

### Principio de funcionamiento

Su resistencia eléctrica disminuye cuando aumenta la fuerza aplicada.

### Características

- Bajo costo.
- Fácil integración.
- Flexible.
- Adecuado para detectar cambios de presión.

### Implementación

Se conecta normalmente mediante un divisor de voltaje.

Los cambios de resistencia generan cambios de voltaje que pueden ser adquiridos por una DAQ.

---

## F. Tarjeta de adquisición de datos (DAQ)

Una tarjeta DAQ permite:

- Adquirir señales analógicas.
- Convertirlas a formato digital.
- Procesarlas mediante software.

### Componentes principales

- Entradas analógicas.
- Entradas digitales.
- ADC (Convertidor Analógico-Digital).
- Interfaz de comunicación.

---

## G. MATLAB

MATLAB es una plataforma de cálculo numérico utilizada para:

- Adquisición de señales.
- Visualización.
- Filtrado.
- Procesamiento digital.
- Análisis espectral.

---

## H. Análisis en el dominio del tiempo y frecuencia

### Dominio del tiempo

Permite observar:

- Inspiración.
- Espiración.
- Amplitud.
- Regularidad.

### Dominio de la frecuencia

Se emplea la Transformada Rápida de Fourier (FFT).

La frecuencia dominante obtenida se relaciona directamente con la frecuencia respiratoria.

---

# III. Metodología

## A. Materiales

- Sensor FSR402.
- Tarjeta DAQ.
- Protoboard.
- Resistencia fija de 10 kΩ.
- Cables de conexión.
- Computador con MATLAB.
- Fuente de alimentación de 5 V.

---

## B. Montaje experimental

Se implementó un divisor de voltaje formado por:

- Sensor FSR402.
- Resistencia fija de 10 kΩ.

La resistencia fue seleccionada por:

- Adecuada sensibilidad.
- Protección del sensor.
- Compatibilidad con la DAQ.

El sensor se fijó sobre la región toracoabdominal para registrar los movimientos respiratorios.

---

## C. Adquisición de la señal respiratoria

Se realizaron dos registros:

### Condición 1: Reposo

El sujeto permaneció en reposo para obtener una señal estable.

### Condición 2: Habla

El sujeto habló continuamente durante la adquisición para analizar cambios en el patrón respiratorio.

Las señales fueron almacenadas para su posterior procesamiento.

---

# Referencias

[1] J. B. West and A. M. Luks, *West's Respiratory Physiology: The Essentials*, 11th ed. Wolters Kluwer, 2021.

[2] A. Nicolò, C. Massaroni, and E. Schena, "The Importance of Respiratory Rate Monitoring: From Healthcare to Sport and Exercise," *Sensors*, vol. 20, no. 21, 2020.

[3] World Health Organization, *Integrated Management of Childhood Illness (IMCI): Chart Booklet*, 2022.

[4] E. Vanegas, R. Igual, and I. Plaza, "Sensing Systems for Respiration Monitoring: A Technical Systematic Review," *Sensors*, vol. 20, no. 18, 2020.

[5] Interlink Electronics, *FSR® 400 Series Integration Guide*, Rev. 2023.

[6] D. L. Presti et al., "Respiratory Monitoring: A Review of Physiological Principles and Sensor Technologies," *Bioengineering*, vol. 8, no. 12, 2021.

[7] INTEF, "Procesos y tipos de respiración."

[8] D. L. Presti et al., "Respiratory Rate Monitoring Methods: A Review," *Sensors*, vol. 20, no. 21, 2020.

[9] National Instruments, *What Is Data Acquisition?*, 2024.

[10] MathWorks, *MATLAB Documentation – Signal Processing Toolbox*, 2024.

[11] S. W. Smith, *The Scientist and Engineer's Guide to Digital Signal Processing*.




