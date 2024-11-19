# Manual Completo: Uso de Pantallas LCD con Arduino UNO R4 WiFi

### Índice
1. [Fundamentos Teóricos](#1-fundamentos-teóricos)
2. [Hardware y Conexiones](#2-hardware-y-conexiones)
3. [Programación del LCD](#3-programación-del-lcd)
4. [Funcionalidades Avanzadas de lcd.print()](#4-funcionalidades-avanzadas-de-lcdprint)
5. [Ejercicios Prácticos](#5-ejercicios-prácticos)
6. [Tips y Mejoras Prácticas](#6-tips-y-mejoras-prácticas)

---

## 1. Fundamentos Teóricos

### 1.1 Introducción a las Pantallas LCD
Las pantallas LCD (Liquid Crystal Display) son componentes fundamentales en la visualización de información en dispositivos electrónicos. Funcionan mediante cristales líquidos intercalados entre dos finas láminas de vidrio que alteran su orientación bajo la influencia de un campo eléctrico, permitiendo el paso de la luz y mostrando caracteres o gráficos.

**Características principales:**
- **Resolución común:** 16x2, con 16 caracteres en 2 líneas.
- **Controlador estándar:** Basado en el IC HD44780.
- **Almacenamiento de caracteres:** Utiliza memoria DDRAM capaz de contener tanto caracteres ASCII como personalizados.
- **Matriz de caracteres:** 5x8 píxeles por carácter.
- **Memoria CGRAM:** Permite crear hasta 8 caracteres personalizados.

### 1.2 Ventajas y Aplicaciones
Las pantallas LCD ofrecen diversas ventajas:
- Bajo consumo de energía
- Alta legibilidad incluso con poca luz
- Interfaz simple y versátil
- Durabilidad y confiabilidad
- Costo accesible
- Amplia disponibilidad de librerías

Aplicaciones comunes:
- Sistemas de monitoreo
- Dispositivos de medición
- Termostatos
- Instrumentos de control
- Proyectos de electrónica

## 2. Hardware y Conexiones

### 2.1 Componentes Necesarios
- Arduino UNO R4 WiFi
- Módulo LCD 16x2
- Potenciómetro de 10kΩ
- Cables de conexión
- Protoboard
- Opcional: Módulo I2C para LCD

### 2.2 Esquemas de Conexión

#### Conexión Directa
```
LCD Pin     Arduino UNO R4 WiFi
--------------------------------
VSS         → GND
VDD         → 5V
V0          → Potenciómetro
RS          → Pin 12
RW          → GND
E           → Pin 11
D4          → Pin 5
D5          → Pin 4
D6          → Pin 3
D7          → Pin 2
A           → 5V (retroiluminación)
K           → GND (retroiluminación)
```

#### Conexión I2C (Recomendada)
```
LCD+I2C Pin Arduino UNO R4 WiFi
--------------------------------
GND         → GND
VCC         → 5V
SDA         → A4
SCL         → A5
```

### 2.3 Consideraciones de Montaje
- Asegurar conexiones firmes y limpias
- Verificar la polaridad correcta
- Ajustar el contraste con el potenciómetro
- Evitar cortocircuitos
- Proteger contra estática

## 3. Programación del LCD

### 3.1 Inicialización Básica

```cpp
// Conexión Directa
#include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
    lcd.begin(16, 2);
    lcd.print("Hola Mundo!");
}

// Conexión I2C
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
    lcd.init();
    lcd.backlight();
    lcd.print("Hola Mundo!");
}
```

### 3.2 Funciones Básicas

```cpp
// Posicionamiento del cursor
lcd.setCursor(columna, fila);    // Posiciona el cursor
lcd.home();                      // Mueve el cursor a (0,0)
lcd.cursor();                    // Muestra el cursor
lcd.noCursor();                  // Oculta el cursor

// Control de pantalla
lcd.clear();                     // Limpia la pantalla
lcd.display();                   // Activa la visualización
lcd.noDisplay();                 // Desactiva la visualización
lcd.blink();                     // Cursor parpadeante
lcd.noBlink();                   // Cursor estático

// Desplazamiento
lcd.scrollDisplayLeft();         // Desplaza el contenido a la izquierda
lcd.scrollDisplayRight();        // Desplaza el contenido a la derecha
```

## 4. Funcionalidades Avanzadas de lcd.print()

### 4.1 Tipos de Datos para lcd.print()

| Tipo de Dato | Ejemplo               | Resultado LCD   |
|--------------|-----------------------|-----------------|
| String       | `lcd.print("Hola");`  | `Hola`          |
| char         | `lcd.print('A');`     | `A`             |
| int          | `lcd.print(42);`      | `42`            |
| long         | `lcd.print(123456L);` | `123456`        |
| float        | `lcd.print(3.14159);` | `3.14`          |
| double       | `lcd.print(3.14159);` | `3.14`          |
| byte         | `lcd.print(255);`     | `255`           |

### 4.2 Formatos Numéricos Especiales

| Formato | Descripción         | Ejemplo                | Resultado |
|---------|---------------------|------------------------|-----------|
| BIN     | Binario             | `lcd.print(42, BIN);`  | `101010`  |
| OCT     | Octal               | `lcd.print(42, OCT);`  | `52`      |
| DEC     | Decimal             | `lcd.print(42, DEC);`  | `42`      |
| HEX     | Hexadecimal         | `lcd.print(42, HEX);`  | `2A`      |

### 4.3 Caracteres Especiales

```cpp
// Definición de carácter personalizado
byte corazon[8] = {
    B00000,
    B01010,
    B11111,
    B11111,
    B01110,
    B00100,
    B00000,
    B00000
};

void setup() {
    lcd.createChar(0, corazon);
    lcd.begin(16, 2);
    lcd.write(byte(0));
}
```

### 4.4 Control de Formato

```cpp
// Control de decimales
float valor = 3.14159;
lcd.print(valor, 2);      // Muestra "3.14"

// Justificación y padding
int numero = 42;
char buffer[16];
sprintf(buffer, "%4d", numero);  // Justifica a la derecha
lcd.print(buffer);
```

## 5. Ejercicios Prácticos

### 5.1 Contador Simple

```cpp
void setup() {
    lcd.begin(16, 2);
    lcd.print("Contador:");
}

void loop() {
    static int contador = 0;
    lcd.setCursor(0, 1);
    lcd.print(contador++);
    delay(1000);
}
```

### 5.2 Monitor de Ambiente

```cpp
void loop() {
    float temperatura = leerTemperatura();
    int humedad = leerHumedad();
    
    // Primera línea: Temperatura
    lcd.setCursor(0, 0);
    lcd.print("T: ");
    lcd.print(temperatura, 1);
    lcd.print(" C");

    // Segunda línea: Humedad
    lcd.setCursor(0, 1);
    lcd.print("H: ");
    lcd.print(humedad);
    lcd.print(" %");

    delay(2000);
}
```

### 5.3 Mensaje Deslizante

```cpp
void scrollText(const char* mensaje) {
    lcd.clear();
    lcd.print(mensaje);
    for(int i = 0; i < strlen(mensaje); i++) {
        lcd.scrollDisplayLeft();
        delay(300);
    }
}
```

## 6. Tips y Mejoras Prácticas

### 6.1 Optimización de Memoria

```cpp
// Evitar String
// Malo
String mensaje = "Temperatura: " + String(temperatura) + "C";
lcd.print(mensaje);

// Bueno
lcd.print("Temp:");
lcd.print(temperatura);
lcd.print("C");
```

### 6.2 Actualización Eficiente

```cpp
void actualizarValor(float nuevoValor, float &valorAnterior, byte posX, byte posY) {
    if (nuevoValor != valorAnterior) {
        lcd.setCursor(posX, posY);
        lcd.print("    ");  // Borra valor anterior
        lcd.setCursor(posX, posY);
        lcd.print(nuevoValor, 1);
        valorAnterior = nuevoValor;
    }
}
```

### 6.3 Mejores Prácticas
- Limitar actualizaciones innecesarias
- Usar constantes para valores fijos
- Implementar rutinas de limpieza
- Manejar errores adecuadamente
- Documentar el código
- Mantener consistencia en el formato
- Optimizar el consumo de energía

### 6.4 Depuración

```cpp
// Función de utilidad para debug
void debugLCD(const char* mensaje, int valor) {
    Serial.print(mensaje);
    Serial.println(valor);
    lcd.clear();
    lcd.print(mensaje);
    lcd.setCursor(0, 1);
    lcd.print(valor);
    delay(1000);
}
```

---

Este manual proporciona una base sólida para trabajar con pantallas LCD en proyectos con Arduino UNO R4 WiFi. Los conceptos y ejemplos presentados pueden adaptarse y expandirse según las necesidades específicas de cada proyecto.