# Manual de Estudio: Control de Display 7 Segmentos con Arduino UNO R4

## 1. Introducción
Este manual está diseñado para estudiantes que desean aprender a controlar un display de 7 segmentos directamente desde el Arduino UNO R4, sin utilizar un decodificador externo.

## 2. Objetivos de Aprendizaje
- Comprender el funcionamiento de un display de 7 segmentos
- Aprender a controlar directamente los segmentos del display
- Implementar una secuencia de números y letras
- Desarrollar habilidades de programación con Arduino

## 3. Materiales Necesarios
- Arduino UNO R4
- Display de 7 segmentos (ánodo común o cátodo común)
- Resistencias de 220Ω (7 unidades)
- Cables de conexión
- Protoboard

## 4. Fundamentos Teóricos

### 4.1 Display de 7 Segmentos
El display de 7 segmentos consta de 7 LEDs (segmentos) etiquetados de 'a' hasta 'g', más un punto decimal (dp). Cada segmento puede ser controlado individualmente para formar números y letras.

```
    a
   ---
f |   | b
  | g |
   ---
e |   | c
  |   |
   ---
    d    • dp
```

### 4.2 Configuración de Pines
En nuestro proyecto utilizaremos los siguientes pines del Arduino UNO R4:
- Segmento a -> Pin 2
- Segmento b -> Pin 3
- Segmento c -> Pin 4
- Segmento d -> Pin 5
- Segmento e -> Pin 6
- Segmento f -> Pin 7
- Segmento g -> Pin 8
- Punto decimal -> Pin 9

## 5. Tabla de Códigos

Para display de ánodo común:

| Caracter | Código Binario | Hexadecimal | Decimal |
|----------|---------------|-------------|---------|
| 0 | 1000000 | 40h | 64 |
| 1 | 1111001 | 79h | 121 |
| 2 | 0100100 | 24h | 36 |
| 3 | 0110000 | 30h | 48 |
| 4 | 0011001 | 19h | 25 |
| 5 | 0010010 | 12h | 18 |
| 6 | 0000010 | 02h | 2 |
| 7 | 1111000 | 78h | 120 |
| 8 | 0000000 | 00h | 0 |
| 9 | 0011000 | 18h | 24 |
| H | 0001001 | 09h | 9 |
| O | 1000000 | 40h | 64 |
| L | 1000111 | 47h | 71 |
| A | 0001000 | 08h | 8 |

Nota: Para display de cátodo común, usar los valores complementarios (invertidos).

## 6. Código de Ejemplo

```cpp
// Definición de pines
const int segmentos[] = {2, 3, 4, 5, 6, 7, 8, 9}; // a-g, dp

// Tabla de códigos para ánodo común
const byte TABLA_CARACTERES[] = {
  0x40, 0x79, 0x24, 0x30, 0x19, // 0-4
  0x12, 0x02, 0x78, 0x00, 0x18, // 5-9
  0xFF, // apagado
  0x09, // H
  0x40, // O
  0x47, // L
  0x08  // A
};

void setup() {
  // Configurar pines como salidas
  for (int i = 0; i < 8; i++) {
    pinMode(segmentos[i], OUTPUT);
  }
}

void loop() {
  // Mostrar secuencia de números y letras
  for (int i = 0; i < 15; i++) {
    mostrarCaracter(TABLA_CARACTERES[i]);
    delay(1000); // Esperar 1 segundo
  }
}

void mostrarCaracter(byte codigo) {
  // Mostrar el patrón de segmentos
  for (int i = 0; i < 8; i++) {
    digitalWrite(segmentos[i], bitRead(codigo, i));
  }
}
```

## 7. Consideraciones Importantes

### 7.1 Conexiones
1. **Resistencias**: Es fundamental usar resistencias limitadoras de corriente (220Ω) para cada segmento del display para proteger los LEDs.
2. **Tipo de Display**: 
   - Para ánodo común: conectar el pin común a 5V
   - Para cátodo común: conectar el pin común a GND
3. **Verificación**: Comprobar todas las conexiones antes de energizar el circuito.

### 7.2 Programación
1. **Configuración de Pines**: Asegurarse de que todos los pines estén correctamente configurados como salidas.
2. **Tabla de Códigos**: Verificar que se está usando la tabla correcta según el tipo de display.
3. **Tiempos**: Los delays pueden ajustarse según la necesidad de visualización.

### 7.3 Solución de Problemas Comunes

1. Si el display no muestra nada:
   - Verificar la polaridad del display
   - Comprobar las conexiones de las resistencias
   - Verificar la configuración de los pines

2. Si los segmentos muestran patrones incorrectos:
   - Revisar el orden de conexión de los pines
   - Verificar que se está usando la tabla correcta (ánodo/cátodo común)
   - Comprobar que los valores en la tabla de códigos son correctos

## 8. Referencias y Recursos Adicionales

- Documentación oficial de Arduino
- Hojas de datos de displays de 7 segmentos
- Comunidad Arduino para soporte adicional