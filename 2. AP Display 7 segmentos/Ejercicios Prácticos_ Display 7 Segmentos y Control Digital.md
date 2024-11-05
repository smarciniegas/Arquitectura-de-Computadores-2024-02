# Ejercicios Prácticos: Display 7 Segmentos y Control Digital

## Nivel Básico

### Ejercicio 1: Contador Ascendente Simple
**Objetivo:** Realizar un contador ascendente del 0 al 9 y mostrar la palabra PUCE.
**Especificaciones:**
- Pulsador conectado al pin 3
- Incremento en flanco descendente del pulsador
- Visualización alternada entre número y palabra PUCE

### Ejercicio 2: Contador Descendente Simple
**Objetivo:** Realizar un contador descendente del 0 al 9 y mostrar la palabra PUCE.
**Especificaciones:**
- Pulsador conectado al pin 3
- Incremento en flanco ascendente del pulsador
- Visualización alternada entre número y palabra PUCE

## Nivel Intermedio

### Ejercicio 3: Contador Bidireccional con Interruptor
**Objetivo:** Implementar un contador ascendente y descendente del 0 al 9 con mensaje "HOLA PUCE".
**Especificaciones:**
- Control mediante pulsador e interruptor
- Interruptor abierto → Modo ascendente
- Interruptor cerrado → Modo descendente
- Visualización alternada entre número y mensaje

### Ejercicio 4: Contador Ascendente de Dos Dígitos
**Objetivo:** Realizar un contador ascendente del 0 al 99.
**Especificaciones:**
- Pulsador conectado al pin 3
- Incremento en flanco descendente
- Visualización de dos dígitos

### Ejercicio 5: Contador Bidireccional de Dos Dígitos
**Objetivo:** Implementar un contador ascendente y descendente del 0 al 99.
**Especificaciones:**
- Dos pulsadores independientes
- Un pulsador para incremento
- Un pulsador para decremento

## Nivel Avanzado

### Ejercicio 6: Sistema Multi-Modo con Display 7 Segmentos
**Objetivo:** Desarrollar un sistema de visualización con múltiples modos de operación.

**Especificaciones de Modos:**
1. **Modo 00:** Contador normal (0-9)
2. **Modo 01:** Contador par (0,2,4,6,8)
3. **Modo 10:** Contador impar (1,3,5,7,9)
4. **Modo 11:** Secuencia especial (PUCE)

**Control del Sistema:**
- **Pulsador 1 (Pin 2):**
  - Función: Control de conteo ascendente
  - Activación: Flanco descendente
- **Pulsador 2 (Pin 3):**
  - Función: Control de conteo descendente
  - Activación: Flanco ascendente
- **Pulsador 3 (Pin 4):**
  - Función: RESET en modos de conteo
  - Función adicional: Control de secuencia especial

**Requisitos Generales para Todos los Ejercicios:**
1. Implementar anti-rebote en pulsadores
2. Utilizar resistencias pull-up/pull-down según corresponda
3. Documentar conexiones en el código
4. Optimizar el código para evitar retardos innecesarios

**Recomendaciones:**
1. Probar exhaustivamente cada modo antes de pasar al siguiente
2. Verificar el correcto funcionamiento de los flancos
3. Implementar variables de estado para seguimiento
4. Comentar el código adecuadamente

**Criterios de Evaluación:**
- Funcionamiento correcto según especificaciones
- Calidad y organización del código
- Implementación adecuada de control de pulsadores
- Manejo correcto de visualización en display

**Nota:** Todos los ejercicios deben incluir el código fuente comentado y un diagrama de conexiones.