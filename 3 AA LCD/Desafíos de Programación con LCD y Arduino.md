# Desafíos de Programación con LCD y Arduino

## Nivel Medio

### Desafío 1: Contador Binario Visual
**Objetivo:** Crear un contador binario que muestre el valor en LCD y en LEDs simultáneamente.

**Componentes:**
- Arduino UNO R4 WiFi
- LCD 16x2
- 8 LEDs
- 2 botones (incremento/decremento)
- Resistencias necesarias

**Requisitos:**
- Mostrar en LCD el valor decimal y binario
- Los LEDs deben representar el número en binario
- Botones para incrementar/decrementar
- Rango: 0-255

**Ejemplo de visualización:**
```
Dec: 42
Bin: 00101010
```

### Desafío 2: Cronómetro con Pausas
**Objetivo:** Implementar un cronómetro con control de usuario y visualización dual.

**Componentes:**
- Arduino UNO R4 WiFi
- LCD 16x2
- Display 7 segmentos de 4 dígitos
- 3 botones (inicio/pausa/reinicio)

**Requisitos:**
- LCD: Mostrar minutos y segundos con mensaje de estado
- Display 7 segmentos: Mostrar centésimas
- Botones para control de cronómetro
- Indicación de estado (Corriendo/Pausado)

**Ejemplo LCD:**
```
Tiempo: 02:45
Estado: CORRIENDO
```

### Desafío 3: Monitor de Interruptores
**Objetivo:** Crear un panel de monitoreo de estados múltiples.

**Componentes:**
- Arduino UNO R4 WiFi
- LCD 16x2
- 6 interruptores
- LEDs indicadores

**Requisitos:**
- Mostrar estado de cada interruptor en LCD
- Actualización en tiempo real
- Contador de cambios de estado
- Alertar cuando más de 3 están activos

**Ejemplo LCD:**
```
SW: ▮▯▮▯▮▯
Cambios: 042
```

## Nivel Alto

### Desafío 4: Calculadora Científica con Memoria
**Objetivo:** Desarrollar una calculadora científica utilizando teclado matricial con sistema de memoria.

**Componentes:**
- Arduino UNO R4 WiFi
- LCD 16x2
- Teclado matricial 4x4
- Display 7 segmentos (4 dígitos)
- Potenciómetro para ajuste de contraste LCD

**Requisitos:**
1. **Funciones Básicas:**
   - Operaciones aritméticas básicas
   - Funciones científicas (sqrt, pow, sin, cos)
   - Sistema de memoria (M+, M-, MR, MC)
   - Historial de operaciones

2. **Interfaz:**
   ```
   123.45 + 67.89
   Ans = 191.34
   ```

3. **Características Avanzadas:**
   - Modo de conversión de unidades
   - Sistema hexadecimal/binario
   - 5 memorias independientes
   - Detección de errores matemáticos

### Desafío 5: Juego de Memoria Secuencial
**Objetivo:** Desarrollar un juego tipo "Simon Says" con múltiples displays.

**Componentes:**
- Arduino UNO R4 WiFi
- LCD 16x2
- Display 7 segmentos
- 4 botones de colores
- 4 LEDs de colores
- Buzzer

**Requisitos:**
- Generar secuencias aleatorias
- Mostrar puntaje en display 7 segmentos
- LCD para instrucciones y estado
- Diferentes niveles de dificultad
- Efectos de sonido
- Modo de alta puntuación
- Tiempo límite por nivel

**Características Adicionales:**
- Modo práctica
- Velocidad ajustable
- Registro de mejores puntuaciones