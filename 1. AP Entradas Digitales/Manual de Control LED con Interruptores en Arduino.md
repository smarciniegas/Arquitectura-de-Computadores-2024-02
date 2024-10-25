# Manual para Estudiante: Control de LED con 2 Interruptores en Arduino

## 1. Introducción
Este manual guía a los estudiantes en la creación de un programa para Arduino que controla un LED utilizando dos interruptores. Este ejercicio es fundamental para comprender el control de entradas y salidas digitales en Arduino.

## 2. Diagrama de Conexión
```
Arduino   Componentes
Pin 13 -----> LED (ánodo)
Pin 7  -----> Switch 1
Pin 6  -----> Switch 2
GND   -----> LED (cátodo) y Switch (común)
```

## 3. Código Comentado
```cpp
// Definición de pines
int led = 13;    // pin 13 asignamos nombre "led"
int S1 = 7;      // pin 7 switch 1
int S2 = 6;      // pin 6 switch 2
int var;         // declaramos una variable

void setup()
{
  pinMode(led, OUTPUT);   // declaramos al led como salida digital
  pinMode(S1, INPUT);     // declaramos al S1 como entrada digital
  pinMode(S2, INPUT);     // declaramos al S2 como entrada digital
}

void loop()
{
  // Caso 1: Ambos switches apagados
  if (digitalRead(S1) == LOW && digitalRead(S2) == LOW)   
  {
    digitalWrite(led,LOW);   // apago led
  }
  
  // Caso 2: Switch 1 encendido, Switch 2 apagado
  if (digitalRead(S1) == HIGH && digitalRead(S2)==LOW)   
  {
    digitalWrite(led,HIGH);   // enciendo led
  }
  
  // Caso 3: Switch 1 apagado, Switch 2 encendido
  if (digitalRead(S1) == LOW && digitalRead(S2) ==HIGH)   
  {
    digitalWrite(led,HIGH);   // enciendo led
  }
  
  // Caso 4: Ambos switches encendidos
  if (digitalRead(S1) == HIGH && digitalRead(S2) ==HIGH)   
  {
    digitalWrite(led,LOW);   // apago led
  }
}
```

## 4. Explicación Detallada de Componentes

### 4.1 Variables y Pines
- **LED (Pin 13)**: Salida digital que controla el estado del LED
- **Switch 1 (Pin 7)**: Entrada digital para el primer interruptor
- **Switch 2 (Pin 6)**: Entrada digital para el segundo interruptor

### 4.2 Configuración (setup)
- Configuración de pines como entrada o salida
- El LED se configura como salida (OUTPUT)
- Los switches se configuran como entradas (INPUT)

### 4.3 Lógica de Control (loop)
Tabla de estados:
| Switch 1 | Switch 2 | Estado LED |
|----------|----------|------------|
| LOW      | LOW      | Apagado    |
| HIGH     | LOW      | Encendido  |
| LOW      | HIGH     | Encendido  |
| HIGH     | HIGH     | Apagado    |

## 5. Guía de Implementación

1. **Preparación**
   - Conectar el LED al pin 13 y GND
   - Conectar Switch 1 al pin 7 y GND
   - Conectar Switch 2 al pin 6 y GND

2. **Verificación**
   - Comprobar todas las conexiones antes de cargar el código
   - Verificar que los switches estén correctamente conectados
   - Asegurar que el LED esté conectado con la polaridad correcta

## 6. Conclusiones y Recomendaciones

### 6.1 Aprendizaje
- Comprensión de entradas y salidas digitales
- Manejo de condiciones múltiples
- Control de actuadores mediante interruptores

### 6.2 Recomendaciones
- Experimentar con diferentes combinaciones de switches
- Modificar los tiempos de respuesta
- Añadir más LEDs o interruptores para expandir la funcionalidad

### 6.3 Posibles Expansiones
- Agregar un tercer switch
- Implementar diferentes patrones de iluminación
- Incorporar otros componentes como buzzers o displays

## 7. Referencias
- Arduino Official Documentation
- Digital Input/Output Tutorial
- Switch Control Examples