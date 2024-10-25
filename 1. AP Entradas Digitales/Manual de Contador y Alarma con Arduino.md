# Manual para Estudiante: Contador y Alarma con Arduino

## 1. Introducción
Este manual guía a los estudiantes en la creación de un programa para Arduino que implementa un contador con visualización en LEDs y una alarma. El sistema utiliza pulsadores para controlar el contador y activar una sirena bajo ciertas condiciones.

## 2. Componentes del Circuito
- 8 LEDs conectados a los pines definidos en `outArray[]`
- Pulsador contador conectado al pin `Pulso`
- Pulsador de reinicio conectado al pin `reinicio`
- Sirena conectada al pin `sirena`

## 3. Código Comentado
```cpp
int outArray[] = {4, 5, 6, 7, 8, 9, 10, 11}; //define pines en vector de 8 bits
int Pulso = 2;
int reinicio = 3;
int sirena =13;
byte b;
int count=0;
int contador=0;

void setup()
{
  for (count=0;count<8;count++) {           //ciclo for, para configurar pines
    pinMode(outArray[count], OUTPUT);       //de vector como salida
  }
  pinMode (Pulso, INPUT);                   //configuro pulsador contador
  pinMode (reinicio, INPUT);                //configuro pulsador de reinicio
  pinMode (sirena,OUTPUT);                  //configuro sirena como salida
}

void loop() {
  if (!digitalRead(Pulso)==1){              //leer entrada de pulsador contador
    do{
    }while(!digitalRead(Pulso)==1);         //elimina rebotes
    delay(10);
    contador++;                             //incrementa contador
    if (contador == 39){                    //verifica si es igual a 39
      for (count=0;count<5;count++){        //activa alarma por 5 ocasiones
        digitalWrite(sirena,HIGH);
        delay(500);                         //con retardo de 500 milisegundos
        digitalWrite(sirena,LOW);
        delay(500);
      }
      contador=0;                           //si es correcto encera
    }
  }
  
  if (!digitalRead(reinicio)==1){           //lee entrada de reinicio
    do{
    }while(!digitalRead(reinicio)==1);      //elimina rebotes
    delay(10);
    contador=0;                             //encera
  }
  b=byte(contador);                         //convierte byte
  digitalWrite(outArray[0],bitRead(b,0));   //visualiza segun posición de vector
  digitalWrite(outArray[1],bitRead(b,1));
  digitalWrite(outArray[2],bitRead(b,2));
  digitalWrite(outArray[3],bitRead(b,3));
  digitalWrite(outArray[4],bitRead(b,4));
  digitalWrite(outArray[5],bitRead(b,5));
  digitalWrite(outArray[6],bitRead(b,6));
  digitalWrite(outArray[7],bitRead(b,7));
}
```

## 4. Explicación Detallada de Componentes

### 4.1 Variables y Pines
- `outArray[]`: Array de 8 pines para los LEDs de visualización
- `Pulso`: Pin 2, entrada para el pulsador contador
- `reinicio`: Pin 3, entrada para el pulsador de reinicio
- `sirena`: Pin 13, salida para la sirena
- `contador`: Variable que almacena el valor del contador

### 4.2 Configuración (setup)
- Configura los pines de los LEDs como salidas
- Configura los pulsadores como entradas
- Configura la sirena como salida

### 4.3 Lógica de Control (loop)
1. **Incremento del contador**:
   - Detecta pulsación del botón contador
   - Incrementa `contador`
   - Si `contador` llega a 39, activa la alarma 5 veces y reinicia el contador

2. **Reinicio del contador**:
   - Detecta pulsación del botón de reinicio
   - Pone `contador` a 0

3. **Visualización en LEDs**:
   - Convierte `contador` a byte
   - Muestra el valor en binario usando los 8 LEDs

## 5. Guía de Implementación

1. **Preparación**
   - Conectar 8 LEDs a los pines 4-11
   - Conectar pulsador contador al pin 2
   - Conectar pulsador de reinicio al pin 3
   - Conectar sirena al pin 13

2. **Verificación**
   - Comprobar todas las conexiones antes de cargar el código
   - Verificar que los pulsadores estén correctamente conectados
   - Asegurar que los LEDs estén conectados con la polaridad correcta

## 6. Conclusiones y Recomendaciones

### 6.1 Aprendizaje
- Manejo de entradas y salidas digitales múltiples
- Implementación de un contador binario
- Control de alarma basado en condiciones

### 6.2 Recomendaciones
- Experimentar con diferentes valores límite para la alarma
- Modificar la secuencia de la alarma
- Añadir funcionalidades adicionales, como un display de 7 segmentos

### 6.3 Posibles Expansiones
- Implementar un modo de configuración para el límite de la alarma
- Añadir una pantalla LCD para mostrar el valor del contador
- Incorporar comunicación serial para monitoreo en tiempo real

## 7. Referencias
- Arduino Official Documentation
- Digital Input/Output Tutorial
- Binary Counting Examples