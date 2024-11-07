# Manual Completo: Sistema Contador Binario con Arduino
*Código original por Mgs. Stalin Arciniegas*

## Índice
1. Introducción
2. Objetivos
3. Fundamentos Teóricos
4. Componentes y Materiales
5. Desarrollo Técnico
6. Código Comentado
7. Resolución de Problemas
8. Referencias

## 1. Introducción

Este manual de estudio está diseñado para introducir a los estudiantes en el mundo de la programación con Arduino a través de un proyecto práctico de contador binario. El proyecto integra conceptos fundamentales de electrónica digital y programación, presentando una aplicación real que combina hardware y software.

El contador binario es un ejemplo perfecto para comprender los principios básicos de los sistemas digitales, la manipulación de bits y la interacción con componentes electrónicos. A través de este proyecto, los estudiantes aprenderán cómo implementar un sistema que responde a entradas del usuario (mediante un pulsador) y muestra información en formato binario utilizando LEDs.

Este material didáctico está estructurado de manera progresiva, comenzando con conceptos básicos y avanzando hacia aspectos más complejos de la programación en Arduino, permitiendo una comprensión integral del sistema.

## 2. Objetivos

### 2.1 Objetivo General
- Comprender e implementar un sistema de contador binario utilizando la plataforma Arduino, integrando conceptos de programación y electrónica digital.

### 2.2 Objetivos Específicos
1. **Conceptuales**
   - Entender los principios básicos de la programación en Arduino
   - Comprender el funcionamiento de las variables y tipos de datos en C++
   - Asimilar los conceptos de sistemas binarios y su representación

2. **Procedimentales**
   - Implementar correctamente el control de entradas y salidas digitales
   - Desarrollar habilidades en la conexión de componentes electrónicos básicos
   - Manejar operaciones con bits y conversiones de tipos de datos

3. **Técnicos**
   - Configurar adecuadamente los pines de Arduino para diferentes funciones
   - Implementar técnicas de control de rebotes en pulsadores
   - Utilizar efectivamente las estructuras de control en programación

## 3. Fundamentos Teóricos

### 3.1 Variables y Tipos de Datos
- **int**: Números enteros (count, Pulso, contador)
- **byte**: Tipo de dato de 8 bits (0-255)
- **array**: Colección de datos del mismo tipo (outArray)

### 3.2 Entradas y Salidas Digitales
- **pinMode()**: Configura los pines como entrada o salida
- **digitalWrite()**: Escribe valores HIGH (1) o LOW (0)
- **digitalRead()**: Lee el estado de un pin digital

### 3.3 Sistema Binario
- Representación de números en base 2
- Conversión entre decimal y binario
- Manipulación de bits

## 4. Componentes y Materiales

### 4.1 Hardware Necesario
- 1 Arduino (cualquier modelo)
- 4 LEDs
- 1 pulsador
- 4 resistencias de 220Ω (para LEDs)
- 1 resistencia de 10kΩ (para pulsador)
- Cables de conexión
- Protoboard

### 4.2 Conexiones
- LEDs:
  - Ánodo (+) → Resistencia 220Ω → Pines 8, 9, 10, 11
  - Cátodo (-) → GND
- Pulsador:
  - Terminal 1 → Pin 2
  - Terminal 1 → Resistencia 10kΩ → 5V
  - Terminal 2 → GND

## 5. Desarrollo Técnico

### 5.1 Configuración Inicial
```cpp
void setup() {
    // Configura los pines de salida para los LEDs
    for (count=0;count<4;count++) {
        pinMode(outArray[count], OUTPUT);
    }
    pinMode(Pulso, INPUT);
}
```

### 5.2 Funcionamiento Principal
1. **Detección del Pulsador**
   - Monitoreo constante del estado del pulsador
   - Activación del contador en flanco descendente

2. **Control de Rebotes**
   - Implementación de rutina anti-rebotes
   - Estabilización de la señal del pulsador

3. **Procesamiento**
   - Incremento del contador
   - Conversión a formato binario
   - Actualización de salidas

### 5.3 Visualización
- LED 1 (Pin 8): Bit menos significativo (LSB)
- LED 2 (Pin 9): Segundo bit
- LED 3 (Pin 10): Tercer bit
- LED 4 (Pin 11): Bit más significativo (MSB)

## 6. Código Completo Comentado
```cpp
/*
 * Contador Binario con Arduino
 * Autor: Mgs. Stalin Arciniegas
 * 
 * Este programa implementa un contador binario que se visualiza a través de LEDs
 * cuando se presiona un pulsador.
 */

// Declaración de variables globales
int count;                          // Variable para ciclos
int outArray[] = {8, 9, 10, 11};   // Pines de salida para LEDs
int Pulso = 2;                     // Pin para el botón pulsador
byte b;                            // Variable para conversión a binario
int contador;                      // Variable del contador principal

void setup() {
    // Configura los pines de salida para los LEDs
    for (count=0; count<4; count++) {
        pinMode(outArray[count], OUTPUT);
    }
    pinMode(Pulso, INPUT);
}

void loop() {
    if (!digitalRead(Pulso)==1) {
        do{
        }while(!digitalRead(Pulso)==1);
        delay(10);
        contador++;
        
        if (contador > 9) {
            contador = 0;
        }
        
        b=byte(contador);
        digitalWrite(outArray[0],bitRead(b,0));
        digitalWrite(outArray[1],bitRead(b,1));
        digitalWrite(outArray[2],bitRead(b,2));
        digitalWrite(outArray[3],bitRead(b,3));
    }
}
```

## 7. Resolución de Problemas Comunes

### 7.1 Problemas de Hardware
1. **LEDs no encienden**
   - Verificar polaridad de LEDs
   - Comprobar conexiones y resistencias
   - Verificar continuidad de cables

2. **Pulsador no responde**
   - Revisar conexión de resistencia pull-up
   - Verificar soldaduras o conexiones
   - Comprobar configuración del pin

### 7.2 Problemas de Software
1. **Contador irregular**
   - Revisar rutina de anti-rebotes
   - Verificar lógica del contador
   - Comprobar conversión de tipos

2. **Visualización incorrecta**
   - Verificar orden de bits
   - Comprobar array de pines
   - Revisar función bitRead()

## 8. Referencias

### 8.1 Documentación Técnica
- [Documentación oficial de Arduino](https://www.arduino.cc/reference/en/)
- [Tutorial de operaciones binarias](https://www.arduino.cc/en/Tutorial/BitMask)
- [Guía de buenas prácticas de programación](https://www.arduino.cc/en/Tutorial/BareMinimum)

### 8.2 Recursos Adicionales
- Hojas de datos de componentes
- Diagramas de conexión
- Ejemplos de código relacionados

---
*Este manual está basado en el código desarrollado por el Mgs. Stalin Arciniegas y está diseñado para proporcionar una comprensión profunda del funcionamiento de un contador binario con Arduino.*