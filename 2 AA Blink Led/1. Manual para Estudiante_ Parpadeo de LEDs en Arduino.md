

# Manual para Estudiante: Parpadeo de LEDs en Arduino

## 1. Introducción
Este manual tiene como objetivo guiar a los estudiantes en la creación de un programa simple para Arduino que hace parpadear dos LEDs. Este ejercicio es fundamental para comprender los conceptos básicos de programación en Arduino y la manipulación de hardware, así como para desarrollar habilidades en la electrónica.

## 2. Código
```cpp
// PUCE Ibarra, Arquitectura de Computadores
// Profesor: Mgs. Stalin Arciniegas

/*
Programa: Parpadeo de leds
Dispositivo: Arduino uno
Notas: Parpadeo de dos leds cada uno con 0.5 segundos de retraso
*/

int led = 13;        // pin 13 asignamos nombre "Led"
int led1 = 12;       // pin 12 asignamos nombre "Led1"

void setup()
{
  pinMode(led, OUTPUT);   // declaramos al Led como salida digital
  pinMode(led1, OUTPUT);  // declaramos al Led1 como salida digital
}

void loop()
{
  digitalWrite(led, HIGH);   // Prende led
  delay(500);                // Espera 500 milisegundos
  digitalWrite(led, LOW);    // Apaga led
  delay(500);                // Espera 500 milisegundos

  digitalWrite(led1, HIGH);  // Prende led1
  delay(500);                // Espera 500 milisegundos
  digitalWrite(led1, LOW);   // Apaga led1
  delay(500);                // Espera 500 milisegundos
}
```

## 3. Explicación teórica de cada comando
- **`int led = 13;`**: Declara una variable `led` y la asigna al pin 13 del Arduino.
- **`int led1 = 12;`**: Declara una variable `led1` y la asigna al pin 12 del Arduino.
- **`void setup() { ... }`**: Función que se ejecuta una vez al inicio para configurar los pines.
  - **`pinMode(led, OUTPUT);`**: Configura el pin 13 como salida digital.
  - **`pinMode(led1, OUTPUT);`**: Configura el pin 12 como salida digital.
- **`void loop() { ... }`**: Función que se ejecuta continuamente después de la configuración inicial.
  - **`digitalWrite(led, HIGH);`**: Envía una señal alta al pin 13 para encender el LED.
  - **`delay(500);`**: Pausa el programa por 500 milisegundos (0.5 segundos).
  - **`digitalWrite(led, LOW);`**: Envía una señal baja al pin 13 para apagar el LED.
  - Se repiten pasos similares para `led1`, encendiéndolo y apagándolo con un retraso de 500 milisegundos.

## 5. Conclusiones y recomendaciones
Este ejercicio básico de parpadeo de LEDs es una excelente manera de familiarizarse con la programación de Arduino y la manipulación de hardware. Se recomienda experimentar con diferentes tiempos de retardo y agregar más LEDs para explorar más posibilidades. Además, es útil revisar la documentación de Arduino para profundizar en otros comandos y funciones disponibles.

